# Grocy

## Overview

Grocy is a web-based household management application focused on tracking consumable items: groceries, pantry items, food expiration dates, and meal planning.

---

## Primary Functions

- Consumable inventory tracking (groceries, pantry items, household consumables)
- Expiration date tracking and alerts
- Shopping list generation
- Barcode scanning for quick item entry

---

## Consumable Inventory Management

- Product database with barcodes for quick entry
- Quantity tracking per storage location (pantry, fridge, freezer, etc.)
- Purchase history and consumption tracking
- Expiration alerts and automated removal of expired items
- Shopping list generation based on low stock items
- Integration with meal planning for automatic shopping list updates

---

## Features

- Barcode scanning support
- Recurring household tasks
- Chore assignments
- Recipes integration
- Multi-user household access

---

## Integration

- MariaDB backend for inventory data
- Traefik for web publishing
- Authentik for family SSO
- Barcode scanner support (hardware and mobile app)

---

## Backup Requirements

- Inventory database
- Product database and barcodes
- Configuration and user data

---

## Related Documentation

- [Traefik Service](traefik.md)
- [Authentik Service](authentik.md)
- [MariaDB Service](mariadb.md)
- [Backup Strategy](../operations/backup-strategy.md)
