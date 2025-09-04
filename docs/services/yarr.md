# Yarr RSS Reader Guide

## Quick Access

### Local Network Access
- **Web Interface**: [https://rss.home.arpa](https://rss.home.arpa)
- **Direct IP Access**: [https://rss.home.arpa](https://rss.home.arpa) 

### Remote Access (via Tailscale)
- **Remote URL**: [https://home.{YourTailnetNameHere}.ts.net/rss/](https://home.{YourTailnetNameHere}.ts.net/rss/)

---

## Overview

**Yarr** (Yet Another RSS Reader) is a modern, lightweight RSS feed reader that provides a clean and efficient way to follow your favorite websites and news sources. Built with Go for performance, it offers a fast, responsive interface for managing and reading your RSS feeds—all while running locally on your HomeServer.

---

## 1. Key Features

- **Feed Management:**
  - Subscribe to RSS/Atom feeds
  - Organize feeds into folders
  - Auto-update feed content
  - Import/Export OPML
- **Reading Experience:**
  - Clean, distraction-free interface
  - Mobile-friendly design
  - Keyboard shortcuts
  - Article preview
- **Performance:**
  - Go-powered backend
  - SQLite database
  - Minimal resource usage
  - Fast feed updates

---

## 2. Accessing Yarr

### Web Interface
- **Local Network:**
  - Access via `https://rss.home.arpa`
  - Or through your HomeServer dashboard
- **Remote Access:**
  - Use your Tailscale URL: `https://home.{YourTailnet}.ts.net/rss/`
  - See [Tailscale Guide](tailscale.md) for remote access details

### Interface Features
- **Layout Options:**
  - List view
  - Magazine view
  - Card view
- **Navigation:**
  - Folder organization
  - Feed filtering
  - Unread counters

---

## 3. Feed Management

### Basic Operations
- Add new feeds
- Create folders
- Organize subscriptions
- Mark items read/unread
- Star favorite articles
- Archive old content

### Advanced Features
- **Feed Organization:**
  - Hierarchical folders
  - Feed categories
  - Custom feed icons
  - Feed status monitoring
- **Content Management:**
  - Full article preview
  - Content filtering
  - Search functionality
  - Bulk operations

---

## 4. Security Features

### Authentication
- **User Access:**
  - Single-user system
  - Local authentication
  - Session management
- **Data Security:**
  - SQLite database security
  - Local storage only
  - No cloud dependencies

### System Integration
- **Service Security:**
  - Dedicated 'yarr' user
  - Limited system access
  - Isolated process
  - Secure file permissions

---

## 5. Configuration

### System Settings
- **Service Configuration:**
  - Running as 'yarr' user
  - Systemd service management
  - Automatic startup
- **Storage Settings:**
  - Database path: `/var/lib/yarr/yarr.db`
  - Application path: `/opt/yarr`
  - Cache directory: `/home/yarr/.cache`

### Application Settings
- **Database:**
  - SQLite with foreign key support
  - Automatic maintenance
  - Built-in backup support
- **Environment:**
  - Go runtime environment
  - System integration
  - Resource management

---

## 6. Advanced Features

### Integration
- **HomeServer Integration:**
  - Dashboard integration
  - System monitoring
  - Status reporting
- **Feed Features:**
  - Feed health monitoring
  - Update scheduling
  - Error reporting

### Customization
- **Interface:**
  - View preferences
  - Reading settings
  - Update intervals
- **Content:**
  - Feed grouping
  - Display options
  - Sort preferences

---

## 7. Troubleshooting

### Common Issues
- **Access Problems:**
  - Verify network connectivity
  - Check service status
  - Review permissions
- **Feed Issues:**
  - Validate feed URLs
  - Check feed status
  - Review update logs

### Logging
- **Log Access:**
  - System logs: `journalctl -u yarr`
  - Application status
  - Feed update logs

---

## 8. Best Practices

### Feed Management
- **Organization:**
  - Use meaningful folder names
  - Regular feed cleanup
  - Monitor feed health
- **Maintenance:**
  - Remove inactive feeds
  - Update feed URLs
  - Archive old content

### System Care
- **Regular Tasks:**
  - Monitor disk usage
  - Check service status
  - Update application
- **Database:**
  - Regular backups
  - Performance monitoring
  - Storage management

---

## 9. Credits & Attribution

**Yarr** (Yet Another RSS Reader) is an open-source project created and maintained by the Yarr community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

- **Original Project**: [Yarr on GitHub](https://github.com/nkanaev/yarr)
- **Maintainer**: [nkanaev](https://github.com/nkanaev)
- **License**: MIT
- **Documentation**: [Yarr Documentation](https://github.com/nkanaev/yarr#readme)

This HomeServer integration builds upon the excellent foundation provided by the Yarr project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Note:** Yarr is designed as a single-user RSS reader, perfect for personal use. The service runs with minimal resource usage and provides a fast, efficient way to keep up with your favorite content sources. 