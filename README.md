# ✈️ Aero DevSecOps Platform

> Enterprise-grade DevSecOps & SRE platform built with **Spring Boot**, **Kubernetes**, **AWS**, **Terraform**, **Ansible** and **GitHub Actions**.

---

## 🎯 Project Purpose

This project is a **production-grade DevSecOps portfolio** designed to demonstrate **end-to-end ownership** of cloud-native platforms, from **architecture and infrastructure** to **CI/CD, security, reliability and operations**.

It simulates a **mission-critical airline platform**, inspired by real-world constraints found in large international enterprises (availability, scalability, security, controlled releases).

The goal is not the business logic itself, but **how the platform is built, secured, deployed, monitored and operated**.

---

## 🧠 Key Objectives

- Design **enterprise-level cloud architecture**
- Implement **DevSecOps practices by default**
- Build **resilient CI/CD pipelines**
- Apply **Site Reliability Engineering (SRE)** principles
- Automate **everything possible**
- Document decisions as in real corporate programs

---

## 🏗️ High-Level Architecture

### System Overview

- **Microservices architecture** based on Spring Boot
- **AWS EKS** as container orchestration platform
- **Infrastructure as Code** using Terraform
- **Configuration & operational automation** using Ansible
- **CI/CD pipelines** powered by GitHub Actions
- **Observability-first design** (metrics, logs, alerts)

### Microservices

| Service | Description |
|------|------------|
| `booking-service` | Handles flight booking logic |
| `pricing-service` | Dynamic pricing & fare calculation |
| `notification-service` | Email / event notifications |
| `user-profile-service` | Passenger profile management |

All services are:
- Stateless
- REST-based
- 12-factor compliant
- Exposing health & metrics via Spring Boot Actuator

---

## ☁️ Cloud & Infrastructure

### Cloud Provider
- **AWS**

### Core Components
- VPC (Multi-AZ)
- EKS (Kubernetes)
- ECR (Container Registry)
- ALB Ingress Controller
- IAM Roles for Service Accounts (IRSA)

### Environments
- `dev`
- `staging`
- `prod`

Each environment is **fully isolated**, reproducible and managed via Terraform.

---

## 🧱 Infrastructure as Code

### Terraform
- Modular architecture
- Remote backend (S3 + DynamoDB locking)
- Environment-based configuration
- Reusable enterprise-style modules

**Terraform manages:**
- Networking
- Kubernetes cluster
- IAM
- Container registry
- Monitoring stack

---

## 🔧 Configuration & Automation

### Ansible

Ansible is used for **post-provisioning and operational automation**, complementing Terraform:

- Validation of infrastructure state
- Kubernetes operational tasks
- Environment configuration checks
- Automated remediation jobs triggered from CI/CD
- Platform consistency enforcement

> This demonstrates the correct separation of concerns:
> - Terraform → infrastructure lifecycle
> - Ansible → configuration & operations

---

## 🔄 CI/CD – GitHub Actions

### CI/CD Principles
- Fully automated pipelines
- Security integrated at every stage
- Progressive delivery strategies
- No static credentials (OIDC with AWS)

### Pipeline Stages
1. Build & unit tests (Maven)
2. Dependency & container security scans
3. Docker image build
4. Push image to Amazon ECR
5. Helm-based deployment to EKS
6. Canary deployment
7. Automated rollback on failure
8. Post-deployment Ansible jobs

### Deployment Strategies
- Canary releases
- Manual approval gates for production
- Environment-specific configurations

---

## 🔐 DevSecOps by Design

Security is not an afterthought.

### Implemented Controls
- Dependency vulnerability scanning
- Container image scanning
- Secure secrets management
- Least-privilege IAM
- Kubernetes RBAC
- Secure CI/CD pipelines

---

## 📊 Observability & SRE

### Monitoring
- Prometheus
- Grafana
- Alertmanager

### Logging
- Fluent Bit
- Elasticsearch
- Kibana

### SRE Practices
- Defined SLI / SLO per service
- Error budgets
- Incident runbooks
- Capacity planning considerations
- Reliability-focused deployment strategies

---

## 📚 Documentation & Architecture Decisions

All architectural decisions are documented following **ADR (Architecture Decision Records)** methodology.

docs/\
├── architecture.md\
├── ci-cd.md\
├── security.md\
├── sre.md\
├── adr/\
└── runbooks/

This reflects **real enterprise engineering practices**.

---

## 📁 Repository Structure

aero-devsecops-platform/ \
├── services/ **Spring Boot microservices** \
├── terraform/ **Infrastructure as Code** \
│ ├── modules/ \
│ └── envs/ \
├── ansible/ **Operational automation** \
├── helm/ **Kubernetes deployment** \
├── .github/workflows/ **GitHub Actions pipelines** \
├── docs/ **Architecture & ops documentation** \
└── README.md

## 🎯 Skills Demonstrated (Mapped to Enterprise DevOps Roles)

- Cloud architecture (AWS)
- Kubernetes at scale
- CI/CD automation
- Infrastructure as Code
- DevSecOps practices
- Site Reliability Engineering
- Production-grade documentation
- Operational excellence mindset

---

## 🚀 Why This Project Exists

This repository reflects **how modern DevOps & SRE teams operate in large, mission-critical organizations**:
- Strong governance
- Automation-first culture
- Security and reliability embedded in every layer
- Clear documentation and accountability

---

## 📌 Status

🚧 Work in progress – built incrementally as a real platform.

---

## 📄 License
Mostefaoui Nadjim
