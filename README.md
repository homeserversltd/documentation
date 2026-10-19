# HOMESERVER Documentation Repository

## Overview

This repository contains the official documentation for the HOMESERVER platform—a professional-grade digital sovereignty solution that provides complete independence from Big Tech surveillance. This documentation is designed as a living, user-centric resource that is automatically distributed to all HOMESERVER devices worldwide.

**Repository:** [https://github.com/homeserversltd/documentation](https://github.com/homeserversltd/documentation)

---

## What This Repository Contains

### 📚 Complete Documentation Suite
- **Setup Guides**: Physical setup, network configuration, security, and verification
- **Service Documentation**: Comprehensive guides for all integrated services (Jellyfin, Vaultwarden, Gogs, etc.)
- **Developer Resources**: Platform configuration, development workflows, API reference
- **Certificate Management**: SSL/TLS installation, renewal, and troubleshooting
- **Troubleshooting**: Common issues, service-specific problems, performance optimization

### 🎯 Target Audience
- **HOMESERVER Customers**: Complete setup and usage guides
- **System Administrators**: Advanced configuration and maintenance
- **Developers**: Platform integration and customization
- **Technical Users**: Deep-dive into system architecture and capabilities

---

## Documentation Philosophy

### 1. Professional-Grade, Not Consumer Appliance
- **Complexity as Feature**: Embrace technical requirements as quality signals
- **System Administrator Level**: Assume technical competence in target audience
- **Digital Sovereignty**: Position as "datacenter in a box" for privacy-conscious professionals
- **Enterprise Integration**: Focus on complete digital stack ownership

### 2. Always Up-to-Date, Locally Available
- **Automatic Distribution**: Documentation bundled with every HOMESERVER software release
- **Offline Access**: Users always have latest docs locally—no internet required after sync
- **Global Reach**: Designed for worldwide audience with clear, precise technical language

### 3. Extensible & Collaborative
- **Easy Contribution**: Add or improve docs by editing Markdown files and updating navigation
- **Infinite Extensibility**: Add unlimited documentation with flexible organization
- **Git-Based Workflow**: Standard Git contribution model with pull requests and reviews

---

## Repository Structure

```
docs/
├── index.md                    # Landing page and overview
├── setup/                      # Complete setup process
│   ├── setup-physical.md      # Hardware and network setup
│   ├── setup-network.md       # Network access configuration
│   ├── setup-admin.md         # Administrative access
│   ├── setup-security.md      # Vault and security configuration
│   ├── setup-verification.md  # System verification
│   └── setup-management.md    # Ongoing management
├── services/                   # Service-specific documentation
│   ├── jellyfin.md           # Media server guide
│   ├── vaultwarden.md        # Password manager guide
│   ├── gogs.md               # Git server guide
│   ├── filebrowser.md        # File management guide
│   ├── calibreweb.md         # E-book manager guide
│   ├── navidrome.md          # Music server guide
│   ├── piwigo.md             # Photo gallery guide
│   ├── tailscale.md          # VPN service guide
│   ├── transmission.md       # BitTorrent client guide
│   └── yarr.md               # RSS reader guide
├── developers/                 # Developer resources
│   ├── index.md              # Developer overview
│   ├── homeserver.json.md    # Platform configuration
│   └── smb-development.md    # Development workflow
├── certificates/               # Certificate management
│   ├── index.md              # Certificate overview
│   ├── renewal.md            # Certificate renewal guide
│   └── troubleshooting.md    # Installation and troubleshooting
├── admin/                     # System administration
│   ├── basic-ssh-commands.md # SSH command reference
│   ├── firewall-config.md    # Firewall configuration
│   ├── network-troubleshooting.md # Network troubleshooting
│   ├── vpn-setup.md          # VPN configuration
│   ├── drive-management.md   # Drive management
│   ├── nas-config.md         # NAS configuration
│   ├── backup-strategies.md  # Backup strategies
│   ├── encryption-setup.md   # Encryption configuration
│   ├── updates-upgrades.md   # System updates
│   ├── log-analysis.md       # Log analysis
│   ├── performance-monitoring.md # Performance monitoring
│   └── disaster-recovery.md  # Disaster recovery
├── troubleshooting/            # Troubleshooting guides
│   ├── common-issues.md      # Common problems
│   ├── service-issues.md     # Service-specific problems
│   ├── network-issues.md     # Network problems
│   └── performance-issues.md # Performance problems
└── reference/                 # Reference materials
    ├── commands.md           # Command reference
    ├── config-files.md       # Configuration files
    ├── ports.md              # Port mappings
    └── file-locations.md     # File locations
```

---

## How to Contribute

### 1. Adding New Documentation
1. **Create Your Markdown File**
   - Place your new `.md` file in the appropriate `docs/` subdirectory
   - Follow existing naming conventions and structure

2. **Update Navigation**
   - Edit `mkdocs.yml` and add your file to the `nav:` section
   - Organize logically within existing categories or create new ones

3. **Submit Pull Request**
   - Fork the repository
   - Make your changes
   - Submit a pull request with clear description of changes

### 2. Documentation Standards
- **Technical Precision**: Use precise technical terminology
- **User-Centric**: Focus on what users can accomplish
- **Actionable Content**: Provide step-by-step instructions
- **Consistent Structure**: Follow established patterns and organization

### 3. Quality Guidelines
- **Accuracy**: Verify all technical information
- **Clarity**: Write for technical users who understand system administration
- **Completeness**: Include troubleshooting and edge cases
- **Maintainability**: Structure content for easy updates

---

## Building and Testing

### Local Development
```bash
# Install MkDocs and Material theme
pip install mkdocs mkdocs-material

# Serve locally for testing
mkdocs serve

# Build static site
mkdocs build
```

### Integration with HOMESERVER
- This repository is deployed as a git submodule in the main HOMESERVER repository
- Documentation is automatically built and served by the MkDocs service
- Changes are distributed to all devices through the HOMESERVER update system

---

## License

This documentation is licensed under **GPL v3.0 (GNU General Public License version 3.0)**.

**Key Points:**
- Free and open source software
- Freedom to use, study, share, and modify
- Copyleft license ensuring derivatives remain free
- Aligns with HOMESERVER's digital sovereignty mission

---

## References

- **Main Repository**: [HOMESERVER Platform](https://github.com/homeserversltd/homeserver)
- **MkDocs Documentation**: [https://www.mkdocs.org/](https://www.mkdocs.org/)
- **Material Theme**: [https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/)
- **HOMESERVER Website**: [https://arpaservers.com](https://arpaservers.com)

---

**This documentation empowers HOMESERVER customers worldwide with comprehensive, always-available guides for their digital sovereignty platform.**

## For AI butlers

This is the central documentation hub, primarily for AI butlers operating the Sovereign Three, with human readers using the illustrated guides as well. A butler reads each page through its own Caduceus at `/api/v1/docs/<page>`; the index is `/api/v1/docs/llms.txt` and `docs/llms.txt`, and the worn seal is `/api/v1/docs/seal`.

## Branches

`main` is the authoring branch. `master` is the frozen field-fleet copy and never moves. Forgejo is canonical; GitHub mirrors both branches, and GitHub's default branch stays `master` because the old updater clones the default branch and compares `VERSION`.
