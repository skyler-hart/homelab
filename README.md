# Infrastructure & Self-Hosted Engineering Lab

This repository documents my enterprise-style infrastructure lab used for developing, testing, and validating modern infrastructure, automation, identity, networking, and security engineering concepts.

## Purpose

This repository is the documentation and operations source of truth for the homelab. It captures architecture decisions, service roles, operational runbooks, and supporting diagrams so the environment can be understood, maintained, and rebuilt consistently.

## Focus Areas

- Infrastructure Engineering
- Platform Engineering
- Infrastructure Automation
- Identity & Access Management
- Networking & Security
- Observability & Monitoring
- Disaster Recovery & Resilience

## Core Technologies

**Networking & Infrastructure:**

- UniFi Networking
- Synology Storage
- Proxmox Virtualization
- Docker & Containers
- Portainer
- NetBox

**DNS & Service Publishing:**

- Pi-hole
- Unbound
- PowerDNS
- pdns-admin
- Traefik

**Identity & Access:**

- Authentik
- Active Directory
- Microsoft Entra ID

**Family & Media Services:**

- Immich
- Jellyfin
- Plex
- Mealie
- Grocy
- Homebox

**Automation & Home:**

- Home Assistant
- Syncthing
- RustDesk

**Database & Utilities:**

- MariaDB
- phpMyAdmin
- IT-Tools
- Baget

**Cloud & Collaboration:**

- Cloudflare
- GitHub
- Microsoft 365
- PowerShell

## Repository Structure

- `docs/architecture` - Core platform design, network layout, identity, DNS, and recovery architecture
- `docs/operations` - Backup, disaster recovery, monitoring, and patch management runbooks
- `docs/services` - Service-specific documentation for core self-hosted applications
- `diagrams/` - Visual architecture diagrams
- `scripts/` - Supporting automation scripts

## Documentation Index

### Architecture

- [Overview](docs/architecture/overview.md)
- [VLAN Architecture](docs/architecture/vlans.md)
- [DNS Architecture](docs/architecture/dns.md)
- [Identity Architecture](docs/architecture/identity.md)
- [Backup & Recovery Architecture](docs/architecture/backup-recovery.md)

### Operations

- [Backup Strategy](docs/operations/backup-strategy.md)
- [Disaster Recovery](docs/operations/disaster-recovery.md)
- [Monitoring](docs/operations/monitoring.md)
- [Patch Management](docs/operations/patch-management.md)

### Services

**Core Infrastructure Services:**

- [Traefik](docs/services/traefik.md)
- [Authentik](docs/services/authentik.md)
- [Pi-hole & Unbound & PowerDNS](docs/services/dns-services.md) *(see DNS Architecture for details)*
- [Proxmox](docs/services/proxmox.md) *(infrastructure virtualization)*
- [Portainer](docs/services/portainer.md) *(Docker management)*
- [NetBox](docs/services/netbox.md) *(infrastructure asset management)*
- [MariaDB](docs/services/mariadb.md) *(database backend)*

**Family & Media Services:**

- [Immich](docs/services/immich.md) *(photos and videos)*
- [Jellyfin](docs/services/jellyfin.md) *(media streaming)*
- [Plex](docs/services/plex.md) *(media streaming)*
- [Mealie](docs/services/mealie.md) *(recipe management)*
- [Grocy](docs/services/grocy.md) *(inventory management)*
- [Homebox](docs/services/homebox.md) *(personal inventory)*

**Automation & Utilities:**

- [Home Assistant](docs/services/home-assistant.md)
- [Syncthing](docs/services/syncthing.md) *(file synchronization)*
- [RustDesk](docs/services/rustdesk.md) *(remote access)*
- [IT-Tools](docs/services/ittools.md)
- [Baget](docs/services/baget.md) *(NuGet server)*

## Current Architecture

The current environment is built around these core design patterns:

- Segmented VLAN-based networking with controlled inter-VLAN access
- Pi-hole as the client-facing DNS layer, Unbound for recursive resolution, and PowerDNS as the internal authoritative DNS service
- Traefik as the centralized ingress and reverse proxy layer
- Authentik as the central SSO and access-control layer for self-hosted services
- Synology-backed local backup with offsite replication for disaster recovery

## Diagrams

- [Network Overview Diagram](diagrams/network-overview.drawio)

## Contact

Recommendations and general comments are welcome via GitHub Issues.

- Open an issue for feedback, suggestions, and non-security discussions
- Report vulnerabilities using GitHub Private Vulnerability Reporting
- Do not post sensitive security details in public issues

## Contributions

This is a private homelab repository and external contributions are not accepted.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Notes

- Some sections describe target-state architecture in addition to current-state implementation details
- Secrets policy: credentials, API keys, tokens, certificates, and sensitive configuration values must be stored in the DevOps Vault in 1Password (not in this repository)
