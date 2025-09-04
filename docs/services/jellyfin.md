# Jellyfin Media Server Guide

## Quick Access

### Local Network Access
- **Web Interface**: [https://jellyfin.home.arpa](https://jellyfin.home.arpa)
- **Direct IP Access**: [https://jellyfin.home.arpa](https://jellyfin.home.arpa)

### Remote Access (via Tailscale)
- **Remote URL**: [https://home.{YourTailnetNameHere}.ts.net/jellyfin/](https://home.{YourTailnetNameHere}.ts.net/jellyfin/)

---

## Overview

**Jellyfin** is your personal, open-source media server for movies, TV shows, and music. With Jellyfin, you can stream your media collection to any device, create user profiles, manage libraries, and enjoy a rich, modern interface—all hosted securely on your HomeServer.

---

## 1. Accessing Jellyfin

- **Web Interface:**
  - Open [https://jellyfin.home.arpa](https://jellyfin.home.arpa) in your browser.
- **Remote Access:**
  - Use [https://home.{YourTailnetNameHere}.ts.net/jellyfin/](https://home.{YourTailnetNameHere}.ts.net/jellyfin/) when connected via Tailscale.
- **Portal Shortcut:**
  - Find Jellyfin in your HomeServer portal under "Media" or "Jellyfin".

---

## 2. What Can You Do With Jellyfin?

- **Watch Movies & TV Shows:**
  - Stream your collection in high quality, with support for subtitles, multiple audio tracks, and rich metadata.
- **Listen to Music:**
  - Enjoy your music library with playlists, album art, and artist info.
- **User Profiles:**
  - Each family member can have their own profile, watch history, and recommendations.
- **Transcoding:**
  - Jellyfin automatically adapts video/audio quality to your device and network.
- **Remote Streaming:**
  - Access your media from anywhere via secure HomeServer integration and Tailscale.
- **Parental Controls:**
  - Restrict content by user profile.

---

## 3. Using the Jellyfin Web App

- **Browse Libraries:**
  - Navigate by Movies, TV Shows, Music, or custom collections.
- **Search:**
  - Use the search bar to quickly find any title, artist, or episode.
- **Play Media:**
  - Click any item to start playback. Use the player controls for subtitles, audio tracks, and quality settings.
- **Create Playlists:**
  - Add movies, episodes, or songs to your own playlists.
- **Continue Watching:**
  - Resume unfinished shows or movies from your dashboard.
- **User Settings:**
  - Change your profile picture, language, or playback preferences in the user menu.

---

## 4. Mobile & TV Apps

Jellyfin supports a wide range of official and third-party apps:

- **Android/iOS:**
  - [Jellyfin Mobile](https://jellyfin.org/docs/general/clients/mobile/) (official)
  - [Finamp](https://github.com/jmshrv/finamp) (music)
- **Smart TVs & Streaming Devices:**
  - [Jellyfin for Android TV](https://play.google.com/store/apps/details?id=org.jellyfin.androidtv)
  - [Jellyfin for Roku](https://channelstore.roku.com/details/592369/jellyfin)
  - [Jellyfin for Fire TV](https://www.amazon.com/Jellyfin-Team/dp/B07T8ZDTTP)
- **Desktop:**
  - [Jellyfin Desktop](https://github.com/jellyfin/jellyfin-media-player)
  - Web browser (full experience)

**To connect a client:**
- Set the server URL to `https://jellyfin.home.arpa`
- Log in with your user credentials (provided by your admin or set in the web UI)

---

## 5. Organizing Your Media Library

- **Expected Folder Structure:**
  - For best results, organize your media as follows (see also [jellyfinDoc.md](../../../docs/jellyfinDoc.md)):

    ```
    /TV Shows/
    └── Show Name (Year)/
        ├── Season 01/
        │   ├── Show Name (Year) - S01E01.mkv
        │   ├── Show Name (Year) - S01E02.mkv
        │   └── ...
        ├── Season 02/
        │   └── Show Name (Year) - S02E01.mkv
        └── ...
    /Movies/
    └── Movie Name (Year).mkv
    /Music/
    └── Artist/
        └── Album/
            └── Track 01.flac
    ```
- **Adding Media:**
  - Upload files via the HomeServer file manager or place them in `/mnt/nas/media`.
  - Jellyfin will automatically scan and index new files.
- **Metadata:**
  - Jellyfin fetches artwork, descriptions, and episode info automatically. You can edit metadata in the web UI if needed.

---

## 6. Integration with HomeServer

- **Portal Integration:**
  - Jellyfin is available as a portal in your HomeServer dashboard for one-click access.
- **Permissions:**
  - Access to the media library is managed by HomeServer. Only authorized users can upload or modify files.
- **homeserver.json:**
  - Jellyfin's configuration and permissions are defined in the `homeserver.json` file, ensuring seamless integration and access control. (See [Platform Configuration](homeserver.json.md))

---

## 7. Troubleshooting

- **Can't log in?**
  - Contact your system administrator for account help.
- **Media not showing up?**
  - Make sure files are in `/mnt/nas/media` and follow the recommended folder structure. Wait a few minutes for scanning.
- **Playback issues?**
  - Try a different browser or app, or check the [Jellyfin FAQ](https://jellyfin.org/docs/general/faq/).

---

## 8. Advanced Features & Documentation

- **Official Documentation:**
  - [Jellyfin Documentation](https://jellyfin.org/docs/)
- **Supported Clients:**
  - [List of official and third-party apps](https://jellyfin.org/docs/general/clients/overview/)
- **Plugins:**
  - Extend Jellyfin with [plugins](https://jellyfin.org/docs/general/server/plugins/).

---

## 9. Credits & Attribution

**Jellyfin** is an open-source project created and maintained by the Jellyfin community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

- **Original Project**: [Jellyfin on GitHub](https://github.com/jellyfin/jellyfin)
- **Maintainer**: [jellyfin](https://github.com/jellyfin)
- **License**: GPL v2
- **Documentation**: [Jellyfin Documentation](https://jellyfin.org/docs)

This HomeServer integration builds upon the excellent foundation provided by the Jellyfin project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Enjoy your movies, shows, and music—anywhere, anytime!** 