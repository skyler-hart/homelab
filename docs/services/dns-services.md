# DNS Services: Pi-hole, Unbound, PowerDNS

## Overview

DNS is split across multiple services to provide on-premises AD domain services, client-facing filtering, recursive resolution, and authoritative zone management. Together they form the backbone of internal service discovery and security filtering across both business/lab infrastructure and family services.

---

## Service Roles

### Active Directory DNS

- DNS authority for on-premises AD domains (lab/business)
- Dynamic DNS updates from domain-joined devices
- SRV records for AD services (Kerberos, LDAP, Netlogon, etc.)
- Replication between multiple AD DNS servers for redundancy
- Integration point for hybrid Azure AD/Entra ID scenarios

### Pi-hole

- Client-facing DNS resolver and filter
- Ad and malware blocking for all VLANs
- Query logging and statistics
- Conditional forwarding to AD DNS for AD domain queries

### Unbound

- Recursive DNS resolver for external queries
- Local/manual entry management
- DNSSEC validation
- Forward zone definitions for internal and split-horizon domains
- Forwarding to PowerDNS for hosted zones
- Conditional forwarding to AD DNS for on-premises AD environment queries

### PowerDNS

- Authoritative DNS for internal zones (family services, lab services)
- Zone management and API
- pdns-admin provides web UI for zone management
- Supports multiple zone types (native, slave, AXFR)
- Independent from AD DNS; handles non-AD internal zones

---

## Architecture

See [DNS Architecture](../architecture/dns.md) for the complete resolution flow and configuration details.

---

## Related Documentation

- [DNS Architecture](../architecture/dns.md)
- [pdns-admin](pdns-admin.md)
- [Architecture Overview](../architecture/overview.md)
