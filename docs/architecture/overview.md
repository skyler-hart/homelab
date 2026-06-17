# Infrastructure Overview

## Purpose

This environment serves as a self-hosted infrastructure and engineering lab used to design, test, validate, and document modern infrastructure, identity, automation, networking, and security solutions.

The platform is built using enterprise infrastructure principles including network segmentation, centralized identity management, service publishing, automation, monitoring, backup, and disaster recovery.

---

## Design Goals

The environment is designed around several core principles:

- Security through network segmentation
- Centralized identity and access management
- Infrastructure automation and repeatability
- High service availability and resiliency
- Documentation-first operations
- Simplified backup and disaster recovery
- Continuous learning and technology evaluation

---

## Core Infrastructure

### Networking

The network is built around a segmented architecture designed to separate systems according to function and trust level.

#### Primary Components

- UniFi Dream Machine Pro
- Managed Switching Infrastructure
- VLAN Segmentation
- Internal DNS Services
- Reverse Proxy Services

#### Network Segments

- User Devices
- Server Infrastructure
- Workstations
- IoT Devices
- Security Cameras
- Management Systems

#### Objectives

- Reduce attack surface
- Limit lateral movement
- Improve troubleshooting
- Simplify policy enforcement

---

### Compute

Compute resources support both infrastructure services and application workloads.

#### Platforms

- Synology RS1619xs+
- Docker Hosts
- Virtual Machines
- Linux-Based Services
- Windows Server Services

#### Workloads

- Infrastructure Services
- Identity Services
- Automation Platforms
- Monitoring Solutions
- Self-Hosted Applications

---

### Storage

Centralized storage provides data services for applications, backups, and operational data.

#### Storage Functions

- Application Data Storage
- Media Storage
- Configuration Backups
- Infrastructure Documentation
- Disaster Recovery Assets

#### Storage Objectives

- Data Protection
- Operational Resilience
- Simplified Recovery
- Centralized Management

---

### Identity

Identity services provide centralized authentication, authorization, and access management across the environment.

#### Identity Components

- Active Directory
- Microsoft Entra ID
- Authentik
- OpenID Connect (OIDC)

#### Capabilities

- Single Sign-On (SSO)
- Multi-Factor Authentication (MFA)
- Centralized Identity Management
- Role-Based Access Control
- Application Federation

#### Benefits

- Reduced credential sprawl
- Improved security posture
- Simplified administration
- Consistent authentication experience

---

### Service Publishing

Applications are securely exposed through centralized ingress and authentication services.

#### Publishing Components

- Traefik Reverse Proxy
- Authentik Forward Authentication
- Automated Certificate Management
- Internal DNS Integration

#### Publishing Objectives

- Secure application access
- Centralized ingress management
- Consistent authentication workflows
- Simplified service onboarding

---

### Services

The environment hosts a comprehensive suite of infrastructure, family, and utility services.

#### Infrastructure & Platform Services

- Traefik (reverse proxy and ingress controller)
- Authentik (centralized authentication and SSO)
- Pi-hole (DNS filtering and visibility)
- Unbound (recursive DNS resolver)
- PowerDNS (authoritative DNS for internal zones)
- pdns-admin (PowerDNS management interface)
- Proxmox (virtualization and container orchestration)
- Portainer (Docker and container management)
- NetBox (infrastructure asset management and DCIM)
- MariaDB (database backend)
- phpMyAdmin (database administration)

#### Family & Media Services

- Immich (photo and video backup and indexing)
- Jellyfin (media server and streaming)
- Plex (media server and streaming)
- Mealie (recipe management and meal planning)
- Grocy (inventory management and household organization)
- Homebox (personal inventory and asset tracking)

#### Automation & Remote Access

- Home Assistant (home automation orchestration)
- Syncthing (decentralized file synchronization)
- RustDesk (remote desktop access and management)

#### Utilities & Development Tools

- IT-Tools (collection of IT utilities)
- Baget (NuGet package server)
- Supporting Services (monitoring, dashboards, automation)

---

### Monitoring and Operations

Infrastructure health and service availability are continuously monitored to support proactive operations.

#### Monitoring Areas

- System Health
- Resource Utilization
- Service Availability
- Authentication Events
- Network Connectivity

#### Operational Focus

- Incident Detection
- Performance Monitoring
- Capacity Planning
- Change Management
- Disaster Recovery Validation

---

## Architecture Principles

This environment is maintained according to the following principles:

1. Infrastructure should be documented.
2. Services should be reproducible.
3. Security should be layered.
4. Automation should replace repetitive tasks.
5. Identity should be centralized.
6. Recovery procedures should be tested.
7. Operational complexity should be minimized wherever possible.

---

## Future Areas of Exploration

- Infrastructure as Code (Terraform)
- Kubernetes and GitOps
- Expanded Cloud Integration
- Advanced Observability
- Security Automation
- Zero Trust Architectures
