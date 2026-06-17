# Traefik

## Overview

Traefik is the central ingress controller and reverse proxy for self-hosted applications in the lab. It handles HTTP/HTTPS routing, TLS termination, certificate automation, and integration with Authentik for access control.

---

## Primary Responsibilities

- Reverse proxy for internal and external application access
- TLS termination for published services
- Dynamic routing based on Docker labels or file configuration
- Integration with Authentik forward authentication
- Centralized ingress policy and service onboarding

---

## Traffic Flow

```text
Client
  -> DNS resolves internal service hostname
  -> Traefik
  -> Authentik (when protected)
  -> Backend service
```

---

## Core Integrations

- PowerDNS for internal service records
- Pi-hole and Unbound for client-side DNS resolution path
- Authentik for authentication and SSO enforcement
- Docker for dynamic service discovery
- Let's Encrypt for certificate issuance and renewal

---

## Security Controls

- HTTPS-only access for published services
- Middleware-based access policies
- Authentik forward auth for selected applications
- Centralized certificate management
- Access and error logging for audit and troubleshooting

---

## Operational Considerations

- New services should be onboarded through a consistent router / middleware pattern
- DNS and Traefik route definitions must stay aligned
- Certificate renewals should be monitored and periodically tested
- Any externally published service should be reviewed for exposure and authentication requirements

---

## Failure Impact

Traefik is a shared dependency for most user-facing services. Failure can make multiple applications appear offline even when the backend containers are healthy. Monitoring and backup of its configuration are therefore high priority.

---

## Related Documentation

- [DNS Architecture](../architecture/dns.md)
- [Authentik Service](authentik.md)
- [Monitoring](../operations/monitoring.md)
