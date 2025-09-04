# Navidrome Music Server Guide

## Quick Access

### Local Network Access
- **Web Interface**: [https://music.home.arpa](https://music.home.arpa)
- **Direct IP Access**: [https://music.home.arpa](https://music.home.arpa)

### Remote Access (via Tailscale)
- **Remote URL**: [https://home.{YourTailnetNameHere}.ts.net/music/](https://home.{YourTailnetNameHere}.ts.net/music/)

---

## Overview

**Navidrome** is your personal, open-source music streaming server. It provides a modern web interface and supports a wide range of music player apps, letting you enjoy your music collection from any device, anywhere. Navidrome is fully integrated into your HomeServer suite—no manual setup required.

---

## 1. Accessing Navidrome

- **Web Interface:**
  - Open [https://music.home.arpa](https://music.home.arpa) in your browser.
- **Remote Access:**
  - Use [https://home.{YourTailnetNameHere}.ts.net/music/](https://home.{YourTailnetNameHere}.ts.net/music/) when connected via Tailscale.
- **Portal Shortcut:**
  - Find Navidrome in your HomeServer portal under "Music".

---

## 2. Using Navidrome

- **Browse & Play:**
  - Use the web interface to browse artists, albums, genres, or search your collection. Click any track to play instantly.
- **Playlists:**
  - Create and manage playlists directly in the web UI.
- **Queue & Shuffle:**
  - Add songs to your queue, shuffle albums or playlists, and enjoy gapless playback.
- **Favorites:**
  - Mark songs, albums, or artists as favorites for quick access.

---

## 3. Mobile & Desktop Apps

Navidrome supports the [Subsonic API](https://www.navidrome.org/docs/usage/clients/), so you can use many popular music player apps:

- **Android:**
  - [Substreamer](https://substreamerapp.com/)
  - [Ultrasonic](https://github.com/ultrasonic/ultrasonic)
  - [Symfonium](https://symfonium.app/)
  - [DSub](https://github.com/danieloeh/DSub)
- **iOS:**
  - [Substreamer](https://substreamerapp.com/)
  - [iSub](https://isubapp.com/)
- **Desktop:**
  - [Aurial](https://github.com/kraxarn/aurial) (macOS)
  - [Jamstash](https://jamstash.com/) (web)

**To connect a client:**
- Set the server URL to `https://music.home.arpa`
- Use your Navidrome username and password (provided by your admin or set in the web UI)

---

## 4. Music Library

- **Location:**
  - All music is stored in `/mnt/nas/music` and automatically indexed by Navidrome.
- **Adding Music:**
  - Upload new music via the HomeServer file manager or by placing files in `/mnt/nas/music`. Navidrome will detect new files automatically (usually within a few minutes).
- **Supported Formats:**
  - MP3, FLAC, AAC, OGG, OPUS, and more. See [Navidrome Supported Formats](https://www.navidrome.org/docs/usage/file-formats/) for details.

---

## 5. Integration with HomeServer

- **Portal Integration:**
  - Navidrome appears in your HomeServer portal as "Music" with a direct link.
- **Permissions:**
  - Access to the music library is managed by HomeServer. Only authorized users can upload or modify music files.
- **homeserver.json:**
  - Navidrome's configuration and permissions are defined in the `homeserver.json` file, ensuring seamless integration and access control. (See [Platform Configuration](homeserver.json.md))

---

## 6. Troubleshooting

- **Can't log in?**
  - Contact your system administrator for account help.
- **Music not showing up?**
  - Make sure files are in `/mnt/nas/music` and wait a few minutes for indexing.
- **Playback issues?**
  - Try a different browser or client app, or check the [Navidrome FAQ](https://www.navidrome.org/docs/faq/).

---

## 7. Advanced Features & Documentation

- **Official Documentation:**
  - [Navidrome Documentation](https://www.navidrome.org/docs/)
- **Supported Clients:**
  - [List of compatible apps](https://www.navidrome.org/docs/usage/clients/)
- **API:**
  - Navidrome supports the [Subsonic API](https://www.navidrome.org/docs/usage/api/), enabling integration with many third-party apps.

---

## 8. Credits & Attribution

**Navidrome** is an open-source project created and maintained by the Navidrome community. We extend our sincere gratitude to the original authors and contributors for their excellent work.

- **Original Project**: [Navidrome on GitHub](https://github.com/navidrome/navidrome)
- **Maintainer**: [navidrome](https://github.com/navidrome)
- **License**: GPL v3
- **Documentation**: [Navidrome Documentation](https://www.navidrome.org/docs/)

This HomeServer integration builds upon the excellent foundation provided by the Navidrome project, adapting it for seamless integration with our platform while maintaining full compatibility with the original software.

---

**Enjoy your music, anywhere!**
