# SLO Specifications

This directory contains SLO definitions for all platform services.

## Error budget policy

- If error budget consumed > 50% in a month: freeze non-critical releases
- If error budget consumed > 75% in a month: freeze all releases
- If error budget consumed > 100%: incident review required before any release

## SLO summary

| Service | Availability | Latency p99 | Error Rate | Window |
|---------|-------------|-------------|------------|--------|
| payments-service | 99.99% | < 500ms | < 0.01% | 30 days |
| fx-rate-service | 99.95% | < 100ms | < 0.05% | 30 days |
| auth-service | 99.99% | < 200ms | < 0.01% | 30 days |
| audit-service | 99.9% | < 1000ms | < 0.1% | 30 days |
| api-gateway | 99.99% | < 200ms | < 0.01% | 30 days |
| notification-service | 99.5% | < 2000ms | < 0.5% | 30 days |
