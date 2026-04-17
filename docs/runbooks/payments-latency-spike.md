# Runbook: payments-service latency spike

**Trigger**: p99 latency > 500ms for 5+ minutes
**Severity**: High
**Owner**: payments-team
**Est. resolution**: 30-45 minutes

## Immediate actions (0-5 minutes)

1. Acknowledge alert and join #incidents Slack channel
2. Check Dynatrace dashboard for service health overview
3. Identify if latency is across all endpoints or specific routes
4. Check for recent deployments in last 2 hours

## Investigation (5-15 minutes)

5. Check database query performance — look for slow queries > 100ms
6. Check downstream service dependencies (auth-service, audit-service)
7. Review error logs for timeout patterns or connection errors
8. Check infrastructure metrics — CPU, memory, connection pool usage
9. Check for traffic spike — compare current RPS to baseline

## Remediation

**If deployment-related:**
10. Initiate rollback via GitHub Actions: trigger rollback workflow
11. Monitor latency for 5 minutes post-rollback

**If database-related:**
12. Check for long-running transactions and kill if safe
13. Review connection pool settings — increase if exhausted

**If traffic spike:**
14. Enable rate limiting at api-gateway if not already active
15. Scale payments-service horizontally if Kubernetes headroom exists

## Escalation triggers

- No improvement after 30 minutes: escalate to payments-team lead
- Error rate > 1%: escalate to engineering manager
- Customer impact confirmed: notify customer success team

## Post-incident

- Complete post-mortem within 24 hours
- File SOX ITGC incident report within 1 hour of detection
- Update this runbook with any new findings
