# HomeServer Platform Configuration (`homeserver.json`)

## Overview

The `homeserver.json` file is the central configuration for the HomeServer platform. It defines UI tabs, service portals, upload settings, admin controls, mount points, permissions, and global system options. This document explains the structure, key fields, and best practices for managing your HomeServer configuration.

---

## 1. File Location

- **Path:** `initialization/flask/inject/src/config/homeserver.json`
- **Managed by:** System administrators (manual edit or via admin UI, if available)

---

## 2. Simplicity & Extensibility: Adding New Services

### Effortless Service Integration
- **Uniform Entry:**
  - Adding a new service is as simple as adding a new entry to the `portals` array in `homeserver.json`.
  - Each service is described with a few key fields (name, description, type, port, URLs, etc.).
- **Automatic Monitoring:**
  - Once added, the service is automatically monitored and managed by the HomeServer interface.
  - Health, status, and activity indicators are linked through the indicators backend and surfaced in the UI.
- **Cross-Referential Access:**
  - Services are accessible from multiple points: the Portals tab, system indicators, and direct links.
  - The architecture ensures that every new service is discoverable and manageable in a consistent way.
- **No Code Required:**
  - Most additions require only a simple JSON edit—no backend/frontend code changes needed for basic integration.

### Example: Adding a New Portal
To add a new service portal (e.g., for a new app):
1. Add a new entry to `tabs.portals.data.portals`:
   ```json
   {
     "name": "NewApp",
     "description": "Description",
     "services": ["newapp"],
     "type": "systemd",
     "port": 1234,
     "localURL": "https://newapp.home.arpa",
     "remoteURL": "https://server.tail13aff.ts.net/newapp/"
   }
   ```
2. Adjust visibility in `tabs.portals.visibility.elements` if needed.
3. Optionally, add monitoring hooks in the indicators backend for advanced status reporting.

---

## 3. Structure & Key Sections

### `tabs`
Defines all UI tabs, their configuration, visibility, and data. Example:
```json
"tabs": {
  "stats": {
    "config": { "displayName": "Stats", "adminOnly": false, ... },
    "visibility": { "tab": true, "elements": { ... } },
    "data": { ... }
  },
  ...
}
```
- **config:** Display name, admin-only flag, order, enable/disable
- **visibility:** Controls which tabs/elements are visible
- **data:** Tab-specific data (e.g., network notes, portal lists)

### `global`
System-wide settings and metadata. Example:
```json
"global": {
  "version": { "generation": 1, "buildId": "20250401-a", ... },
  "theme": { "name": "dark" },
  "admin": { "pin": "1" },
  ...
}
```
- **version:** Build and update info
- **theme:** Default UI theme
- **admin:** Admin PIN (do not share)
- **cors:** Allowed origins for API access
- **mounts:** Disk and NAS mount points
- **permissions:** Directory and service access controls

### `mounts`
Defines all storage mount points:
```json
"mounts": {
  "vault": { "device": "sda4", "mountPoint": "/vault", ... },
  ...
}
```
- **device:** Block device name
- **mountPoint:** Filesystem path
- **encrypted:** Whether the mount is encrypted

### `permissions`
Controls which users/services can access which paths:
```json
"permissions": {
  "nas": {
    "basePath": "/mnt/nas",
    "applications": {
      "Jellyfin": { "user": "jellyfin", ... },
      ...
    },
    "includedPermissions": { "user": ["www-data", "admin"], ... }
  }
}
```
- **applications:** Per-service access rules
- **includedPermissions:** Extra users/groups with access

---

## 4. Indicators & Portals: Unified Monitoring and Access

- **Indicators Backend:**
  - The indicators system (see `backend/indicators/`) automatically monitors service health, status, and activity.
  - New services added to `homeserver.json` can be linked to indicators for real-time monitoring and alerting.
- **Portals Frontend:**
  - The portals UI (see `src/tablets/portals/`) provides a unified, discoverable entry point for all services.
  - Every portal entry is cross-referenced with indicators, so users see live status and can access services with one click.
- **Multidimensional Monitoring:**
  - Services are tracked across multiple dimensions: availability, health, usage, and more.
  - The HomeServer interface brings together all relevant data for each service in a single, user-friendly dashboard.

---

## 5. Admin Notes & Best Practices
- **Backup before editing:** Always keep a backup of `homeserver.json`.
- **Validate JSON:** Use a linter or the admin UI to check for syntax errors.
- **Sensitive data:** Do not store secrets or passwords here (except admin PIN if required).
- **Mounts & permissions:** Ensure all mount points and permissions match your actual filesystem and service users.
- **Tab order:** Use the `order` field to control tab arrangement in the UI.
- **Visibility:** Use `adminOnly` and `visibility` to restrict sensitive tabs/elements.

---

## 6. References
- [Example homeserver.json](https://github.com/yourrepo/homeserver/blob/main/initialization/flask/inject/src/config/homeserver.json)
- [Platform README](../README.md)
- [Admin UI Documentation](admin-ui.md) *(if available)*

---

**Adding and monitoring new services is simple, uniform, and powerful—just update `homeserver.json` and let HomeServer do the rest!** 