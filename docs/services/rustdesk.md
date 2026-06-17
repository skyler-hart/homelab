# RustDesk

## Overview

RustDesk is a free, open-source remote desktop application that allows secure remote access to computers. Self-hosted relay and ID servers provide independent operation without reliance on proprietary cloud services.

---

## Primary Functions

- Remote desktop access and control
- Unattended remote access
- File transfer between devices
- Clipboard sharing
- Audio and video streaming

---

## Use Cases

- Remote support and troubleshooting
- Home network access from remote locations
- Administrative access to lab systems
- File and media access away from home
- Cross-platform device management

---

## Architecture

**Connectivity Model:**
- Direct peer-to-peer connections preferred when both devices can connect
- Relay server for connection forwarding when direct connection unavailable (NAT/firewall)
- ID server for device registration and discovery
- TLS encryption for all connections

**Self-Hosted Infrastructure:**
- ID server deployed for device registration and management
- Relay server deployed for secure connection forwarding
- Full control and privacy over remote access infrastructure
- No dependency on external cloud relay services

---

## Self-Hosted Infrastructure

### ID Server
- Registers and manages device identities
- Stores device credentials and public keys
- Enables device discovery and lookup
- Accessed during initial connection establishment

### Relay Server
- Forwards traffic between RustDesk clients when direct P2P not possible
- Handles encrypted connection forwarding
- Operates transparently (clients don't send credentials to relay)
- Fallback for NAT-restricted or firewall-blocked connections

**Deployment:**
- Both services run on Docker or bare Linux
- Typically deployed on infrastructure VLAN with restricted firewall access
- Port forwarding or VPN-based access from external networks
- Optional integration with Traefik for web UI management

---

## Security Considerations

- Strong connection credentials and tokens
- Restrict access to trusted devices only
- Consider firewall rules for relay/ID server
- Regular software updates for patches

---

## Integration

- ID/relay server access via internal DNS or static IPs
- Internal network clients configured to use self-hosted ID server
- External access (optional): Published through Traefik or VPN tunnel
- Runs on Docker or bare Linux
- Integration with Traefik authentication optional for web management interfaces

---

## Related Documentation

- [VLAN Architecture](../architecture/vlans.md)
- [Firewall Policy](../architecture/vlans.md)
