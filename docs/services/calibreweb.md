# Calibre Web E-book Manager Guide

## Quick Access

### Local Network Access
- **Web Interface**: [https://books.home.arpa](https://books.home.arpa)
- **Direct IP Access**: [https://books.home.arpa](https://books.home.arpa) 
### Remote Access (via Tailscale)
- **Remote URL**: [https://server.{YourTailnetNameHere}.ts.net/books/](https://server.{YourTailnetNameHere}.ts.net/books/)

---

## Overview

**Calibre Web** is a feature-rich e-book server that provides a clean web interface to browse, read, and manage your digital book collection. It offers comprehensive e-book management with support for multiple formats, metadata management, and a responsive reading experience—all integrated with your HomeServer's NAS storage.

---

## 1. Key Features

- **Digital Library Management:**
  - Browse and organize e-books
  - Multiple format support
  - Metadata management
  - Cover art display
- **Reading Features:**
  - In-browser e-book reader
  - Progress tracking
  - Bookmarking system
  - Mobile-friendly interface
- **Library Organization:**
  - Custom categories
  - Series management
  - Author organization
  - Tag system

---

## 2. Accessing Calibre Web

### Web Interface
- **Local Network:**
  - Access via `https://books.home.arpa`
  - Or through your HomeServer dashboard
- **Remote Access:**
  - Use your Tailscale URL: `https://server.{YourTailnet}.ts.net/books/`
  - See [Tailscale Guide](tailscale.md) for remote access details

### Library Features
- **Browse:**
  - Grid or list view
  - Sort by title, author, series
  - Filter by tags or categories
- **Search:**
  - Full-text search
  - Advanced filtering
  - Metadata search

---

## 3. Book Management

### Basic Operations
- Upload new books
- Edit metadata
- Organize collections
- Download books
- Delete entries
- Update cover art

### Advanced Features
- **Metadata Management:**
  - Automatic metadata fetching
  - Bulk metadata editing
  - Series organization
  - Custom metadata fields
- **Format Conversion:**
  - Convert between formats
  - Optimize for devices
  - Maintain quality settings
  - Batch processing

---

## 4. Security Features

### Authentication
- **User Management:**
  - Individual user accounts
  - Role-based permissions
  - Guest access options
- **Access Control:**
  - Reading permissions
  - Download restrictions
  - Upload privileges
  - Admin functions

### Data Protection
- **Library Security:**
  - Secure storage on NAS
  - Regular backups
  - File integrity checks
- **User Privacy:**
  - Reading progress privacy
  - Personal bookshelf
  - Secure sessions

---

## 5. Configuration

### System Settings
- **Service Configuration:**
  - Running as 'calibre' user
  - Systemd service management
  - Automatic startup
- **Storage Settings:**
  - Library path: `/mnt/nas/books`
  - Backup location: `/mnt/nas/backup/calibre-web`
  - Log directory: `/var/log/calibre-web`

### Application Settings
- **Database:**
  - SQLite metadata database
  - Automatic initialization
  - Regular backups
- **Environment:**
  - Python virtual environment
  - ImageMagick integration
  - Unrar support

---

## 6. Advanced Features

### Integration
- **HomeServer Integration:**
  - NAS storage integration
  - Backup system integration
  - Dashboard access
- **External Services:**
  - Metadata lookup services
  - Cover art databases
  - Book information sources

### Customization
- **Interface:**
  - Custom categories
  - Display preferences
  - Reading settings
- **Library:**
  - Custom metadata fields
  - Organization schemes
  - View customization

---

## 7. Troubleshooting

### Common Issues
- **Access Problems:**
  - Verify network connectivity
  - Check authentication credentials
  - Confirm NAS mount status
- **Library Issues:**
  - Check file permissions
  - Verify metadata database
  - Review storage space

### Logging
- **Log Locations:**
  - Application logs: `/var/log/calibre-web/calibre-web.log`
  - System service logs: `journalctl -u calibre-web`
  - Standard output/error in logs

---

## 8. Best Practices

### Library Management
- **Organization:**
  - Consistent naming scheme
  - Complete metadata
  - Regular backups
- **Maintenance:**
  - Update metadata regularly
  - Check for duplicates
  - Verify file integrity

### System Care
- **Regular Tasks:**
  - Monitor disk usage
  - Check log files
  - Update software
- **Backup Strategy:**
  - Regular database backups
  - Configuration backups
  - Library backups

---

**Note:** Initial admin credentials are admin/admin123. Please change these immediately after first login for security. The service is configured to store books on your NAS at `/mnt/nas/books` with automatic backups to `/mnt/nas/backup/calibre-web`. 