# Immich

## Overview

Immich provides self-hosted photo and video backup, indexing, and browsing. It is treated as a high-storage, high-backup-priority service because it contains user-generated media and metadata that is difficult to recreate.

---

## Primary Functions

- Mobile photo and video backup
- Web-based media browsing and search
- Metadata indexing and thumbnail generation
- Shared album and family archive use cases

---

## Service Dependencies

- Traefik for ingress and TLS termination
- Authentik for SSO, enabled through OIDC
- Persistent storage for media library and database
- DNS resolution for internal and external access paths

---

## Storage Considerations

- Media storage should reside on reliable, backed-up storage
- Thumbnail/cache storage can be rebuilt but should still be monitored for capacity usage
- Database backups are critical because metadata, users, and albums are not recoverable from media files alone

---

## Security Considerations

- External publishing should require TLS and authentication
- Mobile client access should be limited to trusted identities
- Shared links should be reviewed periodically and disabled when not needed

---

## Backup Requirements

- Media library
- Database
- Environment/configuration files
- Any API keys or secrets used for notifications or integrations

---

## Recovery Notes

- Restore database and media together to preserve metadata consistency
- Validate mobile backup functionality after any restore
- Confirm reverse proxy and SSO integration before declaring service recovered

---

## Related Documentation

- [Authentik Service](authentik.md)
- [Traefik Service](traefik.md)
- [Backup Strategy](../operations/backup-strategy.md)
