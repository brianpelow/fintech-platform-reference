# ADR-007: Adopt SLO-based reliability management

**Status**: Accepted
**Date**: 2026-02-20
**Authors**: @brianpelow

## Context

Reliability targets are currently informal and inconsistently applied.
Incident response is reactive. There is no systematic way to balance
reliability investment against feature delivery.

## Decision

Adopt SLO-based reliability management. Every P0 and P1 service must
define SLOs with error budgets. Error budget consumption gates feature
releases. PlatformSLOBoard provides real-time visibility.

## Rationale

- Aligns reliability investment with business risk
- Provides objective basis for release gating
- Maps to FFIEC resilience and availability requirements
- Enables data-driven conversations with leadership

## Consequences

Easier:
- Objective reliability targets for P0 services
- Automated release gating based on error budget
- Board-level reliability reporting

Harder:
- SLI instrumentation required for all P0 services
- Cultural shift to error budget mindset

## Compliance implications

Directly supports FFIEC availability and resilience requirements.
Error budget policy provides evidence of risk management controls.

## References

- Google SRE Book: Service Level Objectives
- github.com/brianpelow/PlatformSLOBoard
