# ADR-003: Infrastructure as Code Strategy

## Status
Accepted

## Context
Infrastructure must be reproducible, auditable and automated.

Manual provisioning is error-prone and does not scale.

## Decision
- Terraform is used for cloud infrastructure provisioning
- Ansible is used for configuration management and operational tasks
- Git is the single source of truth

## Consequences
### Positive
- Full traceability of infrastructure changes
- Repeatable and consistent environments
- Easier disaster recovery

### Trade-offs
- Requires discipline in state management
- Learning curve for contributors
