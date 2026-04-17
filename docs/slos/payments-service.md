# SLO: payments-service

**Criticality**: P0
**Owner**: payments-team
**Last reviewed**: 2026-04-01

## Service level indicators

### Availability SLI
- **Definition**: (successful requests / total requests) * 100
- **Good event**: HTTP 2xx or 3xx response within 2 seconds
- **Bad event**: HTTP 5xx, timeout, or connection error
- **Measurement**: Dynatrace synthetic monitoring, 1-minute intervals

### Latency SLI
- **Definition**: Proportion of requests completing within threshold
- **Threshold**: p50 < 100ms, p95 < 300ms, p99 < 500ms
- **Measurement**: Dynatrace APM request timing

### Error rate SLI
- **Definition**: (error responses / total responses) * 100
- **Threshold**: < 0.01%

## Service level objectives

| SLO | Target | Window | Error Budget |
|-----|--------|--------|-------------|
| Availability | 99.99% | 30 days | 4.32 minutes/month |
| Latency p99 | 99.5% of requests < 500ms | 30 days | 216 minutes/month |
| Error rate | < 0.01% | 30 days | 4.32 minutes/month |

## Alerting thresholds

- **Page immediately**: Burn rate > 14.4x (1-hour budget exhaustion)
- **Page within 6 hours**: Burn rate > 6x (6-hour budget exhaustion)
- **Ticket**: Burn rate > 1x sustained for 1 hour

## Compliance notes

99.99% availability satisfies FFIEC resilience requirements for
payment processing systems. SLO breach triggers mandatory incident
report within 1 hour per SOX ITGC controls.
