# Baget

## Overview

Baget is a lightweight NuGet server that allows you to self-host a private NuGet package repository for .NET libraries and applications.

---

## Primary Functions

- Private NuGet package repository for .NET libraries
- PowerShell module hosting and distribution
- Package versioning and dependency management
- Search and discovery of packages
- API for package publishing and consumption
- Internal module installation without external internet access

---

## Use Cases

**Primary:**

- Internal package distribution for PowerShell modules
- Centralized package source for development and operations teams
- Easy internal module installation and updates without public repository dependency

**Secondary:**

- Testing and validating PowerShell module deployments before publishing. Namely WSTools.
- Bridging air-gapped networks (local package mirror for offline environments)
- Alternative to public NuGet.org for internal-only code

---

## Architecture

- ASP.NET Core application
- File-based or database-backed storage
- NuGet protocol compatibility
- API for publishing and querying

---

## Integration

- MariaDB or SQLite backend
- Traefik for reverse proxy (optional)
- Authentik for access control (optional)
- Docker deployment
- Synology NAS storage integration

---

## Package Management

**NuGet Packages (.NET):**

- Upload packages via NuGet client
- Delete and manage package versions
- Search via NuGet protocol
- API key authentication

**PowerShell Modules:**

- Host PSGallery-compatible PowerShell modules
- Internal PowerShell module discovery and installation
- Version management for module deployments
- Testing environment for module validation before production use

---

## Security Considerations

- API key management and rotation
- Access control via firewall rules or Authentik
- SSL/TLS for package transfers
- Backup of package repository

---

## Related Documentation

- [Traefik Service](traefik.md)
- [Authentik Service](authentik.md)
- [Backup Strategy](../operations/backup-strategy.md)
