# ADR-008: Use LangGraph for agentic incident response

**Status**: Accepted
**Date**: 2026-03-01
**Authors**: @brianpelow

## Context

Incident response is slow, inconsistent, and dependent on individual
engineer knowledge. Mean time to acknowledge and mean time to restore
are above FFIEC resilience targets. Post-mortems are inconsistently
documented.

## Decision

Adopt LangGraph-based multi-agent incident response via IncidentPilot.
Agents autonomously triage severity, retrieve runbooks, page on-call,
and draft post-mortems. Human engineers retain final authority.

## Rationale

- Reduces MTTA from minutes to seconds for alert classification
- Consistent runbook retrieval regardless of on-call experience level
- Automated post-mortem drafts improve documentation compliance
- LangGraph provides deterministic agent orchestration

## Consequences

Easier:
- Consistent incident response regardless of on-call engineer
- Automated post-mortem evidence for compliance audits
- Faster MTTA improves FFIEC resilience metrics

Harder:
- AI agent outputs require human review before action
- Anthropic API dependency for agent intelligence

## Compliance implications

Automated post-mortems provide FFIEC incident documentation evidence.
Agent audit trails satisfy SOX ITGC change and incident controls.

## References

- github.com/brianpelow/IncidentPilot
- github.com/brianpelow/mcp-incident-intel
