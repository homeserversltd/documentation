# Gogs Git Server

## Quick Access

### Local Network Access
- **Web Interface**: [https://git.home.arpa/git/](https://git.home.arpa/git/)
- **Direct IP Access**: [https://git.home.arpa/git/](https://git.home.arpa/git/) 

### Remote Access (via Tailscale)
- **Remote URL**: [https://server.{YourTailnetNameHere}.ts.net/git/](https://server.{YourTailnetNameHere}.ts.net/git/)

## Overview

**Gogs** (Go Git Service) is a lightweight, self-hosted Git service running on your HomeServer. It provides a complete GitHub-like experience with repositories, issue tracking, and collaboration tools—all while keeping your code private and secure on your own hardware.

---

## 1. Key Features

- **Complete Git Platform:**
  - Self-hosted Git repositories
  - Web-based repository management
  - Issue tracking and collaboration tools
  - Built-in wiki system
- **Security Features:**
  - SSH key authentication
  - PostgreSQL database backend
  - Granular access control
  - Private repositories
- **Integration:**
  - Seamless HomeServer dashboard access
  - Automatic backup with NAS integration
  - Single sign-on with HomeServer admin

---

## 2. Accessing Gogs

### Web Interface
- **Local Network:**
  - Access via `https://git.home.arpa/git/`
  - Or through your HomeServer dashboard
- **Remote Access:**
  - Use your Tailscale URL: `https://server.{YourTailnet}.ts.net/git/`
  - See [Tailscale Guide](tailscale.md) for remote access details

### Git Operations
- **HTTPS Access:**
  - Clone: `https://git.home.arpa/git/username/repository`
  - Push/Pull with your Gogs credentials
- **SSH Access:**
  - Clone: `git@git.home.arpa:username/repository`
  - Requires SSH key setup in Gogs interface

---

## 3. Repository Management

### Creating Repositories
1. Log in to the Gogs web interface
2. Click the "+" icon in the top navigation
3. Fill in repository details:
   - Name
   - Description
   - Visibility (Public/Private)
   - Initialize with README (optional)
4. Click "Create Repository"

### Managing Access
- Add collaborators through repository settings
- Manage SSH keys in user settings
- Control repository visibility
- Set branch protections

---

## 4. Security Features

### Authentication
- **Local Authentication:**
  - Username/password login
  - SSH key authentication for Git operations
- **Access Control:**
  - Private repositories
  - Collaborator management
  - Organization support
- **Security Settings:**
  - Registration disabled by default
  - Mandatory sign-in for repository viewing
  - Gravatar disabled for privacy

### Data Protection
- **Database Security:**
  - PostgreSQL backend
  - Encrypted credentials
  - Secure session management
- **File Security:**
  - Protected repository storage
  - Secure configuration files
  - Restricted system access

---

## 5. Configuration

### System Settings
- **Service Configuration:**
  - Running as dedicated 'git' user
  - Systemd service management
  - Automatic startup
- **Network Settings:**
  - Port 3000 (internal)
  - HTTPS through reverse proxy
  - SSH on standard port 22

### Repository Settings
- **Storage Location:**
  - Base path: `/mnt/nas/git/repositories`
  - Automatic NAS integration
  - Regular backups
- **Web Interface:**
  - Custom branding
  - Markdown support
  - Code highlighting

---

## 6. Advanced Features

### Integration Options
- **Webhook Support:**
  - Post-receive hooks
  - Custom automation
  - External service integration
- **API Access:**
  - REST API available
  - Token authentication
  - Automated operations

### Administration
- **User Management:**
  - Create/modify users
  - Organization management
  - Access control
- **System Monitoring:**
  - Activity logs
  - System statistics
  - Performance metrics

---

## 7. Troubleshooting

### Common Issues
- **Access Problems:**
  - Verify network connectivity
  - Check authentication credentials
  - Confirm SSH key setup
- **Repository Issues:**
  - Check file permissions
  - Verify disk space
  - Review error logs

### Logging
- **Log Locations:**
  - Application logs: `/var/log/gogs`
  - System service logs: `journalctl -u gogs`
  - SSH access logs: `journalctl -u sshd`

---

## 8. Best Practices

### Repository Management
- **Regular Maintenance:**
  - Monitor disk usage
  - Review access logs
  - Update SSH keys
- **Backup Strategy:**
  - Regular repository backups
  - Configuration backups
  - Database backups

### Security
- **Access Control:**
  - Use strong passwords
  - Regularly rotate SSH keys
  - Review collaborator access
- **System Updates:**
  - Keep Gogs updated
  - Monitor security advisories
  - Update system dependencies

---

## 9. Credits & Attribution

**Gogs** (Go Git Service) is an open-source project created and maintained by the Gogs community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

- **Original Project**: [Gogs on GitHub](https://github.com/gogs/gogs)
- **Maintainer**: [gogs](https://github.com/gogs)
- **License**: MIT
- **Documentation**: [Gogs Documentation](https://gogs.io/docs)

This HomeServer integration builds upon the excellent foundation provided by the Gogs project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Note:** Gogs is configured for security by default with registration disabled and mandatory sign-in for repository viewing. Contact your system administrator for account creation. 