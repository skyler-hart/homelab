# Jellyfin

## Overview

Jellyfin is a free, open-source media system that allows you to organize and stream your personal media collection (music, movies, TV shows, photos) to any device.

---

## Primary Functions

- Media library organization and indexing
- Transcoding for compatibility across devices
- Streaming to multiple clients
- User and access management
- Metadata fetching and organization

---

## Media Types

- Movies
- TV Shows
- Music
- Photos
- Mixed media libraries

---

## Clients & Playback

- Web player
- Mobile apps (iOS, Android)
- Desktop clients
- Smart TV apps
- Generic DLNA/UPnP support

---

## Integration

- Database backend (SQLite or MariaDB)
- Library storage on Synology NAS or Docker volumes
- Optional: Published through Traefik with Authentik SSO
- Backup included in Synology backup strategy

---

## Related Documentation

- [Traefik Service](traefik.md)
- [Authentik Service](authentik.md)
- [Backup Strategy](../operations/backup-strategy.md)
