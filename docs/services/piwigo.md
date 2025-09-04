# Piwigo Photo Gallery Guide

## Quick Access

### Local Network Access
- **Web Interface**: [https://piwigo.home.arpa](https://piwigo.home.arpa)
- **Direct IP Access**: [https://piwigo.home.arpa](https://piwigo.home.arpa)

### Remote Access (via Tailscale)
- **Remote URL**: [https://home.{YourTailnetNameHere}.ts.net/piwigo/](https://home.{YourTailnetNameHere}.ts.net/piwigo/)

---

## Overview

**Piwigo** is your personal photo gallery management system that allows you to organize, share, and display your photo collections through a beautiful web interface. With Piwigo, you can create albums, manage metadata, and share your memories with family and friends—all hosted securely on your HomeServer.

---

## ⚠️ CRITICAL: Photo Upload Method

!!! warning "Use HomeServer Upload Only"
    **DO NOT use Piwigo's built-in upload functionality.** Photos uploaded directly through Piwigo's interface will be stored on the device itself rather than the NAS storage.
    
    **Always use the HomeServer's upload method** (File Browser or Upload tab) to ensure photos are properly stored on NAS storage.
    
    While there is a nightly cleanup service that will attempt to move misplaced files back to NAS storage on a "best effort" basis, **this process is not guaranteed** and may result in data loss or organizational issues.
    
    **Use the supported upload method provided by the HomeServer for reliable photo management.**

---

## 1. Accessing Piwigo

- **Web Interface:**
  - Open [https://piwigo.home.arpa](https://piwigo.home.arpa) in your browser.
- **Remote Access:**
  - Use [https://home.{YourTailnetNameHere}.ts.net/piwigo/](https://home.{YourTailnetNameHere}.ts.net/piwigo/) when connected via Tailscale.
- **Portal Shortcut:**
  - Find Piwigo in your HomeServer portal under "Media" or "Photos".

---

## 2. What Can You Do With Piwigo?

- **Organize Photos:**
  - Create albums and sub-albums to categorize your photos
  - Add descriptions, tags, and metadata to your images
  - Batch operations for efficient management
- **Share Collections:**
  - Create public or private albums
  - Generate share links for specific albums
  - Control access permissions for different users
- **Browse & Search:**
  - Advanced search by tags, dates, and metadata
  - Timeline view for chronological browsing
  - Thumbnail and slideshow viewing modes
- **User Management:**
  - Multiple user accounts with different permission levels
  - Guest access for public albums
  - Admin controls for gallery management

---

## 3. Proper Photo Upload Workflow

### Step 1: Upload Photos via HomeServer
1. **Use File Browser:**
   - Navigate to [https://files.home.arpa](https://files.home.arpa)
   - Upload photos to `/mnt/nas/photos/` directory
2. **Use Upload Tab:**
   - Access the Upload tab in your HomeServer dashboard
   - Select photos and upload to the photos directory

### Step 2: Organize in Piwigo
1. **Access Piwigo Admin:**
   - Log into Piwigo with admin credentials
   - Navigate to Administration panel
2. **Synchronize Files:**
   - Go to Tools > Synchronization
   - Run synchronization to detect new photos
3. **Create Albums:**
   - Organize detected photos into albums
   - Add metadata and descriptions

### What NOT to Do
- ❌ Do not use Piwigo's "Upload" button in the web interface
- ❌ Do not drag and drop files directly into Piwigo
- ❌ Do not use Piwigo's batch upload tools

---

## 4. Using the Piwigo Web Interface

### Viewing Photos
- **Album Navigation:**
  - Browse through your organized album structure
  - Use breadcrumb navigation to move between levels
- **Photo Viewing:**
  - Click any photo for full-size viewing
  - Use arrow keys or navigation buttons for slideshow
  - View EXIF data and photo information
- **Search Features:**
  - Search by tags, keywords, or dates
  - Filter by album, author, or file type
  - Advanced search with multiple criteria

### Album Management
- **Create Albums:**
  - Use the admin interface to create new albums
  - Set album descriptions and permissions
  - Organize albums in hierarchical structure
- **Photo Organization:**
  - Move photos between albums
  - Add tags and descriptions
  - Set photo permissions and visibility

---

## 5. Administration Features

### User Management
- **User Accounts:**
  - Create accounts for family members or friends
  - Set different permission levels (admin, user, guest)
  - Manage user groups and access rights
- **Privacy Settings:**
  - Control album visibility
  - Set password protection for sensitive albums
  - Configure guest access permissions

### Gallery Configuration
- **Appearance:**
  - Choose from various themes and layouts
  - Customize gallery colors and branding
  - Configure thumbnail sizes and display options
- **Functionality:**
  - Enable/disable features like comments and ratings
  - Configure metadata display options
  - Set up automatic slideshow settings

---

## 6. Integration with HomeServer

- **Portal Integration:**
  - Piwigo is available as a portal in your HomeServer dashboard for one-click access.
- **Storage Integration:**
  - Photos are stored on NAS storage at `/mnt/nas/photos/`
  - Automatic backup and redundancy through NAS configuration
- **Permissions:**
  - Access control managed through HomeServer authentication
  - Consistent user management across all services
- **homeserver.json:**
  - Piwigo's configuration and permissions are defined in the `homeserver.json` file, ensuring seamless integration and access control.

---

## 7. Mobile Access

### Mobile Web Interface
- **Responsive Design:**
  - Piwigo's web interface works well on mobile devices
  - Touch-friendly navigation and controls
  - Optimized photo viewing on small screens

### Mobile Apps
- **Third-Party Apps:**
  - Various mobile apps available for iOS and Android
  - Configure with your server URL: `https://piwigo.home.arpa`
  - Use your Piwigo user credentials for authentication

---

## 8. Troubleshooting

### Common Issues
- **Photos Not Appearing:**
  - Verify photos were uploaded via HomeServer (not Piwigo directly)
  - Run synchronization in Piwigo admin panel
  - Check file permissions on `/mnt/nas/photos/`
- **Upload Problems:**
  - Remember: Only use HomeServer upload methods
  - Check available disk space on NAS
  - Verify network connectivity to file services
- **Access Issues:**
  - Confirm user credentials and permissions
  - Check HomeServer authentication status
  - Verify network connectivity

### File Recovery
- **Misplaced Photos:**
  - If photos were accidentally uploaded via Piwigo interface
  - Check nightly cleanup logs for recovery attempts
  - Contact system administrator for manual recovery
  - **Prevention is better than recovery - always use HomeServer upload**

---

## 9. Best Practices

### Photo Management
- **Organization:**
  - Use descriptive album names and hierarchical structure
  - Add meaningful tags and descriptions to photos
  - Regularly organize and clean up your photo collection
- **Upload Workflow:**
  - Always upload via HomeServer File Browser or Upload tab
  - Organize photos in folders before uploading
  - Use consistent naming conventions for files and albums

### Security
- **Access Control:**
  - Regularly review user permissions and access rights
  - Use strong passwords for admin accounts
  - Monitor access logs for unusual activity
- **Privacy:**
  - Be mindful of photo metadata and location information
  - Configure appropriate privacy settings for sensitive albums
  - Regularly review public album settings

---

## 10. Advanced Features & Documentation

- **Official Documentation:**
  - [Piwigo Documentation](https://piwigo.org/doc/doku.php)
- **Plugin System:**
  - Extend functionality with [Piwigo plugins](https://piwigo.org/ext/)
- **API Access:**
  - [Piwigo API documentation](https://piwigo.org/doc/doku.php?id=dev:webapi) for developers

---

## 11. Credits & Attribution

**Piwigo** is an open-source project created and maintained by the Piwigo community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

- **Original Project**: [Piwigo on GitHub](https://github.com/Piwigo/Piwigo)
- **Maintainer**: [Piwigo](https://github.com/Piwigo)
- **License**: GPL v2
- **Documentation**: [Piwigo Documentation](https://piwigo.org/doc/doku.php)

This HomeServer integration builds upon the excellent foundation provided by the Piwigo project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Remember: Always upload photos through the HomeServer interface to ensure proper storage and organization!** 