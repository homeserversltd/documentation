# Tailscale VPN Service Guide

## Official Resources & Support

!!! info "Service-Specific Issues"
    **Experiencing issues with Tailscale functionality?** Please create an issue ticket with the original developers so they can fix it for everyone. HomeServer LLC provides the integration and hosting platform only.

### Official Links
- **Original Project**: [Tailscale on GitHub](https://github.com/tailscale/tailscale)
- **Company**: [Tailscale Inc.](https://tailscale.com/)
- **License**: Various (see [Tailscale License](https://github.com/tailscale/tailscale/blob/main/LICENSE))
- **Official Documentation**: [Tailscale Documentation](https://tailscale.com/kb/)

## Quick Access

### Service Management
- **Admin Interface**: Access through HomeServer Admin panel
- **Status Monitoring**: Available in HomeServer Stats tab
- **Configuration**: Managed via HomeServer Admin settings

### Remote Network Access
- **Your Tailscale Network**: Provides secure access to all HomeServer services
- **Remote HomeServer URL**: [https://home.{YourTailnetNameHere}.ts.net](https://home.{YourTailnetNameHere}.ts.net)
- **Note**: Tailscale is the service that enables remote access to all other services

---

## Overview

**Tailscale** provides secure, private VPN connectivity for your HomeServer, enabling you to access your server and services from anywhere in the world. With Tailscale, you get seamless remote access, strong encryption, and easy device management—all fully integrated into your HomeServer experience.

---

## 1. What Can You Do With Tailscale?

- **Remote Access:**
  - Connect to your HomeServer and all its services securely from anywhere, as if you were on your home network.
- **Private Networking:**
  - All traffic is encrypted and routed through your private Tailscale network (Tailnet).
- **Zero Configuration:**
  - No port forwarding or firewall changes required—just log in and connect.
- **Multi-Device Support:**
  - Access your HomeServer from your phone, laptop, or any device with Tailscale installed.
- **MagicDNS:**
  - Use easy-to-remember names (like `home-server.tailnet-name.ts.net`) instead of IP addresses.

---

## 2. Accessing Your HomeServer Remotely

- **Connect to Tailscale:**
  1. Install the Tailscale app on your device ([Download here](https://tailscale.com/download)).
  2. Log in with your account and join your Tailnet.
  3. Once connected, you can access your HomeServer services using their Tailscale URLs, for example:
     - `https://home.{YourTailnetNameHere}.ts.net/jellyfin/`
     - `https://home.{YourTailnetNameHere}.ts.net/vault/`
     - `https://home.{YourTailnetNameHere}.ts.net/music/`
- **No VPN Client Needed for Local Access:**
  - On your home network, continue using the standard URLs (e.g., `https://jellyfin.home.arpa`).

---

## 3. Using Tailscale

- **Start/Stop the Service (Admin Only):**
  - Start: `sudo systemctl start tailscaled`
  - Stop: `sudo systemctl stop tailscaled`
  - Status: `sudo systemctl status tailscaled`
- **Connect to Your Tailnet:**
  - Run `sudo tailscale up` on the server and follow the authentication link.
- **Check Status:**
  - `tailscale status` (shows connected devices)
  - `ip link show tailscale0` (shows the VPN interface)
- **Web Integration:**
  - All HomeServer services are accessible via Tailscale URLs for secure remote access.

---

## 4. Integration with HomeServer

- **Portal Integration:**
  - Tailscale is preconfigured and managed by your HomeServer. No manual setup required for most users.
- **Unified Access:**
  - All service portals (Jellyfin, Vaultwarden, Navidrome, etc.) are available via Tailscale URLs when remote.
- **homeserver.json:**
  - Tailscale configuration and service URLs are managed centrally, ensuring seamless integration. (See [Platform Configuration](homeserver.json.md))

---

## 5. One-Click VPN Management (Powered by HomeServer)

Your HomeServer interface provides direct, advanced control over Tailscale VPN:

- **Connect/Disconnect:** Start or stop your VPN connection with a single click. If authentication is required, you'll be prompted with a secure link—no need to run commands manually.
- **Service Control:** Enable or disable Tailscale auto-start from the web UI.
- **Live Status:** Instantly see whether your server is connected, and to which tailnet, right from your dashboard.
- **Tailnet Name Management:** View or update your tailnet name directly from the HomeServer interface.
- **No Terminal Needed:** All common VPN actions are available from the dashboard—no command line required.

These features are powered by HomeServer's advanced backend integration with Tailscale, ensuring a seamless and secure experience for all users.

---

## 6. Security & Best Practices

- **Strong Encryption:**
  - All connections are end-to-end encrypted by Tailscale.
- **Access Control:**
  - Only devices you authorize can join your Tailnet and access your HomeServer.
- **No Open Ports:**
  - Your HomeServer remains protected behind your firewall—no need to expose services to the public internet.

---

## 7. Troubleshooting

- **Can't connect remotely?**
  - Make sure your device is connected to Tailscale and logged into the correct account.
  - Check that the Tailscale service is running on your HomeServer.
- **Service not appearing?**
  - Confirm the service is running and included in your HomeServer portals.
- **Check logs:**
  - `sudo journalctl -u tailscaled -n 100 --no-pager`
- **Reconnect:**
  - Run `sudo tailscale up` again if needed.

---

## 8. Advanced Features & Documentation

- **Official Documentation:**
  - [Tailscale Documentation](https://tailscale.com/kb/)
- **MagicDNS:**
  - [Learn more about MagicDNS](https://tailscale.com/kb/1081/magicdns/)
- **ACLs & Sharing:**
  - [Access control and sharing](https://tailscale.com/kb/1018/acls/)

---

## 9. Credits & Attribution

**Tailscale** is a commercial VPN service created and maintained by Tailscale Inc. We extend our sincere gratitude to the Tailscale team for their excellent work in providing secure, easy-to-use VPN technology.

This HomeServer integration builds upon the excellent foundation provided by Tailscale, adapting it for seamless integration with our platform while maintaining full compatibility with the original service.

---

**Enjoy secure, private access to your HomeServer—anywhere, anytime!** 