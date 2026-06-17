# Mealie

## Overview

Mealie is a self-hosted recipe management and meal planning application designed for families to organize recipes, plan meals, and share cooking information.

---

## Primary Functions

- Recipe collection, organization, and management
- Meal planning and weekly schedule creation
- Recipe import from popular food websites
- Family recipe sharing and collaboration
- Nutritional information and ingredient tracking

---

## User Features

- Recipe import from popular food websites
- Ingredient database and recipe notes
- Weekly meal planning and scheduling
- Shared family recipe accounts
- Mobile-friendly recipe browser and meal planning interface
- Recipe scaling and serving size adjustment

---

## Integration

- MariaDB backend for recipe and plan data
- Traefik for reverse proxy publishing
- Authentik for family member SSO
- Backup of recipe database and uploads

---

## Data Backup

- Recipe database backups critical
- User-uploaded images and documents
- Configuration and user accounts
- Restore procedures in [Disaster Recovery](../operations/disaster-recovery.md)

---

## Related Documentation

- [Traefik Service](traefik.md)
- [Authentik Service](authentik.md)
- [MariaDB Service](mariadb.md)
- [Backup Strategy](../operations/backup-strategy.md)
