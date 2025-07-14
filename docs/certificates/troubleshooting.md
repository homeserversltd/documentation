# CA Certificate Installation & Troubleshooting

!!! info "Certificate Renewal"
    Remember that SSL/TLS certificates expire every 2 years maximum. See the [Certificate Renewal Guide](renewal.md) for renewal procedures and scheduling.

This guide helps you install the HomeServer root CA certificate on various operating systems and troubleshoot common issues.

---

## Quick Reference Table

| OS/Distro         | Commands                                                                                 |
|-------------------|----------------------------------------------------------------------------------------|
| Debian/Ubuntu     | `sudo cp ... /usr/local/share/ca-certificates/`<br>`sudo update-ca-certificates`         |
| Fedora/RHEL/CentOS| `sudo cp ... /etc/pki/ca-trust/source/anchors/`<br>`sudo update-ca-trust extract`        |
| Arch/Manjaro      | `sudo trust anchor ~/Downloads/root.crt`                                                |
| openSUSE          | `sudo cp ... /etc/pki/trust/anchors/`<br>`sudo update-ca-certificates`                   |
| Gentoo/Alpine     | `sudo cp ... /usr/local/share/ca-certificates/`<br>`sudo update-ca-certificates`         |
| FreeBSD           | `sudo cp ... /usr/local/share/certs/`<br>`sudo certctl rehash`                           |
| OpenBSD           | `sudo cp ... /etc/ssl/certs/`<br>`sudo c_rehash /etc/ssl/certs/`                         |
| NixOS             | Edit config, add to `security.pki.certificateFiles`, then `sudo nixos-rebuild switch`    |

---

## Distribution-Specific Instructions

### Debian / Ubuntu
1. Download `root.crt` and save it.
2. Install `ca-certificates` if needed:
   ```sh
   sudo apt update && sudo apt install ca-certificates
   ```
3. Copy and update:
   ```sh
   sudo mkdir -p /usr/local/share/ca-certificates
   sudo cp ~/Downloads/root.crt /usr/local/share/ca-certificates/homeserver.crt
   sudo update-ca-certificates
   ```
4. Restart your browser.

### Fedora / RHEL / CentOS
1. Download `root.crt` and save it.
2. Install `ca-certificates` if needed:
   ```sh
   sudo dnf install ca-certificates
   ```
3. Copy and update:
   ```sh
   sudo mkdir -p /etc/pki/ca-trust/source/anchors
   sudo cp ~/Downloads/root.crt /etc/pki/ca-trust/source/anchors/homeserver.crt
   sudo update-ca-trust extract
   ```
4. Restart your browser.

### Arch Linux / Manjaro
1. Download `root.crt` and save it.
2. Install `ca-certificates-utils` if needed:
   ```sh
   sudo pacman -S ca-certificates-utils
   ```
3. Add the certificate:
   ```sh
   sudo trust anchor ~/Downloads/root.crt
   ```
4. Restart your browser.
   
**Troubleshooting:**
- If you see `p11-kit: unrecognized file format`, ensure the file is in PEM format (starts with `-----BEGIN CERTIFICATE-----`).
- To convert DER to PEM:
  ```sh
  openssl x509 -inform der -in ~/Downloads/root.crt -out ~/Downloads/root.pem
  sudo trust anchor ~/Downloads/root.pem
  ```
- To re-encode a PEM file:
  ```sh
  openssl x509 -in ~/Downloads/root.crt -out ~/Downloads/root-fixed.crt
  sudo trust anchor ~/Downloads/root-fixed.crt
  ```

### openSUSE
1. Download `root.crt` and save it.
2. Copy and update:
   ```sh
   sudo cp ~/Downloads/root.crt /etc/pki/trust/anchors/homeserver.crt
   sudo update-ca-certificates
   ```
3. Restart your browser.

### Gentoo / Alpine
1. Download `root.crt` and save it.
2. Copy and update:
   ```sh
   sudo cp ~/Downloads/root.crt /usr/local/share/ca-certificates/homeserver.crt
   sudo update-ca-certificates
   ```
3. Restart your browser.

### FreeBSD
1. Download `root.crt` and save it.
2. Copy and rehash:
   ```sh
   sudo cp ~/Downloads/root.crt /usr/local/share/certs/homeserver.crt
   sudo certctl rehash
   ```
3. Restart your browser.

### OpenBSD
1. Download `root.crt` and save it.
2. Copy and rehash:
   ```sh
   sudo cp ~/Downloads/root.crt /etc/ssl/certs/
   sudo c_rehash /etc/ssl/certs/
   ```
3. Restart your browser.

### NixOS
1. Download `root.crt` and save it.
2. Edit `/etc/nixos/configuration.nix`:
   ```nix
   security.pki.certificateFiles = [ "/home/anon/Downloads/root.crt" ];
   ```
3. Rebuild:
   ```sh
   sudo nixos-rebuild switch
   ```
4. Restart your browser.

---

## Browser-Specific Notes
- **Firefox:** May require manual import: Preferences → Privacy & Security → Certificates → View Certificates.
- **Snap/Flatpak/AppImage browsers:** May not use system CA store. Import manually in the app.
- **WSL:** Install the CA in Windows, not WSL, for browser trust.

## Chrome/Chromium Browser-Specific Troubleshooting

If you have installed the CA certificate correctly but Chrome or Chromium still shows certificate warnings (e.g., `NET::ERR_CERT_AUTHORITY_INVALID`), try the following steps:

1. **Disable Secure DNS**
   - Go to `chrome://settings/security` in your browser.
   - Scroll down to the "Advanced" section.
   - Ensure that "Use secure DNS" is **off** (disabled). Secure DNS can sometimes interfere with local certificates and cause trust issues for internal domains.

2. **Reset Certificate/SSL Flags**
   - Go to `chrome://flags` in your browser.
   - Use the search bar to look for "Certificate" or "SSL".
   - If you have changed any related flags, reset them to their default values.
   - Relaunch the browser after making changes.

3. **Restart Chrome Completely**
   - Fully quit all Chrome/Chromium processes and reopen the browser to ensure changes take effect.

If you continue to see certificate warnings after these steps, review the rest of this guide or see the Common Errors & Troubleshooting section below.

---

## Common Errors & Troubleshooting

### "unrecognized file format"
- Ensure the certificate is in PEM format (starts with `-----BEGIN CERTIFICATE-----`).
- Convert DER to PEM:
  ```sh
  openssl x509 -inform der -in ~/Downloads/root.crt -out ~/Downloads/root.pem
  ```

### "update-ca-certificates: command not found"
- Install the appropriate package for your distro (see above).

### "trust anchor: command not found"
- Install `ca-certificates-utils` (Arch/Manjaro).

---

For further help, see your distribution's documentation or contact your system administrator.
