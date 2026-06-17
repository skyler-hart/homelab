# Monitoring

## Overview

Infrastructure and service health are continuously monitored to enable proactive detection of failures, performance degradation, and security events. Monitoring covers system resources, service availability, authentication activity, and network health.

---

## Monitoring Stack

| Tool | Role |
| ---- | ---- |
| Uptime Kuma | Service availability and endpoint health checks |
| Grafana | Metrics dashboards and visualization |
| Prometheus | Metrics collection and storage |
| Node Exporter | Host-level metrics (CPU, memory, disk, network) |
| cAdvisor | Docker container metrics |
| Authentik (built-in) | Authentication and access event logging |
| Traefik (built-in) | HTTP access logs and routing metrics |

---

## Monitoring Scope

### System Health

- CPU, memory, and disk utilization per host
- Disk I/O and network throughput
- System uptime and load average

### Service Availability

- HTTP/HTTPS endpoint checks for all self-hosted services
- Docker container state monitoring
- Internal DNS resolution checks

### Authentication Events

- Authentik login success and failure events
- MFA challenge events
- Policy violation alerts

### Network Health

- VLAN connectivity tests
- Gateway reachability
- WAN link availability

---

## Alerting

| Alert Type | Trigger | Notification Channel |
| ---------- | ------- | -------------------- |
| Service down | Endpoint fails 2 consecutive checks | Notification (e.g., email / ntfy) |
| Host CPU high | > 90% for 5 minutes | Notification |
| Disk near full | > 85% utilization | Notification |
| Auth failures | > 5 failed logins in 10 minutes | Notification |
| WAN down | Gateway unreachable | Notification |

---

## Dashboards

- **Infrastructure Overview**: Host resource utilization across all systems
- **Docker Services**: Container health, restarts, and resource usage
- **Service Availability**: Uptime Kuma summary for all monitored endpoints
- **Authentik**: Authentication events, active sessions, policy hits

---

## Retention

| Data Type | Retention Period |
| --------- | ---------------- |
| Prometheus metrics | 30 days |
| Uptime Kuma history | 90 days |
| Application logs | 30 days |

---

## Related Documentation

- [Architecture Overview](../architecture/overview.md)
- [Disaster Recovery](disaster-recovery.md)
