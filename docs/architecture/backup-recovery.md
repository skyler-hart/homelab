# Backup & Recovery Architecture

## Overview

The backup strategy follows a 3-2-1 model: three copies of data, on two different media types, with one copy offsite. Synology provides the primary backup platform, with cloud offsite replication as the secondary tier.

---

## Backup Architecture Diagram

```text
[Services / Docker Hosts]
        │
        ▼
[Synology RS1619xs+] ──── Local NAS Backup (Primary)
        │
        ▼
[Cloud Storage] ────────── Offsite Backup (Secondary)
```

---

## Backup Tiers

| Tier | Platform | Method | Retention |
| ---- | -------- | ------ | --------- |
| Primary | Synology RS1619xs+ | Hyper Backup / rsync | 30 days |
| Offsite | Cloud Storage (S3-compatible) | Synology Hyper Backup Vault | 90 days |

---

## Data Categories and Backup Scope

| Category | Examples | Backed Up | Priority |
| -------- | -------- | --------- | -------- |
| Infrastructure Configurations | UniFi config, VLAN rules, firewall policies | Yes | Critical |
| Docker Compose Files | All service definitions in repo | Yes (Git + NAS) | Critical |
| Application Data | Immich media, Nextcloud files, Authentik DB | Yes | High |
| Server Configurations | OS config, cron jobs, environment files | Yes | High |
| Documentation | This repository | Yes (GitHub) | High |
| Log Data | System and application logs | No | Low |

---

## Recovery Objectives

| Metric | Target |
| ------ | ------ |
| Recovery Time Objective (RTO) | < 4 hours for critical services |
| Recovery Point Objective (RPO) | < 24 hours |

---

## Backup Schedule

| Job | Frequency | Window |
| --- | --------- | ------ |
| Docker volume snapshot | Daily | 02:00 |
| Application data backup | Daily | 03:00 |
| Full system configuration backup | Weekly | Sunday 04:00 |
| Offsite cloud sync | Daily | 05:00 |
| Backup verification | Monthly | First Sunday |

---

## Recovery Procedures

Detailed recovery procedures are documented in the [Disaster Recovery](../operations/disaster-recovery.md) runbook.

### High-Level Recovery Steps

1. Identify the failure scope (single service, host, or full environment)
2. Locate most recent clean backup for affected data
3. Restore to new or recovered host
4. Re-deploy Docker services using Compose files from repository
5. Restore application data volumes from backup
6. Validate service health and integration (DNS, auth, reverse proxy)
7. Update documentation and post-mortem as appropriate

---

## Related Documentation

- [Backup Strategy](../operations/backup-strategy.md)
- [Disaster Recovery](../operations/disaster-recovery.md)
- [Architecture Overview](overview.md)
