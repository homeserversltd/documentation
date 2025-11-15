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