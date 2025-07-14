# Initial Network Access

## Local Network Discovery

### Primary Access Method
- **From any device on your local network**, navigate to `server.home.arpa` in your web browser
- This will connect you to your new HomeServer's splash page
- *Note: Any subdomain under `.home.arpa` is a reserved domain specifically for home servers*

### What You'll See
- **HomeServer welcome page** with service overview
- **Admin access button** in the top right corner
- **Service status indicators** showing system health

## Alternative Access Methods

### Direct IP Access
- **Check your router's DHCP client list** for the HomeServer's IP address
- **Look for device name** "HomeServer" or similar in connected devices
- **Navigate directly** to the IP address in your browser

### Network Scanning
- **Use network discovery tools** like Fing or Advanced IP Scanner
- **Scan your local subnet** (typically 192.168.1.x or 192.168.0.x)
- **Look for open ports** 80 (HTTP) and 443 (HTTPS)

### Router Administration
- **Access your router's admin panel** (usually 192.168.1.1 or 192.168.0.1)
- **Check connected devices** or DHCP client list
- **Identify the HomeServer** by MAC address or hostname

## Troubleshooting Network Access

### Device Not Found
- **Ensure both devices are on the same network segment**
- **Check for guest network isolation** - HomeServer must be on main network
- **Verify DHCP is working** - device needs an IP address

### Browser Issues
- **Try different browsers** (Chrome, Firefox, Safari)
- **Clear browser cache** and cookies
- **Disable browser extensions** that might block local connections

### Network Configuration
- **Check firewall settings** on your computer
- **Verify network adapter settings** are set to automatic
- **Test with mobile device** on same WiFi network

## Security Considerations

### First Access
- **Use HTTPS when available** for encrypted connections
- **Verify certificate warnings** are expected for self-signed certificates
- **Note the admin access requirements** for initial setup

### Network Safety
- **HomeServer operates on local network only** until configured otherwise
- **No external access** is enabled by default
- **Admin authentication required** for configuration changes

## Next Steps

Once you can access your HomeServer's web interface, proceed to [Administrative Access & Authentication](setup-admin.md) to begin secure configuration. 