# ADR-006: Use ISO 20022 for all payment messages

**Status**: Accepted
**Date**: 2026-02-15
**Authors**: @brianpelow

## Context

The global payments industry is migrating to ISO 20022 as the universal
financial messaging standard. Our correspondent banking partners and
payment rails require ISO 20022 compliance by 2025.

## Decision

All payment messages — both internal and external — will use ISO 20022
XML message formats. The payments-service will implement pacs.008
for credit transfers and pacs.002 for status reports.

## Rationale

- Regulatory requirement for SWIFT and SEPA compliance
- Richer data enables better fraud detection
- Future-proof: becoming the global standard
- Enables straight-through processing with partner banks

## Consequences

Easier:
- Compliance with correspondent banking requirements
- Richer payment data for AML and fraud screening
- Interoperability with global payment rails

Harder:
- More complex message schemas than legacy formats
- Team training required on ISO 20022 data model

## Compliance implications

Required for SWIFT gpi compliance and SEPA credit transfer scheme.
Supports AML transaction monitoring data requirements.

## References

- ISO 20022 Universal Financial Industry Message Scheme
- SWIFT gpi compliance requirements
