# 🏗️ Architecture – Aero DevSecOps Platform

## 1. Overview

The **Aero DevSecOps Platform** is a cloud-native, enterprise-grade platform designed to demonstrate **end-to-end DevSecOps and Site Reliability Engineering (SRE) practices**.

It simulates a **mission-critical airline system**, focusing on **architecture quality, security, automation, reliability and operational excellence**, rather than business complexity.

This document describes the **high-level architecture**, key components, responsibilities, and architectural decisions.

---

## 2. Architectural Goals

The platform is designed with the following goals:

- High availability and fault tolerance
- Secure-by-design architecture
- Fully automated CI/CD pipelines
- Infrastructure as Code (IaC)
- Clear separation of concerns
- Observability-first and SRE-driven operations
- Enterprise-level governance and security

---

## 3. System Context (C4 – Level 1)

### Actors
- External clients (Web / Mobile applications)
- DevOps & SRE engineers
- Product development teams
- AWS Cloud Platform

### System
- **Aero DevSecOps Platform**

The platform exposes APIs to external clients while being operated internally by DevSecOps and SRE teams.

---

## 4. Container Architecture (C4 – Level 2)

### Core Components

- **GitHub**  
  Source code management and collaboration.

- **GitHub Actions**  
  CI/CD engine handling build, test, security scans, deployments and operational automation.

- **Amazon ECR**  
  Container image registry for versioned Docker images.

- **Amazon EKS (Kubernetes)**  
  Container orchestration platform hosting all application services.

- **Spring Boot Microservices**
  - booking-service
  - pricing-service
  - notification-service
  - user-profile-service

- **Observability Stack**
  - Prometheus
  - Alertmanager
  - Grafana
  - Fluent Bit
  - Elasticsearch
  - Kibana

---

## 5. Infrastructure Architecture (C4 – Level 3)

### AWS Components

- **VPC (Multi-AZ)**
- **Public Subnets**
  - Application Load Balancer (ALB)
- **Private Subnets**
  - EKS Worker Nodes
- **Amazon ECR**
- **IAM (IRSA)**
- **AWS Secrets Manager**
- **S3 + DynamoDB**
  - Terraform remote state and locking

The architecture is designed to tolerate availability zone failures and to scale horizontally.

---

## 6. CI/CD Architecture

### Pipeline Flow

1. Code pushed to GitHub (feature / develop / main branches)
2. GitHub Actions triggered
3. Build & unit tests (Maven)
4. Dependency and container image security scans
5. Docker image build
6. Image pushed to Amazon ECR
7. Deployment to EKS using Helm
8. Canary deployment strategy applied
9. Post-deployment operational checks executed via Ansible
10. Notifications sent to collaboration channels

### Authentication & Security

- GitHub Actions authenticates to AWS using **OIDC and short-lived credentials**
- No static AWS credentials stored in CI/CD
- Principle of least privilege enforced

---

## 7. Infrastructure as Code

### Terraform Responsibilities

Terraform is responsible for **infrastructure lifecycle management**, including:

- Networking (VPC, subnets, routing)
- Kubernetes cluster (EKS)
- IAM roles and policies
- Container registry (ECR)
- Observability infrastructure

Terraform uses:
- Remote backend (S3)
- State locking (DynamoDB)
- Modular, reusable design

---

## 8. Configuration & Operational Automation

### Ansible Responsibilities

Ansible complements Terraform and is used for **procedural and operational automation**, such as:

- Post-deployment validation
- Configuration consistency checks
- Kubernetes operational tasks
- Automated remediation workflows
- Drift detection

This enforces a clear separation:
- **Terraform provisions**
- **Ansible operates**

---

## 9. Kubernetes Architecture

### Deployment Model

- Helm charts per service
- Environment-specific values
- Rolling and canary deployments

### Kubernetes Features

- Horizontal Pod Autoscaling (HPA)
- Pod Disruption Budgets (PDB)
- Liveness and readiness probes
- Network policies
- Resource limits and requests

---

## 10. Security Architecture (DevSecOps)

Security is integrated at every layer:

- CI/CD security scanning (dependencies and images)
- Secure secrets management using AWS Secrets Manager
- IAM Roles for Service Accounts (IRSA)
- Kubernetes RBAC
- Admission control and policy enforcement (OPA / Gatekeeper – conceptually)

No secrets are stored in Git repositories or container images.

---

## 11. Observability & SRE

### Monitoring
- Metrics collected via Prometheus
- Dashboards built in Grafana
- Alerts managed by Alertmanager

### Logging
- Centralized logging using Fluent Bit and Elasticsearch
- Log visualization in Kibana

### SRE Practices
- Defined SLIs and SLOs per service
- Error budgets influencing release decisions
- Incident response runbooks
- Capacity planning considerations

---

## 12. Resilience & Reliability

- Multi-AZ deployment
- Stateless services
- Horizontal scaling
- Canary deployments to reduce blast radius
- Backup and disaster recovery strategies documented

---

## 13. Architectural Principles

- Automation first
- Security by design
- Reliability over velocity
- Observability as a requirement
- Clear ownership and accountability

---

## 14. Future Enhancements

- Chaos engineering experiments
- Advanced policy enforcement
- Multi-region disaster recovery
- Service mesh evaluation

---

## 15. Conclusion

This architecture reflects **real-world enterprise DevSecOps and SRE practices**, designed to operate highly available, secure and scalable platforms in regulated and mission-critical environments.

