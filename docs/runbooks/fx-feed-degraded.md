# Runbook: FX rate feed degraded

**Trigger**: FX rate data stale > 60 seconds during market hours
**Severity**: High
**Owner**: trading-team
**Est. resolution**: 15-30 minutes

## Immediate actions (0-5 minutes)

1. Acknowledge alert and join #incidents channel
2. Confirm staleness: check fx-rate-service /health endpoint
3. Check market hours — alert is lower priority outside 07:00-22:00 UTC
4. Notify trading operations team immediately if during market hours

## Investigation (5-15 minutes)

5. Check upstream feed provider status page
6. Check fx-rate-service logs for connection errors to feed provider
7. Verify network connectivity to feed provider endpoints
8. Check for recent deployments in fx-rate-service

## Remediation

**If feed provider issue:**
9. Switch to secondary feed provider (see config/feed-providers.yaml)
10. Alert trading operations that rates are from secondary source

**If service issue:**
11. Restart fx-rate-service pod if connection is stuck
12. Roll back if recent deployment is suspected cause

## Escalation triggers

- Feed unavailable > 5 minutes during market hours: page trading lead
- No secondary feed available: escalate to VP Engineering immediately

## Compliance notes

Stale FX rate incidents must be logged as data quality incidents.
Trading operations must be notified within 2 minutes of detection.
Document rate source for all trades executed during degraded period.
