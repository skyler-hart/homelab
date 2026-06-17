# Disaster Recovery

## Overview

This runbook defines the process for recovering the environment following a partial or complete failure. It covers individual service recovery, host recovery, and full environment rebuild scenarios.

---

## Recovery Objectives

| Metric | Target |
| ------ | ------ |
| Recovery Time Objective (RTO) | < 4 hours for critical services |
| Recovery Point Objective (RPO) | < 24 hours |

---

## Failure Scenarios

| Scenario | Severity | Recovery Path |
| -------- | -------- | ------------- |
| Single service failure | Low | Restart container / redeploy Compose service |
| Docker host failure | Medium | Rebuild host, restore volumes from NAS |
| NAS failure | High | Restore from offsite cloud backup to replacement |
| Network failure (UDM Pro) | High | Restore UniFi config backup to replacement unit |
| Full environment loss | Critical | Full rebuild from repo + offsite backup |

---

## Recovery Procedures

### 1. Single Service Recovery

```bash
# Restart a specific service
docker compose -f /path/to/docker-compose.yml restart <service>

# Redeploy a specific service
docker compose -f /path/to/docker-compose.yml up -d <service>
```

1. Check container logs for root cause before restarting
2. If data corruption is suspected, restore the service volume from the most recent NAS backup before redeploying
3. Confirm service is healthy and integrated with Traefik and Authentik

---

### 2. Docker Host Recovery

1. Provision a new Linux host (or restore from snapshot if virtualized)
2. Install Docker and Docker Compose
3. Clone the infrastructure repository from GitHub
4. Restore Docker volumes from the Synology NAS backup
5. Deploy services with Docker Compose
6. Verify DNS records point to the new host if the IP changed
7. Confirm Traefik routing and Authentik authentication are functioning

---

### 3. Network (UDM Pro) Recovery

1. Perform factory reset or replace hardware
2. Restore latest UniFi configuration backup from NAS
3. Verify VLAN assignments, firewall rules, and DHCP reservations
4. Confirm DNS servers are reachable per VLAN
5. Validate inter-VLAN firewall policy

---

### 4. NAS Recovery

1. Replace or rebuild the Synology unit
2. Restore data from offsite cloud backup using Hyper Backup
3. Reconfigure shared folders and permissions
4. Resume backup schedules
5. Verify Docker hosts can reach NAS shares

---

### 5. Full Environment Rebuild

For complete loss of all on-premises infrastructure:

1. **Networking**: Restore UDM Pro from backup or reconfigure from documentation
2. **Storage**: Provision new NAS, restore from offsite backup
3. **DNS**: Redeploy Pi-hole, Unbound, and PowerDNS; restore configs and internal zones from backup
4. **Identity**: Restore Authentik DB from backup; AD/Entra recovery per Microsoft DR docs
5. **Services**: Pull infrastructure repo, restore volumes, deploy all Compose stacks
6. **Verification**: Walk through service health checklist below

---

## Post-Recovery Health Checklist

- [ ] DNS resolves internal hostnames correctly
- [ ] Traefik is routing requests to all services
- [ ] Authentik SSO login works
- [ ] Immich, Nextcloud, and other services accessible
- [ ] Home Assistant automations active
- [ ] Monitoring/alerting active
- [ ] Backup jobs re-enabled and scheduled
- [ ] Firewall rules verified per VLAN design

---

## Related Documentation

- [Backup Strategy](backup-strategy.md)
- [Backup & Recovery Architecture](../architecture/backup-recovery.md)
- [VLAN Architecture](../architecture/vlans.md)
