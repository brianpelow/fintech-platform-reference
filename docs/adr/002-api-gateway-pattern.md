# ADR-002: Adopt API gateway pattern for all external traffic

**Status**: Accepted
**Date**: 2026-01-20
**Authors**: @brianpelow

## Context

The platform exposes multiple services to external clients including mobile apps,
third-party integrators, and partner banks. Without a unified entry point, each
service must independently implement authentication, rate limiting, and TLS termination.

## Decision

All external traffic must pass through the api-gateway service. No service will
expose public endpoints directly. The gateway handles TLS termination, JWT
validation, rate limiting, request logging, and routing.

## Rationale

- Single enforcement point for authentication and authorization
- Centralizes PCI-DSS network segmentation controls
- Simplifies certificate management and rotation
- Enables consistent request tracing and audit logging

## Consequences

Easier:
- Centralized auth policy enforcement
- Simplified service-to-service mTLS inside the perimeter
- Unified rate limiting and DDoS protection

Harder:
- Gateway becomes a critical P0 dependency
- Latency budget must account for gateway overhead

## Compliance implications

Satisfies PCI-DSS Requirement 1 (network access controls) and
Requirement 8 (authentication management).

## References

- PCI-DSS v4.0 Requirements 1 and 8
- FFIEC Information Security Booklet: Network Controls
