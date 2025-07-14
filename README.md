# MkDocs Documentation Contribution Guide

## Overview
This documentation site is powered by [MkDocs](https://www.mkdocs.org/) with the Material theme. It is designed as a living, user-centric documentation hub for HomeServer customers worldwide. Every device automatically downloads the latest documentation on update, ensuring users always have local, up-to-date guides for their system—no internet required after sync.

---

## Mental Models & Philosophy

### 1. User-Centric, Practical Documentation
- **Focus on the End User:**
  - Every guide is written for real people using the device, not just system administrators.
  - Service docs (e.g., Jellyfin, Navidrome) emphasize what users can do, how to access features, and practical workflows.
- **Actionable, Not Just Reference:**
  - Documentation is structured to help users accomplish tasks, solve problems, and get the most from their HomeServer.

### 2. Always Up-to-Date, Locally Available
- **Automatic Updates:**
  - Documentation is bundled and updated with every HomeServer software release.
  - Users always have the latest docs, even offline.
- **Global Accessibility:**
  - Designed for a worldwide audience—clear, concise, and accessible language.

### 3. Extensible & Collaborative
- **Easy Contribution:**
  - Anyone can add or improve docs by editing Markdown files and updating navigation.
  - No rebuild scripts or complex workflows required.
- **Infinite Extensibility:**
  - Add as many Markdown files as needed; organize with categories or flat lists.

### 4. Consistency & Discoverability
- **Navigation-Driven:**
  - All docs are discoverable via the sidebar and search.
  - Consistent structure across service guides for ease of use.

---

## How to Add New Documentation Pages

1. **Create Your Markdown File**
   - Place your new `.md` file in the `docs/` directory (e.g., `docs/vaultwarden.md`).
   - Example: `docs/my_new_service.md`

2. **Link the File in the Navigation**
   - Edit `mkdocs.yml` and add your new file to the `nav:` section.
   - You can nest files under categories or add them at the top level.
   - Example:
     ```yaml
     nav:
       - Home: index.md
       - Services:
           - Vaultwarden: vaultwarden.md
           - My New Service: my_new_service.md
     ```

3. **Update the Index (Optional)**
   - You may also want to mention your new page in `index.md` for discoverability.
   - Example:
     ```markdown
     - My New Service (see sidebar)
     ```

4. **No Manual Rebuild Needed**
   - The MkDocs service watches for changes and auto-rebuilds the site.
   - Your new page will appear in the sidebar navigation immediately after saving changes.

---

## Infinite Extensibility
- You can keep adding as many Markdown files as you want to the `docs/` directory.
- Just link them in `mkdocs.yml` under `nav:` to make them appear in the navigation.
- Organize with categories, subcategories, or flat lists as needed.

---

## References
- [index.md](docs/index.md): The homepage/landing page for the documentation site.
- [mkdocs.yml](mkdocs.yml): The configuration file that controls navigation and site settings.
- [MkDocs Documentation](https://www.mkdocs.org/)
- [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/)

---

**Summary:**
- Add Markdown files to `docs/`.
- Link them in `mkdocs.yml` under `nav:`.
- Optionally mention them in `index.md`.
- MkDocs will auto-update—no manual build required.
- All users always have the latest, locally available documentation for their device.
