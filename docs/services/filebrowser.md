# File Browser Guide

## Quick Access

### Local Network Access
- **Web Interface**: [https://files.home.arpa](https://files.home.arpa)
- **Direct IP Access**: [https://files.home.arpa](https://files.home.arpa)

### Remote Access (via Tailscale)
- **Remote URL**: [https://server.{YourTailnetNameHere}.ts.net/files/](https://server.{YourTailnetNameHere}.ts.net/files/)

---

## Overview

**File Browser** provides a modern web interface to manage files and folders on your HomeServer. It offers a secure, user-friendly way to browse, upload, download, and manage files stored on your NAS, with built-in authentication and comprehensive file operations.

---

## 1. Key Features

- **Modern Web Interface:**
  - Clean, intuitive design
  - Dark theme by default
  - Mobile-friendly layout
  - Responsive performance
- **File Operations:**
  - Upload and download files
  - Create, rename, and delete files/folders
  - Move and copy operations
  - Share files securely
- **Security Features:**
  - User authentication
  - Granular permissions system
  - Secure file sharing
  - Activity logging

---

## 2. Accessing File Browser

### Web Interface
- **Local Network:**
  - Access via `https://files.home.arpa`
  - Or through your HomeServer dashboard
- **Remote Access:**
  - Use your Tailscale URL: `https://server.{YourTailnet}.ts.net/files/`
  - See [Tailscale Guide](tailscale.md) for remote access details

### File Operations
- **Upload:**
  - Drag and drop files
  - Multi-file upload support
  - Progress tracking
- **Download:**
  - Single file downloads
  - Directory downloads (as ZIP)
  - Resumable downloads

---

## 3. File Management

### Basic Operations
- Create new folders
- Upload files and folders
- Move/Copy files
- Rename items
- Delete files/folders
- Download files

### Advanced Features
- **File Sharing:**
  - Generate share links
  - Set expiration times
  - Password protection
- **File Preview:**
  - Image thumbnails
  - Text file preview
  - PDF viewer
  - Video player

---

## 4. Security Features

### Authentication
- **User Management:**
  - Individual user accounts
  - Secure password storage
  - Session management
- **Permissions System:**
  - Granular access control
  - Directory-specific permissions
  - Operation-based restrictions

### Access Control
- **User Permissions:**
  - View files
  - Download files
  - Upload/modify files
  - Share files
  - Execute commands (disabled by default)
- **Admin Features:**
  - User management
  - Global settings
  - Activity monitoring

---

## 5. Configuration

### System Settings
- **Service Configuration:**
  - Running as dedicated 'filebrowser' user
  - Systemd service management
  - Automatic startup
- **Network Settings:**
  - Internal port configuration
  - HTTPS through reverse proxy
  - Local address binding

### Storage Settings
- **Root Directory:**
  - Base path: `/mnt/nas`
  - Automatic NAS integration
  - Consistent permissions
- **Database:**
  - SQLite database for settings
  - Located at `/etc/filebrowser/filebrowser.db`
  - Automatic backup support

---

## 6. Advanced Features

### Customization
- **Branding:**
  - Custom site name: 'Home Server'
  - Dark theme enabled
  - External links disabled
- **Interface:**
  - Responsive design
  - Mobile optimization
  - Keyboard shortcuts

### Integration
- **HomeServer Integration:**
  - Single sign-on support
  - Consistent styling
  - Dashboard integration
- **Storage:**
  - NAS mount integration
  - Automatic path mapping
  - Permission synchronization

---

## 7. Troubleshooting

### Common Issues
- **Access Problems:**
  - Verify network connectivity
  - Check authentication credentials
  - Confirm NAS mount status
- **Upload Issues:**
  - Check disk space
  - Verify file permissions
  - Review upload size limits

### Logging
- **Log Locations:**
  - Application logs: `/var/log/filebrowser`
  - System service logs: `journalctl -u filebrowser`
  - Access logs in dashboard

---

## 8. Best Practices

### File Management
- **Organization:**
  - Use meaningful folder names
  - Maintain folder structure
  - Regular cleanup of temporary files
- **Security:**
  - Use strong passwords
  - Review share links regularly
  - Monitor access logs

### System Maintenance
- **Regular Tasks:**
  - Check disk usage
  - Review user permissions
  - Monitor system logs
- **Updates:**
  - Keep File Browser updated
  - Check for security updates
  - Backup configuration

---

**Note:** File Browser is configured for security by default with authentication required and external links disabled. Contact your system administrator for account creation. 