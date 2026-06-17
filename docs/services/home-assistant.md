# Home Assistant

## Overview

Home Assistant provides smart home orchestration, automation, and device integration across the lab environment. It acts as the primary control plane for IoT workflows and centralizes telemetry, automation rules, and event-driven actions.

---

## Primary Functions

- Device discovery and control
- Automation and scheduling
- Sensor and event aggregation
- Dashboarding for home and lab operations
- Integration point for IoT-focused workflows

---

## Network Placement

- Hosted in the Server VLAN
- Communicates with devices in the IoT VLAN through tightly scoped firewall rules
- May consume MQTT, HTTP, mDNS, or vendor-specific APIs depending on device type

---

## Security Considerations

- External is proxied through Traefik and protected by Authentik where practical
- Long-lived access tokens should be limited and rotated when possible
- IoT device access is restricted to only required ports and protocols
- Administrative access should be limited to trusted user/workstation networks

---

## Backup Requirements

- Full Home Assistant configuration backup
- Secrets and integration configuration
- Automation YAML or UI-managed automation exports
- Add-on configuration where applicable

---

## Operational Notes

- Changes to IoT firewall policy should be validated against Home Assistant automations
- Any MQTT or webhook dependencies should be documented alongside the service deployment
- Recovery testing should include validation of critical automations, not just UI availability

---

## Related Documentation

- [VLAN Architecture](../architecture/vlans.md)
- [Backup Strategy](../operations/backup-strategy.md)
- [Monitoring](../operations/monitoring.md)
