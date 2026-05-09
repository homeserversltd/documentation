# Troubleshooting

This section collects recurring issues and their resolutions. For NIC/network problems on specific hardware, see the footnote below.

---

## `503 Service Temporarily Unavailable` on `https://home.arpa` {#home-arpa-503}

**Issue:**  
Nginx shows `503 Service Temporarily Unavailable` for `https://home.arpa`.

**Quick fix:**  
Rebuild the frontend artifacts on the server:

```bash
cd /var/www/homeserver
sudo npm run build
```

If you do **not** see a `src/` directory (or source files) in `/var/www/homeserver`, this likely means only the build output is present. In that case, you will need to clone the full website repository with the source code before running `npm run build`:

```bash
cd /var/www
sudo git clone <website-repo-url> homeserver
cd homeserver
sudo npm install
sudo npm run build
```
Replace `<website-repo-url>` with the actual repository URL.

Then refresh `https://home.arpa`.

**Note:**  
One known failure mode is missing or stale frontend build output under `/var/www/homeserver/build`, which causes the app to fail serving `index.html`. If the source files (`src/`) are missing, attempting to rebuild will not work—ensure you have the source present either by restoring it or doing a fresh `git clone` of the website repository.

---

## NIC link down (BIOS power management) {#nic-link-down-bios}

**Issue:**  
WAN or LAN interfaces stay down, or the device only gets network when Ethernet cables were **plugged in before boot**. DHCP (Kea) may not bind; the device can appear unreachable.

**Cause:**  
On some hardware (notably certain MiniForum and similar units), BIOS power-management features put the NIC into low-power states that only wake on physical link detection. No amount of software configuration overrides this.

**Fix (BIOS):**

1. Enter BIOS at boot (typically Del or F2).
2. **Disable ASPM:** Advanced → Onboard Devices → PCH-PCIE (or similar). Set all ASPM options to **Disabled**.
3. **Disable Energy Efficient Ethernet (EEE):** Find and disable EEE in advanced/onboard options.
4. **Disable Deep S5:** Disable Deep S5 (and any "deep sleep" NIC option) so the NIC does not enter ultra-low-power state.
5. Save and exit; reboot. Connect cables and verify WAN/LAN and DHCP.

**Footnote:** If things are broken, ensure cables are plugged in before booting. For full technical detail, see the cold-storage reference: *MiniForum NIC / BIOS power management*.

---

## Troubleshooting Log: Disk Full Disaster (Module 1)

**Issue:**  
Woke up to find the home server malfunctioning—DHCP (kea) was not handing out IP addresses, and Jellyfin media server was completely broken.

### Symptoms
- No devices could obtain an IP address from the DHCP server.
- Jellyfin media server became unresponsive; user data and history seemingly lost.

### Diagnosis
- Connected a monitor and logged in as root directly to check system state.
- Discovered the root disk was 100% full. This caused:
  - Kea DHCP service to stop issuing IP addresses (due to inability to write lease files).
  - Jellyfin services to fail, as they could not write any cache, logs, or data.

### Resolution Steps

#### For Kea DHCP
1. **Stop the DHCP service:**
   ```
   systemctl stop kea-dhcp4.service
   ```
2. **Remove corrupted or unwriteable lease files:**
   ```
   rm /var/lib/kea/kea-leases.csv
   rm /var/lib/kea/kea-leases.csv.2
   ```
3. **Clear enough disk space** to restore normal operation. Identify and remove the main files or directories filling your partition.
4. **Reboot the server:**
   ```
   reboot
   ```
5. **Verify that devices are receiving IP addresses again.**

#### For Jellyfin
1. **Stop Jellyfin service:**
   ```
   sudo systemctl stop jellyfin.service
   ```
2. **Delete all Jellyfin data (if necessary)** _Warning: this wipes user accounts, settings, and server history. Use only as a last resort, or back up first if possible:_
   ```
   rm -rf /var/lib/jellyfin/* /var/cache/jellyfin/* /etc/jellyfin/* /var/log/jellyfin/*
   ```
3. **Restart Jellyfin:**
   ```
   sudo systemctl restart jellyfin.service
   ```

**Note:** If data was lost due to disk full and deletion, a Jellyfin reinstallation/setup will be required.

---

**Summary/Lesson:**  
Drive space is mission critical for all server operations. A full disk will silently break fundamental services like DHCP and Jellyfin, sometimes catastrophically. Monitoring disk usage and setting up alerts is highly recommended.

---

*This is the first entry of an ongoing troubleshooting log, documenting “bad days” and their recoveries on Home Server infrastructure.*