# ADR-003: Use Backstage as engineering system of record

**Status**: Accepted
**Date**: 2026-01-25
**Authors**: @brianpelow

## Context

As the platform grows, engineers struggle to discover services, understand
ownership, find documentation, and onboard to new teams. There is no single
source of truth for the engineering system inventory.

## Decision

Adopt Backstage as the engineering system of record. All services must have
a catalog-info.yaml file. TechDocs are served from Backstage. The service
catalog is kept fresh via service-catalog-sync nightly automation.

## Rationale

- Industry standard developer portal with strong ecosystem
- Catalog-as-code fits existing GitOps practices
- Plugin ecosystem covers most platform integrations
- service-catalog-sync automates catalog maintenance

## Consequences

Easier:
- Service discovery and ownership resolution
- Onboarding time reduction
- Compliance inventory for audit evidence

Harder:
- Teams must maintain catalog-info.yaml files
- Backstage itself becomes a platform dependency

## Compliance implications

Provides inventory evidence for SOX ITGC and FFIEC system inventory controls.

## References

- github.com/brianpelow/mcp-developer-portal
- github.com/brianpelow/service-catalog-sync
