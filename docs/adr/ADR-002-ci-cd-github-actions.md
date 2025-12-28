# ADR-002: CI/CD with GitHub Actions

## Status
Accepted

## Context
The platform requires automated pipelines for:
- Build
- Test
- Security scanning
- Containerization
- Deployment

CI/CD must integrate tightly with GitHub repositories.

## Decision
GitHub Actions is selected as the primary CI/CD platform.

Pipelines will:
- Build Spring Boot applications
- Run unit and integration tests
- Perform SAST and dependency scanning
- Build and push Docker images
- Deploy to Kubernetes via GitOps principles

## Consequences
### Positive
- Native GitHub integration
- Declarative YAML pipelines
- Secure secrets management

### Trade-offs
- Less mature UI than some enterprise CI tools
