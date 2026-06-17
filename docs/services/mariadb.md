# MariaDB

## Overview

MariaDB is the database backend for multiple services in the lab, providing reliable relational data storage for application data and configuration.

---

## Primary Functions

- Database backend for Authentik, Mealie, Grocy, NetBox, and other services
- User and privilege management
- Backup and replication support
- Query optimization and monitoring

---

## Services Using MariaDB

- Authentik (database, optional)
- Mealie (recipes and meal plans)
- Grocy (inventory management)
- NetBox (infrastructure data)
- Other custom or third-party applications

---

## Backup & Recovery

- Included in Synology backup strategy
- Regular snapshots of databases
- Point-in-time recovery support (via binlogs if enabled)
- Restore procedures documented in [Disaster Recovery](../operations/disaster-recovery.md)

---

## Performance & Monitoring

- Resource monitoring via Prometheus and Grafana
- Query logging for troubleshooting
- Replication status (if applicable)
- Backup job status tracking

---

## Related Documentation

- [Backup Strategy](../operations/backup-strategy.md)
- [Disaster Recovery](../operations/disaster-recovery.md)
- [Monitoring](../operations/monitoring.md)
