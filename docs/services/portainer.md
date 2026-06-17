# Portainer

## Overview

Portainer is a container management platform that provides a web UI for Docker and Kubernetes management, simplifying container lifecycle operations.

---

## Primary Functions

- Docker container management and monitoring
- Image and volume management
- Stack deployment from Compose files
- User and access control
- Environment and agent management

---

## Use Cases

- Quick container diagnostics and troubleshooting
- Lightweight CI/CD integration
- Multi-host Docker management
- Non-CLI container operations

---

## Security Considerations

- Portainer should be restricted to trusted users
- Access controlled via Authentik SSO or local credentials
- Should not be exposed externally without strong authentication
- API keys should be rotated periodically

---

## Related Documentation

- [Traefik Service](traefik.md)
- [Authentik Service](authentik.md)
- [Monitoring](../operations/monitoring.md)
