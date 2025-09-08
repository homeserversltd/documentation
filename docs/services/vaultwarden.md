# Vaultwarden Password Manager Guide

## Official Resources & Support

!!! info "Service-Specific Issues"
    **Experiencing issues with Vaultwarden functionality?** Please create an issue ticket with the original developers so they can fix it for everyone. HomeServer LLC provides the integration and hosting platform only.

### Official Links
- **Original Project**: [Vaultwarden on GitHub](https://github.com/dani-garcia/vaultwarden)
- **Maintainer**: [dani-garcia](https://github.com/dani-garcia)
- **License**: GPL v3
- **Official Documentation**: [Vaultwarden Documentation](https://github.com/dani-garcia/vaultwarden/wiki)

## Quick Access

### Local Network Access
- **Web Interface**: [https://vault.home.arpa](https://vault.home.arpa)
- **Direct IP Access**: [https://vault.home.arpa](https://vault.home.arpa)

### Remote Access (via Tailscale)
- **Remote URL**: [https://home.{YourTailnetNameHere}.ts.net/vault/](https://home.{YourTailnetNameHere}.ts.net/vault/)

---

## Overview

**Vaultwarden** is your secure, self-hosted password manager, fully compatible with Bitwarden clients. With Vaultwarden, you can safely store, organize, and access your passwords, notes, and other secrets from any device—web, mobile, or browser extension. Vaultwarden is seamlessly integrated into your HomeServer, so you always have secure, local access to your credentials.

---

## 1. Accessing Vaultwarden

- **Web Interface:**
  - Open [https://vault.home.arpa](https://vault.home.arpa) in your browser.
- **Remote Access:**
  - Use [https://home.{YourTailnetNameHere}.ts.net/vault/](https://home.{YourTailnetNameHere}.ts.net/vault/) when connected via Tailscale.
- **Portal Shortcut:**
  - Find Vaultwarden in your HomeServer portal under "Password Manager" or "Vaultwarden".

---

## 2. What Can You Do With Vaultwarden?

- **Store Passwords & Secrets:**
  - Save logins, secure notes, credit cards, and identities in your encrypted vault.
- **Autofill & Generate Passwords:**
  - Use browser extensions or mobile apps to autofill logins and generate strong passwords.
- **Share Securely:**
  - Share credentials with trusted users (if enabled by your admin).
- **Access Anywhere:**
  - Use the web app, mobile apps, or browser extensions—your vault is always available.
- **Two-Factor Authentication:**
  - Add an extra layer of security to your account.

---

## 3. Using Vaultwarden

- **Log In:**
  - Open the web interface or your Bitwarden-compatible app.
  - Set the server URL to `https://vault.home.arpa`.
  - Enter your email and password. (Contact your admin if you need an account or password reset.)
- **Add Items:**
  - Click "Add Item" to save a new login, note, card, or identity.
- **Organize:**
  - Use folders, collections, and tags to keep your vault tidy.
- **Autofill:**
  - Install the Bitwarden browser extension and log in with your Vaultwarden credentials for one-click autofill.
- **Mobile Access:**
  - Use the Bitwarden app (Android/iOS) and set the server URL to your Vaultwarden instance.

---

## 4. Integration with HomeServer

- **Portal Integration:**
  - Vaultwarden is available as a portal in your HomeServer dashboard for one-click access.
- **Permissions:**
  - Access is managed by HomeServer. Only authorized users can create or manage vaults.
- **homeserver.json:**
  - Vaultwarden's configuration and permissions are defined in the `homeserver.json` file, ensuring seamless integration and access control. (See [Platform Configuration](homeserver.json.md))

---

## 5. Security & Best Practices

- **Strong Passwords:**
  - Use the built-in password generator for all new logins.
- **Enable 2FA:**
  - Add two-factor authentication to your account for extra protection.
- **Keep Your Vault Backed Up:**
  - Regularly export your vault or ensure your HomeServer is backed up.
- **Never Share Your Master Password:**
  - Only you should know your master password.

---

## 6. Troubleshooting

- **Can't log in?**
  - Contact your system administrator for account help or password reset.
- **Browser extension not connecting?**
  - Double-check the server URL and your credentials.
- **Mobile app issues?**
  - Ensure the app is set to use your Vaultwarden server URL.
- **Forgot your master password?**
  - For security, only you can reset your master password. Contact your admin for account recovery options.

---

## 7. Advanced Features & Documentation

- **Official Documentation:**
  - [Vaultwarden Documentation](https://github.com/dani-garcia/vaultwarden/wiki)
- **Bitwarden Clients:**
  - [Bitwarden Apps & Extensions](https://bitwarden.com/download/)
- **Admin Panel:**
  - If enabled, access at `/admin` with your admin token (ask your admin for details).

---

## 8. Credits & Attribution

**Vaultwarden** is an open-source project created and maintained by the Vaultwarden community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

This HomeServer integration builds upon the excellent foundation provided by the Vaultwarden project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Your passwords, always safe, always with you.**
