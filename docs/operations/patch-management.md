# Patch Management

## Overview

Patching covers the operating systems, Docker host software, container images, self-hosted application packages, and supporting infrastructure. The goal is to keep all components current on security patches while avoiding unplanned disruptions.

---

## Scope

| Component | Platform | Update Method |
| --------- | -------- | ------------- |
| Linux hosts (OS) | Ubuntu/Debian | `apt upgrade` |
| Docker Engine | All hosts | `apt upgrade docker-ce` |
| Container images | All services | Pull latest, redeploy via Compose |
| Synology DSM | Synology RS1619xs+ | DSM Update Center |
| UniFi firmware | UDM Pro, switches, APs | UniFi Network controller |
| Pi-hole / Unbound / PowerDNS | Docker containers or VMs | Image or package update + redeploy |
| Microsoft 365 / Entra | Cloud | Managed by Microsoft (auto) |
| Windows hosts | Domain-joined | Windows Update / WSUS |

---

## Patch Schedule

| Cadence | Scope |
| ------- | ----- |
| Monthly | Linux OS security patches, Docker host updates |
| Monthly | Container image updates for all self-hosted services |
| Monthly | Synology DSM and package updates |
| As released | Critical / zero-day security patches (applied within 48 hours) |
| Quarterly | Full environment review and dependency audit |

---

## Process

### Linux Host Patching

```bash
sudo apt update && sudo apt upgrade -y
sudo apt autoremove -y
# Reboot if kernel update applied
sudo reboot
```

### Container Image Updates

```bash
# Pull latest images
docker compose pull

# Redeploy updated containers
docker compose up -d

# Remove unused images
docker image prune -f
```

### Synology DSM

1. Log in to Synology DSM
2. Navigate to **Control Panel > Update & Restore**
3. Review available updates and release notes
4. Schedule or apply update during a maintenance window

### UniFi

1. Log in to UniFi Network controller
2. Navigate to **System > Firmware Updates**
3. Review available updates for UDM Pro, switches, and APs
4. Stage updates during low-traffic period

---

## Pre-Patch Checklist

- [ ] Backup current configuration (NAS + offsite sync verified)
- [ ] Review release notes for breaking changes
- [ ] Notify users of planned maintenance window if applicable
- [ ] Confirm monitoring is active before and after patch
- [ ] Verify any required credentials, API keys, tokens, and certificates are available in 1Password DevOps Vault

## Post-Patch Checklist

- [ ] Verify all services are running and accessible
- [ ] Confirm DNS, Traefik routing, and Authentik SSO are functional
- [ ] Check logs for errors following service restarts
- [ ] Update patch log with date, components patched, and any issues
- [ ] Rotate or update secrets in 1Password DevOps Vault if changed during maintenance

---

## Emergency Patching

For critical CVEs or zero-day vulnerabilities:

1. Assess exposure and severity
2. Apply patch within 48 hours of vendor availability
3. Document the vulnerability, patch applied, and any residual risk
4. Verify environment stability post-patch

---

## Related Documentation

- [Backup Strategy](backup-strategy.md)
- [Disaster Recovery](disaster-recovery.md)
- [Architecture Overview](../architecture/overview.md)
