# Transmission with PIA VPN Integration

## Quick Access

### Local Network Access
- **Web Interface**: [https://transmission.home.arpa](https://transmission.home.arpa)
- **Direct IP Access**: [https://transmission.home.arpa](https://transmission.home.arpa)

### Remote Access
- **Remote URL**: Not available for security reasons (VPN-protected service)
- **Note**: Transmission runs in a VPN namespace and is only accessible locally

---

## Overview

**Transmission** is a powerful BitTorrent client integrated with your HomeServer, featuring automatic Private Internet Access (PIA) VPN protection. This ensures all your downloads are secure, private, and properly routed through an encrypted VPN connection. The service is fully managed through your HomeServer interface, providing one-click control over both Transmission and its VPN connection.

---

## 1. Key Features

- **Automatic VPN Protection:**
  - All Transmission traffic is automatically routed through PIA VPN
  - Network namespace isolation for enhanced security
  - Dynamic port forwarding for optimal connectivity
  - Automatic port configuration and firewall management
- **Web Interface:**
  - Access Transmission through your HomeServer dashboard
  - Monitor download status and manage torrents
  - View real-time VPN connection status
  - Control both Transmission and VPN with one click
- **Security Features:**
  - Network isolation prevents VPN leaks
  - Encrypted credentials management
  - Automatic firewall rule management
  - Fail-safe disconnection if VPN drops

---

## 2. Using Transmission

### Web Interface Access
- **Local Network:**
  - Access via `https://transmission.home.arpa`
  - Or through your HomeServer dashboard
- **Remote Access:**
  - Use your Tailscale URL: `https://server.{YourTailnet}.ts.net/transmission/`
  - See [Tailscale Guide](tailscale.md) for remote access details

### Managing Downloads
- Add torrents through the web interface
- Monitor download progress
- Manage bandwidth allocation
- Set download priorities
- View detailed statistics

---

## 3. VPN Integration

### Status Monitoring
- **VPN Status Indicator:**
  - 🟢 Green: VPN and Transmission running
  - 🟡 Yellow: Partial service (VPN or Transmission)
  - 🔴 Red: Services stopped
  - ⚪ White: Loading/checking status

### One-Click Management
- **Enable/Disable:**
  - Single click to start/stop both services
  - Automatic VPN connection before Transmission starts
  - Proper shutdown sequence when stopping
- **Port Management:**
  - Automatic port forwarding setup
  - Dynamic port assignment from PIA
  - Firewall rules automatically updated

### Credentials Management
- **PIA VPN:**
  - Securely store and manage PIA credentials
  - Update credentials through web interface
  - Encrypted storage and transmission
- **Transmission Access:**
  - Separate credentials for Transmission web UI
  - Update authentication details easily
  - Secure credential storage

---

## 4. Advanced Features

### Network Configuration
- **Namespace Isolation:**
  - Dedicated network namespace for VPN traffic
  - Prevents IP leaks outside VPN tunnel
  - Automatic routing configuration
- **Firewall Management:**
  - Dynamic rule updates based on VPN status
  - LAN access to web interface
  - Protected external connectivity

### Service Management
- **Automatic Recovery:**
  - Service monitoring and auto-restart
  - VPN connection maintenance
  - Port forwarding renewal
- **Logging & Debugging:**
  - Detailed status logging
  - Performance monitoring
  - Troubleshooting tools

---

## 5. Configuration

### VPN Settings
- **Connection Type:**
  - OpenVPN UDP (standard protocol)
  - Automatic server selection
  - Port forwarding enabled
- **Network Settings:**
  - IPv6 disabled for security
  - DNS leak protection
  - Kill switch enabled

### Transmission Settings
- **Default Configuration:**
  - Web interface on port 9091
  - Automatic port forwarding
  - LAN access enabled
- **Customization:**
  - Bandwidth limits
  - Queue management
  - Peer settings

---

## 6. Troubleshooting

### Common Issues
- **VPN Won't Connect:**
  - Check PIA credentials
  - Verify network connectivity
  - Review system logs
- **Transmission Inaccessible:**
  - Confirm VPN status
  - Check service status
  - Verify credentials

### Status Checking
- **View Service Status:**
  - Check dashboard indicators
  - Review system logs
  - Monitor network status
- **Connection Testing:**
  - Verify VPN connectivity
  - Test port forwarding
  - Check web interface access

---

## 7. Security Best Practices

- **Always use VPN:**
  - Never disable VPN protection
  - Keep credentials updated
  - Monitor connection status
- **Regular Updates:**
  - Keep system updated
  - Check for security advisories
  - Update credentials periodically
- **Access Control:**
  - Use strong passwords
  - Limit admin access
  - Monitor access logs

---

## 8. Technical Details

### Network Architecture
- Isolated network namespace
- Virtual ethernet interfaces
- Automatic routing configuration
- Dynamic port forwarding

### Security Features
- Encrypted credential storage
- Network isolation
- Automatic firewall management
- Fail-safe disconnection

### Integration Points
- HomeServer dashboard
- Status monitoring
- Credential management
- Service control

---

## 9. Credits & Attribution

**Transmission** is an open-source project created and maintained by the Transmission community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

- **Original Project**: [Transmission on GitHub](https://github.com/transmission/transmission)
- **Maintainer**: [transmission](https://github.com/transmission)
- **License**: GPL v2
- **Documentation**: [Transmission Documentation](https://transmissionbt.com/help/)

This HomeServer integration builds upon the excellent foundation provided by the Transmission project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Note:** This service is designed for security and privacy. Always ensure the VPN status indicator shows green before using Transmission. 