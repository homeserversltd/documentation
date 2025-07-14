# SMB Development Workflow

## Overview

The HomeServer provides SMB (Samba) shares that enable efficient development workflows. By mounting these shares locally, you can easily deploy code, configuration files, and other resources to "tricky places" on the server using rsync. This approach is particularly useful for deploying to system directories that require elevated privileges.

---

## 1. SMB Share Configuration

### 1.1 Available Shares

The HomeServer exposes several SMB shares for development access:

| Share Name | Path | Purpose | Access |
|------------|------|---------|---------|
| `webroot` | `/var/www/homeserver` | Web application files | Admin user |
| `docs` | `/opt/docs` | MkDocs documentation | Admin user |
| `nas` | `/mnt/nas` | NAS storage | Admin user |

### 1.2 Current SMB Configuration

The SMB configuration is defined in `/etc/samba/smb.conf`:

```ini
[webroot]
comment = Web Server Root Directory
path = /var/www/homeserver
browseable = yes
read only = no
create mask = 0777
directory mask = 0777
valid users = ${ADMIN_USER}
force user = ${ADMIN_USER}

[docs]
comment = MkDocs Documentation Root
path = /opt/docs
browseable = yes
read only = no
create mask = 0777
directory mask = 0777
valid users = ${ADMIN_USER}
force user = ${ADMIN_USER}
```

### 1.3 Adding New SMB Shares

To add a new development share, add a section to `smb.conf`:

```ini
[sharename]
comment = Description of the share
path = /path/to/directory
browseable = yes
read only = no
create mask = 0777
directory mask = 0777
valid users = ${ADMIN_USER}
force user = ${ADMIN_USER}
```

**Key Configuration Options:**
- `path`: Server directory to share
- `valid users`: Users allowed to access (use `${ADMIN_USER}` for admin)
- `force user`: Force all operations as this user
- `create mask`/`directory mask`: File/directory permissions (0777 for full access)
- `browseable`: Show in network browser
- `read only`: Set to `no` for write access

---

## 2. Development Workflow Setup

### 2.1 Mount SMB Shares Locally

Mount the server shares to your local development machine:

```bash
# Create mount points
sudo mkdir -p /mnt/homeserver-webroot
sudo mkdir -p /mnt/homeserver-docs
sudo mkdir -p /mnt/homeserver-nas

# Mount shares (replace with your server IP and credentials)
sudo mount -t cifs //192.168.123.1/webroot /mnt/homeserver-webroot \
  -o username=admin,password=your-password,vers=3.0,uid=$(id -u),gid=$(id -g)

sudo mount -t cifs //192.168.123.1/docs /mnt/homeserver-docs \
  -o username=admin,password=your-password,vers=3.0,uid=$(id -u),gid=$(id -g)

sudo mount -t cifs //192.168.123.1/nas /mnt/homeserver-nas \
  -o username=admin,password=your-password,vers=3.0,uid=$(id -u),gid=$(id -g)
```

### 2.2 Persistent Mounting

For persistent mounts across reboots, add entries to `/etc/fstab`:

```bash
# Add to /etc/fstab
//192.168.123.1/webroot /mnt/homeserver-webroot cifs username=admin,password=your-password,vers=3.0,uid=1000,gid=1000,iocharset=utf8 0 0
//192.168.123.1/docs /mnt/homeserver-docs cifs username=admin,password=your-password,vers=3.0,uid=1000,gid=1000,iocharset=utf8 0 0
//192.168.123.1/nas /mnt/homeserver-nas cifs username=admin,password=your-password,vers=3.0,uid=1000,gid=1000,iocharset=utf8 0 0
```

**Security Note:** Consider using a credentials file instead of embedding passwords:
```bash
# Create credentials file
sudo nano /etc/samba/credentials
# Add:
# username=admin
# password=your-password

# Use in mount command
sudo mount -t cifs //192.168.123.1/webroot /mnt/homeserver-webroot \
  -o credentials=/etc/samba/credentials,vers=3.0,uid=$(id -u),gid=$(id -g)
```

---

## 3. Rsync Deployment Workflows

### 3.1 Basic Rsync Deployment

Deploy your local development files to the server:

```bash
# Deploy web application
sudo rsync -av --delete \
  --exclude='venv' \
  --exclude='*.pyc' \
  --exclude='__pycache__' \
  --exclude='.git' \
  --exclude='node_modules' \
  --exclude='test-results' \
  --exclude='playwright-report' \
  initialization/flask/inject/ \
  /mnt/homeserver-webroot/

# Deploy documentation
sudo rsync -av --delete \
  --exclude='.git' \
  initialization/networkservices/mkdocs/config/ \
  /mnt/homeserver-docs/
```

### 3.2 Selective Deployment

Deploy specific components or configurations:

```bash
# Deploy only configuration files
sudo rsync -av \
  initialization/flask/inject/src/config/ \
  /mnt/homeserver-webroot/src/config/

# Deploy only backend changes
sudo rsync -av --delete \
  --exclude='*.pyc' \
  --exclude='__pycache__' \
  initialization/flask/inject/backend/ \
  /mnt/homeserver-webroot/backend/

# Deploy only frontend changes
sudo rsync -av --delete \
  --exclude='node_modules' \
  initialization/flask/inject/src/ \
  /mnt/homeserver-webroot/src/
```

### 3.3 Network Service Configurations

Deploy network service configurations to system directories:

```bash
# Deploy Samba configuration
sudo rsync -av \
  initialization/networkservices/samba/config/smb.conf \
  /mnt/homeserver-nas/system-configs/samba/

# Deploy Nginx configurations
sudo rsync -av \
  initialization/networkservices/nginx/config/ \
  /mnt/homeserver-nas/system-configs/nginx/

# Deploy systemd service files
sudo rsync -av \
  initialization/networkservices/*/config/*.service \
  /mnt/homeserver-nas/system-configs/systemd/
```

---

## 4. Advanced Deployment Patterns

### 4.1 Automated Deployment Script

Create a deployment script for common workflows:

```bash
#!/bin/bash
# deploy.sh - HomeServer deployment script

set -e

WEBROOT_MOUNT="/mnt/homeserver-webroot"
DOCS_MOUNT="/mnt/homeserver-docs"
NAS_MOUNT="/mnt/homeserver-nas"

# Check if mounts are available
check_mounts() {
    if ! mountpoint -q "$WEBROOT_MOUNT"; then
        echo "Error: Webroot not mounted at $WEBROOT_MOUNT"
        exit 1
    fi
}

# Deploy web application
deploy_webapp() {
    echo "Deploying web application..."
    sudo rsync -av --delete \
        --exclude='venv' \
        --exclude='*.pyc' \
        --exclude='__pycache__' \
        --exclude='.git' \
        --exclude='node_modules' \
        --exclude='test-results' \
        --exclude='playwright-report' \
        initialization/flask/inject/ \
        "$WEBROOT_MOUNT/"
    echo "Web application deployed successfully"
}

# Deploy documentation
deploy_docs() {
    echo "Deploying documentation..."
    sudo rsync -av --delete \
        --exclude='.git' \
        initialization/networkservices/mkdocs/config/ \
        "$DOCS_MOUNT/"
    echo "Documentation deployed successfully"
}

# Deploy configurations
deploy_configs() {
    echo "Deploying configurations..."
    sudo rsync -av \
        initialization/networkservices/samba/config/smb.conf \
        "$NAS_MOUNT/system-configs/samba/"
    echo "Configurations deployed successfully"
}

# Main deployment logic
case "${1:-all}" in
    webapp)
        check_mounts
        deploy_webapp
        ;;
    docs)
        check_mounts
        deploy_docs
        ;;
    configs)
        check_mounts
        deploy_configs
        ;;
    all)
        check_mounts
        deploy_webapp
        deploy_docs
        deploy_configs
        ;;
    *)
        echo "Usage: $0 {webapp|docs|configs|all}"
        exit 1
        ;;
esac

echo "Deployment completed successfully"
```

### 4.2 Watch and Auto-Deploy

Set up automatic deployment on file changes:

```bash
# Install inotify-tools
sudo apt install inotify-tools

# Watch for changes and auto-deploy
inotifywait -m -r -e modify,create,delete \
    initialization/flask/inject/src/ \
    --format '%w%f %e' | while read file event; do
    echo "File $file changed ($event), deploying..."
    sudo rsync -av \
        initialization/flask/inject/src/ \
        /mnt/homeserver-webroot/src/
done
```

---

## 5. Service Management After Deployment

### 5.1 Restart Services via SSH

After deploying changes, restart services on the server:

```bash
# Restart web application
sshpass -p 'your-password' ssh admin@192.168.123.1 \
    'sudo systemctl restart gunicorn.service'

# Restart documentation service
sshpass -p 'your-password' ssh admin@192.168.123.1 \
    'sudo systemctl restart mkdocs.service'

# Restart Samba after configuration changes
sshpass -p 'your-password' ssh admin@192.168.123.1 \
    'sudo systemctl restart smbd.service'
```

### 5.2 Build and Restart Workflow

Complete deployment with build and restart:

```bash
# Deploy, build, and restart
deploy_and_restart() {
    # Deploy files
    sudo rsync -av --delete \
        --exclude='venv' --exclude='*.pyc' --exclude='__pycache__' \
        --exclude='.git' --exclude='node_modules' \
        initialization/flask/inject/ \
        /mnt/homeserver-webroot/
    
    # SSH to server and restart services
    sshpass -p 'your-password' ssh admin@192.168.123.1 \
        'cd /var/www/homeserver && npm install && npm run build && sudo systemctl restart gunicorn.service'
}
```

---

## 6. Troubleshooting SMB Development

### 6.1 Common Mount Issues

**Permission Denied:**
```bash
# Check SMB credentials
smbclient -L //192.168.123.1 -U admin

# Verify mount options include correct uid/gid
mount | grep cifs
```

**Mount Fails:**
```bash
# Check SMB service status on server
sshpass -p 'password' ssh admin@192.168.123.1 'sudo systemctl status smbd'

# Test SMB connectivity
telnet 192.168.123.1 445
```

**Stale Mounts:**
```bash
# Force unmount stale mounts
sudo umount -f /mnt/homeserver-webroot

# Clear SMB cache
sudo smbcontrol all close-share webroot
```

### 6.2 Rsync Issues

**Permission Errors:**
```bash
# Ensure proper ownership on target
sudo chown -R www-data:www-data /mnt/homeserver-webroot/

# Use --no-perms to ignore permission preservation
sudo rsync -av --no-perms source/ destination/
```

**Partial Transfers:**
```bash
# Use --partial to resume interrupted transfers
sudo rsync -av --partial --progress source/ destination/

# Verify transfer with checksums
sudo rsync -av --checksum source/ destination/
```

---

## 7. Security Considerations

### 7.1 Network Security
- Use SMB3 protocol version for encryption
- Restrict SMB access to trusted networks
- Consider VPN access for remote development

### 7.2 Access Control
- Use dedicated development user accounts
- Implement least-privilege access
- Regularly rotate SMB passwords

### 7.3 File Permissions
- Maintain proper file ownership after deployment
- Use appropriate umask settings
- Verify service account permissions

---

## 8. Best Practices

### 8.1 Development Workflow
1. **Test Locally First**: Always test changes locally before deployment
2. **Incremental Deployment**: Deploy small, focused changes
3. **Backup Before Deploy**: Keep backups of critical configurations
4. **Verify After Deploy**: Test functionality after each deployment

### 8.2 File Management
- Use `.gitignore` patterns in rsync excludes
- Maintain clean separation between development and production files
- Document deployment procedures for team members

### 8.3 Performance Optimization
- Use `--delete` carefully to avoid unintended file removal
- Leverage rsync's `--checksum` for accuracy when needed
- Monitor network bandwidth during large deployments

---

**The SMB development workflow provides a powerful, flexible way to deploy code and configurations to your HomeServer efficiently and securely!** 