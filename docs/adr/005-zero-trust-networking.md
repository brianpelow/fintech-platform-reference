# ADR-005: Implement zero-trust network architecture

**Status**: Accepted
**Date**: 2026-02-10
**Authors**: @brianpelow

## Context

Traditional perimeter-based security is insufficient for a cloud-native
fintech platform. Lateral movement within the network perimeter poses
significant risk for payment data.

## Decision

Implement zero-trust networking. All service-to-service communication
uses mTLS. No implicit trust based on network location. Every request
is authenticated and authorized regardless of source.

## Rationale

- Eliminates lateral movement risk for PCI-DSS cardholder data
- Satisfies FFIEC zero-trust guidance
- Enables fine-grained service authorization policies
- Reduces blast radius of any single compromised service

## Consequences

Easier:
- Audit trail for all service-to-service calls
- Granular access control per service identity
- Compliance evidence for PCI-DSS network segmentation

Harder:
- Certificate lifecycle management complexity
- Performance overhead of mTLS handshakes
- Developer experience requires service mesh tooling

## Compliance implications

Directly satisfies PCI-DSS Requirements 1, 4, and 7.
Aligns with FFIEC zero-trust architecture guidance.

## References

- NIST SP 800-207 Zero Trust Architecture
- PCI-DSS v4.0 Requirements 1 and 4
