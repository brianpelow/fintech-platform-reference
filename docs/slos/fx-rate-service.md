# SLO: fx-rate-service

**Criticality**: P0
**Owner**: trading-team
**Last reviewed**: 2026-04-01

## Service level indicators

### Availability SLI
- **Definition**: FX rate feed available and current
- **Good event**: Rate data refreshed within 60 seconds, HTTP 200
- **Bad event**: Stale data > 60 seconds, HTTP 5xx, feed unavailable

### Latency SLI
- **Definition**: Rate lookup response time
- **Threshold**: p99 < 100ms

### Data freshness SLI
- **Definition**: Age of most recent FX rate data
- **Threshold**: < 60 seconds during market hours

## Service level objectives

| SLO | Target | Window | Error Budget |
|-----|--------|--------|-------------|
| Availability | 99.95% | 30 days | 21.6 minutes/month |
| Latency p99 | 99.5% of requests < 100ms | 30 days | 216 minutes/month |
| Data freshness | 99.9% of rates < 60s old | Market hours | 43 minutes/month |

## Alerting thresholds

- **Page immediately**: Feed unavailable > 2 minutes during market hours
- **Page within 6 hours**: Burn rate > 6x outside market hours
- **Ticket**: Latency p99 > 200ms sustained for 15 minutes

## Compliance notes

FX rate integrity is critical for regulatory trade reporting.
Stale rate data must be logged as a data quality incident.
