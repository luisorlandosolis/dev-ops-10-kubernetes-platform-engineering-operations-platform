# Dev-Ops-10: Kubernetes Platform Engineering & Operations Platform

## Overview

Dev-Ops-10 is a platform engineering project focused on the design, deployment, operation, monitoring, and validation of a multi-node Kubernetes environment hosted on Proxmox VE.

The project expands upon previous portfolio work in infrastructure automation, backup and recovery, and deployment operations by introducing cloud-native infrastructure, container orchestration, observability, workload resiliency, and platform operations.

Rather than serving as a simple Kubernetes lab, the platform is intended to simulate production-inspired operational practices and provide a foundation for future service hosting.

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
| 105 | dops10-k8s-template | N/A | Golden Template |
| 106 | dops10-k8s-control-01 | 192.168.1.210 | Control Plane |
| 107 | dops10-k8s-worker-01 | 192.168.1.211 | Worker Node |
| 108 | dops10-k8s-worker-02 | 192.168.1.212 | Worker Node |

Additional architectural details are documented in:

```text
docs/architecture.md
