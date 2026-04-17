# Runbooks

Operational runbooks for common incident scenarios.

## Index

| Runbook | Trigger | Severity |
|---------|---------|----------|
| payments-latency-spike | p99 latency > 500ms | High |
| fx-feed-degraded | FX rate feed stale > 60s | High |
| auth-service-errors | Error rate > 1% | Critical |
| database-connection-exhaustion | Connection pool > 90% | Critical |

## Using these runbooks

1. These runbooks are automatically retrieved by IncidentPilot during incidents
2. Follow steps in order unless circumstances require deviation
3. Document any deviations in the post-mortem
4. Update runbooks after each incident with lessons learned
