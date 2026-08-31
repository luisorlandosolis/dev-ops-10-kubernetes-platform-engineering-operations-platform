# Dev-Ops-10: Kubernetes Platform Engineering & Operations Platform

## Overview

Dev-Ops-10 is a platform engineering project focused on the design, deployment, operation, monitoring, and validation of a multi-node Kubernetes environment.

The project expands upon previous portfolio work in infrastructure automation, backup and recovery, and deployment operations by introducing cloud-native orchestration concepts and platform engineering practices.

Rather than serving as a simple Kubernetes lab, the platform is intended to simulate production-inspired operational practices and provide a foundation for future observability, CI/CD, and platform services.

---

## Current Status

### Completed

✅ Three-node Kubernetes cluster deployed

✅ Control Plane operational

✅ Two Worker Nodes operational

✅ containerd runtime configured

✅ Flannel networking deployed

✅ CoreDNS validated

✅ NGINX deployment validated

✅ Replica scaling validated

✅ Self-healing behavior validated

✅ Service creation and endpoint discovery validated

✅ Namespace isolation validated

✅ Multi-workload operation validated

### Current Phase

Phase 4 - Platform Networking (Ingress)

🚧 Next

### Planned

📋 Persistent Storage

📋 Observability (Grafana & Prometheus)

📋 CI/CD Integration

📋 Platform Services

---

## Portfolio Relationship

Demonstrates:

- Kubernetes Administration
- Platform Engineering
- Linux Administration
- Proxmox Virtualization
- Ubuntu Server Administration
- Container Orchestration
- Infrastructure Operations
- Platform Monitoring
- Disaster Recovery
- High Availability Concepts
- CI/CD Concepts
- Operational Runbook Development
- Observability Engineering

---

## Project Origin

Following the completion of several infrastructure-focused portfolio projects, a gap remained in cloud-native platforms and container operations.

Dev-Ops-10 was created to provide hands-on experience designing and operating a Kubernetes environment capable of supporting modern application workloads while introducing platform engineering concepts including cluster lifecycle management, workload orchestration, monitoring, resiliency testing, and service hosting.

---

## Objectives

### Primary Objectives

- Build a multi-node Kubernetes cluster
- Standardize Linux node deployment
- Implement repeatable platform operations
- Develop Kubernetes administration skills
- Establish observability capabilities
- Document operational procedures
- Validate workload resiliency

### Secondary Objectives

- Deploy monitoring platforms
- Integrate CI/CD workflows
- Implement cluster recovery procedures
- Explore GitOps concepts
- Host future application workloads

---

## Environment

### Hypervisor

- Proxmox VE

### Guest Operating System

- Ubuntu Server 24.04.4 LTS

### Cluster Architecture

- 1 Control Plane
- 2 Worker Nodes

### Platform Type

Production-inspired home lab environment.

---

## Technology Stack

### Infrastructure

- Proxmox VE
- Ubuntu Server 24.04 LTS
- QEMU Guest Agent

### Kubernetes Platform

- Kubernetes
- kubeadm
- kubelet
- kubectl
- containerd

### Networking

- Kubernetes Services
- CoreDNS
- Container Networking Interface (Future)

### Observability (Planned)

- Prometheus
- Grafana

### Platform Services (Planned)

- Helm
- Ingress Controller
- Jenkins

---

## Architecture

Current node inventory:

| VMID | Hostname | IP Address | Role |
|--------|----------|------------|--------|
| XXX | dops10-k8s-template | N/A | Golden Template |
| XXX | dops10-k8s-controlXX | 10.0.0.XX | Control Plane |
| XXX | dops10-k8s-worker-XX | 10.0.0.XX | Worker Node |
| XXX | dops10-k8s-worker-XX | 10.0.0.XX | Worker Node |

Additional architectural details are documented in:

```text
docs/architecture.md
