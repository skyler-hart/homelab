# VLAN Architecture

## Overview

The network is segmented into discrete VLANs to enforce trust boundaries, limit lateral movement, and simplify policy enforcement. All inter-VLAN traffic is routed through the UniFi Dream Machine Pro where firewall rules are applied.

---

## VLAN Segments

| VLAN ID | Name | Purpose | Trust Level |
| ------- | ---- | ------- | ----------- |
| 1 | Management | Network infrastructure management, UDM Pro, switches, APs | High |
| 10 | Servers | Docker hosts, VMs, core infrastructure services | High |
| 20 | Workstations | Domain-joined and personal workstations | Medium |
| 30 | User Devices | Laptops, phones, and general personal devices | Medium |
| 40 | IoT | Smart home devices, sensors, automation endpoints | Low |
| 50 | Cameras | IP security cameras and NVR | Isolated |
| 60 | Guest | Temporary guest Wi-Fi access | Untrusted |

---

## Firewall Policy Summary

### General Rules

- All inter-VLAN traffic is denied by default
- Explicit allow rules are added per service requirement
- IoT and Camera VLANs cannot initiate connections to any other segment
- Guest VLAN is internet-only with no access to internal resources
- Management VLAN is accessible only from Workstations and Servers

### Key Allow Rules

| Source VLAN | Destination VLAN | Port / Protocol | Reason |
| ----------- | ---------------- | --------------- | ------ |
| Workstations | Servers | 443 (HTTPS) | Web service access |
| Workstations | Management | 22, 443, 8443 | Admin access |
| Servers | Management | 53 (DNS) | Internal DNS resolution |
| IoT | Servers | 1883 (MQTT) | Home Assistant MQTT broker |
| IoT | — | 443 (HTTPS) | Cloud updates only |
| Cameras | Servers | NVR port | Camera stream to NVR |

---

## DNS per VLAN

Each VLAN is assigned an internal DNS server to enforce consistent name resolution and allow for split-horizon DNS where needed.

- Management, Servers, Workstations → Pi-hole
- IoT, Cameras → Pi-hole with restricted egress to prevent alternate DNS
- Guest → ISP DNS or public resolver (1.1.1.1)

---

## Design Principles

- **Least privilege**: Devices only reach what they need
- **Blast radius containment**: Compromised IoT or guest devices cannot pivot to servers
- **Simplified auditing**: Traffic flows are predictable and logged at the gateway
- **Consistent policy**: UniFi firewall rules are the single source of inter-VLAN enforcement
