# Syncthing

## Overview

Syncthing is a free, open-source file synchronization tool that replaces proprietary cloud services. It allows you to keep your important files in sync across multiple devices without relying on a central server.

---

## Primary Functions

- Decentralized file synchronization
- Continuous sync across devices
- Version history and disaster recovery
- Selective folder sharing between devices
- Cross-platform support

---

## Supported Devices

- Linux servers and hosts
- Windows machines
- macOS systems
- Mobile devices (via companion apps)
- Network-attached storage (NAS)

---

## Use Cases

- Personal file backup and sync
- Document sharing between family members
- Configuration file management
- Photo library synchronization
- Development project sync

---

## Architecture

- No central server dependency
- Direct device-to-device connections
- Optional relay server for NAT traversal
- Local discovery on network
- TLS encrypted transfers

---

## Integration

- Runs on Docker or bare Linux
- Independent service (no external dependencies)
- Firewall traversal via relay (if needed)
- Backup of Syncthing configuration

---

## Security Considerations

- Strong device IDs and verification
- Ignored patterns for sensitive files
- Selective folder sharing permissions
- Regular backups of synced data

---

## Related Documentation

- [Backup Strategy](../operations/backup-strategy.md)
