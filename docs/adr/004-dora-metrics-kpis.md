# ADR-004: Adopt DORA metrics as primary delivery KPIs

**Status**: Accepted
**Date**: 2026-02-01
**Authors**: @brianpelow

## Context

Engineering leadership needs objective, industry-benchmarked metrics to
communicate delivery performance to boards and regulators. Subjective
velocity metrics are insufficient for regulated environments.

## Decision

Adopt the four DORA metrics as the primary engineering delivery KPIs:
deployment frequency, lead time for changes, change failure rate, and
time to restore service. Target elite band performance within 12 months.

## Rationale

- Industry-standard, research-backed framework
- Maps directly to regulatory resilience requirements
- Objective and automatable via TeamHealthRadar
- Recognized by FFIEC as reliability indicators

## Consequences

Easier:
- Board-level engineering performance reporting
- Objective comparison to industry benchmarks
- Automated measurement via CI/CD instrumentation

Harder:
- Teams must instrument pipelines for accurate measurement
- Cultural shift from output to outcome metrics

## Compliance implications

MTTR tracking directly satisfies FFIEC resilience requirements.
Change failure rate supports SOX ITGC change management controls.

## References

- DORA State of DevOps Report
- github.com/brianpelow/TeamHealthRadar
