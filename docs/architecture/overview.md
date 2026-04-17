# Platform Architecture Overview

## System context

The fintech platform serves three categories of clients:
- **Consumer apps** — mobile and web applications for end users
- **Partner banks** — correspondent banking and payment rail integrations
- **Internal systems** — back-office, reporting, and compliance tooling

All external traffic enters through the api-gateway. No service is
directly exposed to the public internet.

## Core services

```
                    [External Clients]
                           |
                    [api-gateway] <-- TLS termination, JWT validation, rate limiting
                    /     |      \
          [payments] [fx-rate] [auth]
               |         |        |
               +----[audit-service]----+
                           |
                   [Event Store (append-only)]
```

## Data flows

### Payment initiation
1. Client authenticates via auth-service, receives JWT
2. Payment request sent to api-gateway with JWT
3. api-gateway validates JWT, routes to payments-service
4. payments-service validates, enriches with FX rate if needed
5. payments-service emits PaymentInitiated event to audit-service
6. Settlement initiated asynchronously

### FX rate lookup
1. fx-rate-service polls upstream providers every 30 seconds
2. Rates cached in-memory with TTL
3. Rate requests served from cache, miss triggers upstream fetch
4. All rate lookups logged to audit-service

## Infrastructure

- **Compute**: Kubernetes (EKS)
- **Networking**: Istio service mesh for mTLS
- **Observability**: Dynatrace APM + PagerDuty
- **CI/CD**: GitHub Actions
- **Secrets**: HashiCorp Vault
- **Registry**: ECR

## Platform tooling

| Tool | Purpose | Repo |
|------|---------|------|
| IncidentPilot | Agentic incident response | brianpelow/IncidentPilot |
| PlatformSLOBoard | SLO monitoring | brianpelow/PlatformSLOBoard |
| TeamHealthRadar | DORA metrics | brianpelow/TeamHealthRadar |
| TechDebtLedger | Debt tracking | brianpelow/TechDebtLedger |
| mcp-compliance-grc | Compliance automation | brianpelow/mcp-compliance-grc |
| BoardroomBrief | Executive reporting | brianpelow/BoardroomBrief |
| platform-conductor | Platform orchestration | brianpelow/platform-conductor |
