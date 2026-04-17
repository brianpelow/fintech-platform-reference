# fintech-platform-reference

> Reference architecture for a regulated fintech engineering platform.

## Overview

Engineering system of record for a canonical regulated fintech platform.
Covers a payments and FX trading platform under PCI-DSS, SOX ITGC, and FFIEC.

## Platform services

| Service | Domain | Criticality | SLO |
|---------|--------|-------------|-----|
| payments-service | Payments | P0 | 99.99% |
| fx-rate-service | Trading | P0 | 99.95% |
| auth-service | Identity | P0 | 99.99% |
| audit-service | Compliance | P1 | 99.9% |
| notification-service | Comms | P2 | 99.5% |
| api-gateway | Platform | P0 | 99.99% |

## Architecture principles

1. Compliance by design — controls built in, not bolted on
2. Defense in depth — no single point of failure or trust
3. Observable by default — every service emits structured telemetry
4. Auditability first — every state change produces an immutable audit record
5. Platform over heroics — automation eliminates manual toil

## Regulatory context

- PCI-DSS v4.0 — payment card data handling
- SOX ITGC — financial reporting system controls
- FFIEC IT Examination Handbook — information security and resilience
- ISO 20022 — payment message standards

## Structure

```
docs/
  architecture/   system context, component diagrams, data flows
  adr/            Architecture Decision Records
  runbooks/       operational runbooks
  slos/           SLO specifications and error budget policies
catalog/
  components/     Backstage component definitions
  systems/        Backstage system definitions
  apis/           Backstage API definitions
compliance/       PCI-DSS, SOX, FFIEC control mappings
```

## License

Apache 2.0
