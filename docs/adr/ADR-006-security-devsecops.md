# ADR-006: DevSecOps & Security Controls

## Status
Accepted

## Context
Security must be embedded across the SDLC.

The platform handles sensitive data and must meet enterprise security standards.

## Decision
Security controls are applied at every layer:
- Code scanning (SAST)
- Dependency scanning
- Container image scanning
- IaC scanning
- Secrets management
- RBAC and least privilege

## Consequences
### Positive
- Reduced security risks
- Early vulnerability detection
- Compliance-ready architecture

### Trade-offs
- Increased pipeline duration
- Additional tooling to manage
