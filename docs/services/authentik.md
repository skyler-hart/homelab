# Authentik

## Overview

Authentik is the central identity broker for self-hosted services in the lab. It provides single sign-on, multi-factor authentication, policy enforcement, and application federation for services published through Traefik.

---

## Role in the Environment

- Centralized authentication for self-hosted applications
- Forward authentication provider for Traefik
- Identity abstraction layer between users and individual services
- MFA enforcement point for internal and externally published apps

---

## Protocols

| Protocol | Use Case |
| -------- | -------- |
| OIDC | Primary integration method for modern self-hosted apps |
| OAuth2 | API and delegated access scenarios |
| SAML | Legacy or enterprise-style application integrations |
| LDAP (optional) | Directory-backed application lookups where needed |

---

## Integrations

- Traefik
- Immich
- Nextcloud
- Internal admin tools and dashboards

---

## Security Controls

- MFA using TOTP and/or WebAuthn
- Group-based access control
- Per-application access policies
- Audit logging for authentication events
- Session management and token expiration controls

---

## Benefits

- Centralized identity and authentication policy
- Reduced credential sprawl across self-hosted apps
- Consistent user experience for service access
- Simplified onboarding of new internal services

---

## Dependencies

- DNS records for service discovery
- Traefik for ingress and application publishing
- Reliable backup of Authentik configuration and database

---

## Related Documentation

- [Identity Architecture](../architecture/identity.md)
- [Traefik Service](traefik.md)
- [Disaster Recovery](../operations/disaster-recovery.md)
