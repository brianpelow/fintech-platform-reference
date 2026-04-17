# ADR-001: Use event sourcing for payment state management

**Status**: Accepted
**Date**: 2026-01-15
**Authors**: @brianpelow

## Context

Payment processing requires an immutable, auditable record of all state
transitions. Traditional CRUD-based approaches make it difficult to reconstruct
the history of a payment, satisfy regulatory audit requirements, and implement
reliable distributed transaction patterns.

## Decision

Adopt event sourcing for the payments-service domain. All payment state changes
will be represented as immutable domain events stored in an append-only event store.
Current state is derived by replaying the event stream.

## Rationale

- Provides complete audit trail required by PCI-DSS and SOX
- Enables reliable distributed transaction handling via saga pattern
- Supports temporal queries for regulatory reporting
- Decouples write and read models for independent scaling

Alternatives considered:
- Two-phase commit: rejected due to availability risk and complexity
- Outbox pattern only: insufficient audit trail granularity

## Consequences

Easier:
- Complete payment audit trail for PCI-DSS compliance
- Temporal debugging and incident reconstruction
- Event-driven integration with downstream systems

Harder:
- Eventual consistency requires careful UX design
- Event schema evolution requires versioning discipline
- Team must understand event sourcing patterns

## Compliance implications

Directly satisfies PCI-DSS Requirement 10 (audit log maintenance).
Supports SOX ITGC controls for financial system change tracking.

## References

- Martin Fowler: Event Sourcing pattern
- PCI-DSS v4.0 Requirement 10.2
