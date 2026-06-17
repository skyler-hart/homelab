# Proxmox

## Overview

Proxmox Virtual Environment (PVE) provides virtualization and container orchestration for infrastructure workloads, VMs, and LXC containers in the lab environment.

---

## Primary Functions

- Hypervisor platform for virtual machines
- LXC container orchestration
- Resource isolation and allocation
- HA clustering (if applicable)
- Storage backend management

---

## Integration

- Docker hosts may run on Proxmox VMs or LXC containers
- NetworkIntegration with UniFi VLAN configuration
- Backup integration with Synology NAS
- Monitoring via external tools (Prometheus, Uptime Kuma)

---

## Related Documentation

- [Architecture Overview](../architecture/overview.md)
- [Monitoring](../operations/monitoring.md)
