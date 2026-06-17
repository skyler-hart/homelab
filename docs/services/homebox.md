# Homebox

## Overview

Homebox is a personal inventory management system for organizing and tracking household items, possessions, and assets with a focus on knowing what you own and where it is.

---

## Primary Functions

- Non-consumable equipment and tool inventory tracking
- Item categorization and organization
- Photos, serial numbers, and documentation storage
- Location and storage area management (workshop, garage, storage boxes, etc.)
- Asset search and discovery by category or location

---

## Use Cases

- Tool and equipment inventory (workshop, garage, storage)
- Cable and networking hardware tracking and organization
- Home insurance documentation and asset value tracking
- Warranty and receipt storage
- Spring cleaning and decluttering
- Asset location and availability search

---

## Features

- Item database with photos
- Categorization and tagging
- Location tracking (rooms, storage boxes, etc.)
- Custom fields and attributes
- Import and export capabilities

---

## Integration

- Web interface for access
- Traefik for reverse proxy publishing
- Authentik for family member authentication
- Database backend (MariaDB)

---

## Backup Requirements

- Item database and metadata
- Uploaded photos and documents
- User accounts and preferences

---

## Related Documentation

- [Traefik Service](traefik.md)
- [Authentik Service](authentik.md)
- [Backup Strategy](../operations/backup-strategy.md)
