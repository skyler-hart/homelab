# Identity Architecture

## Overview

Identity and access management uses a segmented model:

- **Active Directory & Entra ID**: Lab and business purposes only (Windows infrastructure, Microsoft 365, Azure resources)
- **Intune**: Device management for Azure AD and hybrid devices (MDM/MAM, Autopilot provisioning)
- **Authentik**: Self-hosted identity management for family services and some lab services (internal applications, family-facing apps)

This provides centralized authentication, SSO, MFA, and role-based access control appropriate for each workload.

---

## Identity Providers

| Platform | Role | Scope |
| -------- | ---- | ----- |
| Active Directory (AD DS) | On-premises identity authority | Lab/business: Windows workstations, servers, domain-joined resources |
| Microsoft Entra ID | Cloud identity and SSO | Lab/business: Microsoft 365, Azure resources, Entra-integrated apps |
| Intune | Mobile device management and device compliance | Azure AD and hybrid device management, Autopilot provisioning, MAM policies |
| Authentik | Self-hosted identity and SSO | Family services and selected lab services (Traefik, Immich, Jellyfin, Mealie, etc.) |

---

## Authentication Flows

### Family & Lab Services (Authentik)

```text
User → Traefik (reverse proxy)
     → Authentik (forward auth)
     → OIDC/OAuth2 → Service
```

- All self-hosted application services are fronted by Traefik
- Authentik is configured as a forward authentication provider
- Users authenticate once via Authentik and access all integrated apps via SSO
- Includes: family services (Immich, Jellyfin, Mealie, etc.) and lab services fronted via Traefik

### Business & Lab Infrastructure (AD / Entra ID)

```text
User → Active Directory (domain authentication)
     → Entra ID (cloud sync and MFA)
     → Microsoft 365 / Azure / Domain Resources
```

- Entra ID enforces MFA and conditional access policies
- AD DS is synchronized to Entra ID via Microsoft Entra Connect Sync
- Applies to lab/business workstations, servers, and cloud resources only

---

## Device Management

### Intune (MDM/MAM)

Intune manages device compliance and configuration for Azure AD and hybrid-joined devices.

**Capabilities:**
- Device compliance policies (encryption, antivirus, firewall requirements)
- Configuration profiles (Wi-Fi, VPN, certificate distribution)
- Mobile Application Management (MAM) for app-based access control
- Conditional Access integration with Entra ID

**Device Types:**
- **Azure AD-joined devices**: Cloud-only devices without AD DS domain membership
- **Hybrid Azure AD-joined devices**: On-premises AD DS domain-joined and Entra ID registered
- **On-premises AD DS devices**: Legacy devices managed via Group Policy (not Intune-enrolled)

### Windows Autopilot

Autopilot automates provisioning and deployment of new Azure AD and hybrid-joined devices.

**Workflow:**
1. Device powers on and connects to network
2. Autopilot retrieves device profile from cloud
3. Device joins Azure AD or hybrid Azure AD
4. Intune policies and apps are deployed
5. User signs in with Entra ID credentials

---

| Protocol | Used By |
| -------- | ------- |
| OpenID Connect (OIDC) | Authentik ↔ self-hosted apps |
| OAuth 2.0 | Authentik ↔ self-hosted apps |
| SAML 2.0 | Authentik ↔ legacy/enterprise apps |
| Kerberos | Active Directory domain authentication |
| LDAP | Active Directory directory queries |

---

## Multi-Factor Authentication

- **Authentik**: MFA enforced for all SSO-integrated services via TOTP or WebAuthn
- **Entra ID / Intune**: MFA enforced via Conditional Access for all Microsoft cloud services and devices
- **Active Directory**: MFA enforced at perimeter via Authentik proxy for self-hosted access

---

## Role-Based Access Control

**Lab/Business:**
- AD security groups control access to network shares, servers, and Windows resources
- Entra ID groups control access to Microsoft 365 apps and cloud resources

**Family & Lab Services:**
- Authentik groups and policies control access to self-hosted applications and family services
- Principle of least privilege applied across all tiers

---

## User Lifecycle

**Lab/Business (AD / Entra ID):**

| Stage | Process |
| ----- | ------- |
| Provisioning | Manual for lab environment; templated accounts in AD |
| Sync | AD → Entra ID via Microsoft Entra Connect Sync |
| Deprovisioning | Disable in AD, propagates to Entra ID |

**Family & Lab Services (Authentik):**

| Stage | Process |
| ----- | ------- |
| Provisioning | Create account in Authentik management interface |
| Authentication | OAuth2/OIDC to Traefik-fronted services |
| Deprovisioning | Disable or delete in Authentik |

---

## Related Documentation

- [Architecture Overview](overview.md)
- [Authentik Service](../services/authentik.md)
- [Traefik Service](../services/traefik.md)
