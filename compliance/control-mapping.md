# Compliance Control Mapping

This document maps platform capabilities to regulatory control requirements.

## PCI-DSS v4.0

| Requirement | Control | Implementation | Evidence Source |
|-------------|---------|----------------|-----------------|
| 1.1 — Network access controls | API gateway enforces all external access | api-gateway mTLS + JWT | api-gateway access logs |
| 1.2 — Network segmentation | Zero-trust mTLS between all services | ADR-005 | Service mesh telemetry |
| 4.2 — Encrypt transmission | TLS 1.3 on all endpoints | api-gateway TLS config | Certificate scan results |
| 6.3 — Security vulnerabilities | SAST/SCA in CI pipeline | GitHub Actions workflows | CI scan reports |
| 7.1 — Access control | RBAC via auth-service | auth-service RBAC config | auth-service audit logs |
| 8.2 — Authentication | JWT with short expiry | auth-service token policy | auth-service logs |
| 10.2 — Audit log | Immutable audit trail | audit-service event store | audit-service records |
| 10.3 — Audit log protection | Append-only event store | ADR-001 event sourcing | audit-service architecture |
| 11.3 — Vulnerability scanning | Nightly dependency scanning | TechDebtLedger agent | Self-scan reports |
| 12.10 — Incident response | Automated IR via IncidentPilot | IncidentPilot workflows | Post-mortem records |

## SOX ITGC

| Control Area | Control | Implementation | Evidence Source |
|-------------|---------|----------------|-----------------|
| Change management | All changes via PR + CI | GitHub branch protection | GitHub PR history |
| Access controls | RBAC + MFA enforced | auth-service | auth-service audit logs |
| Incident management | Documented IR process | IncidentPilot post-mortems | Post-mortem records |
| System availability | SLO monitoring + alerting | PlatformSLOBoard | SLO dashboards |
| Audit trail | Immutable event log | audit-service | audit-service records |
| Change evidence | CHANGELOG + ADRs | All repos | GitHub commit history |
| Monitoring | DORA metrics + health checks | TeamHealthRadar | Weekly health reports |

## FFIEC IT Examination Handbook

| Domain | Requirement | Implementation | Evidence Source |
|--------|-------------|----------------|-----------------|
| Information security | Zero-trust architecture | ADR-005 | Network audit logs |
| Resilience | 99.99% SLO for P0 services | PlatformSLOBoard | SLO reports |
| Incident response | < 1 hour MTTA for P0 | IncidentPilot | Incident records |
| Change management | All changes peer-reviewed | GitHub PR process | PR history |
| Vendor management | Third-party dependencies tracked | TechDebtLedger | Dependency reports |
| Business continuity | Multi-region deployment capable | Infrastructure ADRs | Architecture docs |
| Audit and accountability | Comprehensive audit trail | audit-service | Audit records |
