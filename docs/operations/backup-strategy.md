# Backup Strategy

## Objectives

- Protect all critical configuration and application data
- Minimize recovery time following any failure
- Ensure at least one offsite copy of all critical data exists
- Support full environment rebuild from a cold state within 4 hours

---

## Backup Model

This environment follows the **3-2-1 rule**:

- **3** copies of data
- **2** different storage media
- **1** copy offsite

| Copy | Location | Medium |
| ---- | -------- | ------ |
| 1 | Production (live volumes) | Docker host disk |
| 2 | Synology RS1619xs+ (local NAS) | RAID array |
| 3 | Cloud (S3-compatible offsite) | Object storage |

---

## Data Categories

| Category | Location | Backup Method |
| -------- | -------- | ------------- |
| Infrastructure Configurations | Git repo, NAS | GitHub + Hyper Backup |
| Docker Compose Files | Git repo | GitHub |
| Application Data (Immich, Nextcloud, Authentik) | Docker volumes | Hyper Backup |
| Server OS Configurations | Each host | Scripted export to NAS |
| DNS Records | Pi-hole, Unbound, PowerDNS | Config backup to NAS |
| UniFi Network Config | UDM Pro | Automated backup to NAS |
| Documentation | Git repo | GitHub |

---

## Backup Schedule

| Job | Type | Frequency | Time | Retention |
| --- | ---- | --------- | ---- | --------- |
| Docker volumes | Incremental | Daily | 02:00 | 30 days |
| Application data | Full | Weekly | Sunday 03:00 | 12 weeks |
| Server OS config export | Full | Weekly | Sunday 02:00 | 8 weeks |
| DNS / UniFi config | Full | Daily | 01:00 | 30 days |
| Offsite cloud sync | Sync | Daily | 05:00 | 90 days |

---

## Backup Platform: Synology RS1619xs+

- **Hyper Backup**: Application data, Docker volumes, and configuration archives
- **Cloud Sync / Hyper Backup Vault**: Offsite replication to S3-compatible storage
- Backups stored on a dedicated Synology shared folder with restricted access

---

## Verification

- Monthly restore test performed on a non-production host
- Backup job health reviewed after each scheduled run
- Any failed jobs trigger a manual review and retry
- Restore tests documented in operations log

---

## Recovery Objectives

| Metric | Target |
| ------ | ------ |
| RTO (critical services) | < 4 hours |
| RPO | < 24 hours |

---

## Related Documentation

- [Backup & Recovery Architecture](../architecture/backup-recovery.md)
- [Disaster Recovery](disaster-recovery.md)
