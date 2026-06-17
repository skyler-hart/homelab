# DNS Architecture

## Overview

Internal DNS is split across multiple roles to serve both on-premises Active Directory and internal services:

- **Active Directory DNS** handles lab/business AD domain services (SRV records, dynamic updates, replication)
- **Pi-hole** is the primary DNS endpoint that clients use for filtering and query routing
- **Unbound** performs recursive resolution and hosts local/manual entries
- **PowerDNS** acts as the authoritative name server for internal and split-horizon zones

Client queries flow from Pi-hole through Unbound, which conditionally forwards AD domain queries to Active Directory DNS, authoritative queries for family/lab services to PowerDNS, and resolves everything else recursively.

---

## DNS Infrastructure

| Role | Platform | Location |
| ---- | -------- | -------- |
| AD Domain Services | Active Directory DNS | On-premises AD environment |
| Client-Facing DNS / Filtering | Pi-hole | Server VLAN |
| Recursive Resolver / Local Overrides | Unbound | Server VLAN |
| Authoritative DNS (Internal/Split-Horizon) | PowerDNS | Server VLAN |

---

## Resolution Flow

```text
Client query
     │
     ▼
Pi-hole (client-facing DNS / filtering)
     │
     ▼
Unbound (recursive resolver / manual entries)
     │
     ├─ AD domain query ────────────────► Active Directory DNS
     │
     ├─ Internal/split-horizon zone ───► PowerDNS (authoritative)
     │
     └─ All other queries ──────────────► Root hints / DNSSEC recursive resolution
```

Clients across all VLANs are assigned Pi-hole as their DNS server. Pi-hole provides ad-blocking and client-visible DNS services, forwards queries to Unbound for resolution. Unbound conditionally forwards:
- AD domain queries to Active Directory DNS for lab/business infrastructure
- Selected internal and split-horizon zones to PowerDNS for family/lab services
- All other queries recursively via root hints with DNSSEC validation

---

## Internal DNS Zones

### Forward Zones (PowerDNS)

- Multiple private and split-horizon zones are hosted internally
- Records are managed in PowerDNS
- Zone names are intentionally omitted from repository documentation

### Zone Types

| Zone Type | Description |
| --------- | ----------- |
| Hybrid identity-integrated zone | Selected internal records are resolved locally while other records continue to resolve externally |
| Split-horizon zone | Internal clients receive private addresses while external clients receive public addresses |
| Internal-only zone | Names exist only on the internal network and are never published publicly |

### Reverse Zones (PowerDNS)

- PTR records maintained for server VLAN subnets to support logging and diagnostics

---

## Split-Horizon DNS

Selected services and domains have both internal and external DNS records.

- **Internal resolution** → Pi-hole → Unbound → PowerDNS → returns private IP (direct LAN access)
- **External resolution** → Public DNS → returns external IP (for remote access)

This avoids NAT hairpinning and keeps internal traffic on the LAN.

---

## Resolver Chain

| Layer | Function |
| ----- | -------- |
| Pi-hole | Primary client resolver, DNS filtering, visibility, VLAN-specific policies |
| Unbound | Recursive resolution, manual/local entries, conditional forwarding, DNSSEC validation |
| PowerDNS | Authoritative answers for internal/split-horizon zones |
| Active Directory DNS | Authoritative answers for AD domain services (lab/business) |

---

## Unbound Forwarding Configuration

| Zone/Query Type | Forwarded To | Reason |
| --------------- | ------------ | ------ |
| AD domain queries | Active Directory DNS | Lab/business AD domain authority |
| Redacted internal and split-horizon zones | PowerDNS (Server VLAN) | Internal zone authority (family/lab services) |
| All other | Root hints (recursive) | Full recursive resolution with DNSSEC |

---

## DNS Security

- DNSSEC validation enabled in Unbound for all recursive queries
- Pi-hole is the only DNS endpoint exposed to client VLANs
- IoT VLAN DNS restricted to Pi-hole (prevents clients using alternative public DNS)
- Query logging enabled in Pi-hole, Unbound, and PowerDNS for audit and troubleshooting
- Block lists applied in Unbound for known malicious and ad-serving domains

---

## Integration with Service Publishing

Traefik and Authentik rely on internal DNS to route requests correctly.

- Internal service hostnames for published apps resolve to the Traefik reverse proxy
- Traefik handles TLS termination and routes to individual backend services
- Certificate management uses Let's Encrypt with DNS-01 challenge

---

## Related Documentation

- [Architecture Overview](overview.md)
- [VLAN Architecture](vlans.md)
- [Traefik Service](../services/traefik.md)
