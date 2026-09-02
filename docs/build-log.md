# Build Log

## Project

Dev-Ops-10: Kubernetes Platform Engineering & Operations Platform

---

# Session 01

## Infrastructure Foundation

Date: August 2026

---

## Project Purpose

Dev-Ops-10 was created to address the next major portfolio area following infrastructure automation, backup and recovery, and deployment operations.

Key focus areas include:

- Container Platforms
- Kubernetes
- Platform Engineering
- Cloud-Native Operations
- Observability
- CI/CD

Rather than building a simple Kubernetes lab, the project focuses on designing, deploying, operating, monitoring, and validating a multi-node Kubernetes platform hosted on virtualized infrastructure.

---

## Current Architecture

### Hypervisor

- Proxmox VE

### Planned Kubernetes Cluster

- Control Plane: 1
- Worker Nodes: 2

---

## Node Inventory

### Kubernetes Template

Hostname:

```text
k8s-template
```

Role:

```text
Golden Image
```

---

### Control Plane Node

Hostname:

```text
k8s-control-01
```

Role:

```text
Kubernetes Control Plane
```

---

### Worker Node 01

Hostname:

```text
k8s-worker-01
```

Role:

```text
Kubernetes Worker
```

---

### Worker Node 02

Hostname:

```text
k8s-worker-02
```

Role:

```text
Kubernetes Worker
```

---

## Golden Image Strategy

Created a reusable Linux golden image.

Purpose:

- Linux Golden Image
- Future Clone Source
- Kubernetes Baseline

Potential future clones include:

- Worker Nodes
- Utility Nodes
- CI/CD Nodes
- Testing Nodes
- Platform Services

Result:

✅ Reusable deployment baseline established

---

## Template Configuration

### Operating System

```text
Ubuntu Server LTS
```

### Baseline Configuration

- Virtualized Infrastructure
- UEFI Boot
- VirtIO Storage
- VirtIO Networking
- QEMU Guest Agent

Result:

✅ Standardized deployment template established

---

## Ubuntu Configuration

### Installed

- OpenSSH Server

### Intentionally Excluded

- MicroK8s
- Docker
- Additional Platform Services
- Monitoring Components

Reason:

Maintain a clean Kubernetes deployment baseline.

---

## Base Tooling

Installed:

- qemu-guest-agent
- curl
- wget
- git
- vim
- htop
- net-tools

Validation:

```bash
systemctl status qemu-guest-agent
```

Result:

```text
Running
```

✅ Baseline administrative tooling installed

---

## Kubernetes Preparation

Swap disabled to satisfy Kubernetes requirements.

Validation:

```bash
free -h
```

Result:

```text
Swap: 0B
```

Persistent configuration updated to maintain compatibility across reboots.

Result:

✅ Kubernetes prerequisite completed

---

## Clone Validation

Created initial control plane node from the template.

Validation performed to confirm:

- Independent storage allocation
- Separation from template source
- Clone persistence
- Template preservation

Result:

✅ Full clone strategy validated

---

## Network Engineering

Reviewed initial DHCP configuration prior to implementing static addressing.

Validation activities included:

- Route validation
- Gateway verification
- SSH connectivity testing
- Address planning

Result:

✅ Network assumptions validated before implementation

---

## Static Address Strategy

Defined static addressing plan for:

- Control Plane Node
- Worker Node 01
- Worker Node 02

Validation methods:

- Address availability testing
- Route validation
- Connectivity verification

Result:

✅ Static networking strategy validated

---

## Control Plane Configuration

Completed:

- Hostname assignment
- Static network configuration
- Gateway configuration
- DNS configuration
- SSH enablement
- Remote administration validation

Validation:

```bash
hostname
hostname -I
ip route
```

Results:

✅ Hostname validated

✅ Static networking operational

✅ Routing functional

✅ SSH connectivity successful

Result:

✅ Control plane node operational

---

## Milestone Status

### Phase 1 - Infrastructure Foundation

✅ Complete

---

# Session 02

## Kubernetes Cluster Formation

Date: August 2026

### Objective

Deploy and validate a functional multi-node Kubernetes cluster.

---

## Container Runtime Deployment

Installed:

- containerd

Configuration:

```text
SystemdCgroup = true
```

Validation:

✅ containerd operational on all cluster nodes

---

## Kubernetes Components Installation

Installed:

- kubelet
- kubeadm
- kubectl
- kubernetes-cni

Version:

```text
v1.34.11
```

Result:

✅ Kubernetes components installed successfully

---

## Kubernetes Control Plane Initialization

Successfully initialized the Kubernetes control plane using kubeadm.

Core Components Created:

- Kubernetes API Server
- Scheduler
- Controller Manager
- etcd

Result:

✅ Control Plane Operational

---

## Cluster Bootstrap Configuration

Generated:

- Cluster join token
- kubeadm join command
- Bootstrap configuration

Result:

✅ Worker node onboarding enabled

---

## Cluster Networking

Installed:

- Flannel CNI

Validation:

CoreDNS successfully transitioned from Pending to Running status.

Result:

✅ Pod networking operational

---

## Worker Node Integration

Successfully joined:

- Worker Node 01
- Worker Node 02

Validation:

```bash
kubectl get nodes
```

Result:

```text
Control Plane Ready
Worker Node 01 Ready
Worker Node 02 Ready
```

Result:

✅ Three-node cluster operational

---

## First Workload Deployment

Deployed:

```text
NGINX
```

Validation:

```bash
kubectl get deployments
kubectl get pods -o wide
```

Observed:

- Deployment created successfully
- Pod scheduled automatically
- Workload running normally

Learning Outcome:

Kubernetes determines workload placement automatically through the scheduler.

---

## Major Learning Milestones

### Component Roles

containerd

```text
Container Runtime
```

kubelet

```text
Node Agent
```

kubeadm

```text
Cluster Bootstrap Tool
```

kubectl

```text
Cluster Administration CLI
```

API Server

```text
Cluster Entry Point
```

Scheduler

```text
Workload Placement Engine
```

Controller Manager

```text
Desired State Enforcement
```

etcd

```text
Cluster Database
```

Flannel

```text
Pod Networking
```

CoreDNS

```text
Cluster DNS
```

---

## Mental Breakthrough

Recognized common operational patterns:

Terraform

```text
Desired Infrastructure
```

Ansible

```text
Desired Configuration
```

Kubernetes

```text
Desired Applications
```

KrakkenOS

```text
Desired Asset Operations
```

Result:

✅ Desired State Architecture Concept Understood

---

## Current Status

### Completed

- Platform Foundation
- Kubernetes Cluster Formation
- Container Runtime Installation
- Control Plane Initialization
- Worker Node Integration
- Flannel Deployment
- CoreDNS Validation
- First Workload Deployment

### In Progress

- Kubernetes Workloads
- Services
- Scheduler Observation
- Self-Healing Validation

### Next Steps

- Scale NGINX
- Deploy Services
- Test Pod Recovery
- Test Node Drain Operations
- Explore ReplicaSets
- Explore Deployments

---

## Current Milestone

### Phase 3 - Kubernetes Workloads & Services

🚧 In Progress
---

# Session 03

## Workloads, Services, Self-Healing, and Namespaces

Date: August 2026

### Objective

Move beyond cluster formation and begin operating Kubernetes as a platform.

---

## Replica Scaling Validation

Validation:

```bash
kubectl scale deployment nginx --replicas=5

Result:

✅ Replica scaling validated

Learning:

```text
Deployment
= Blueprint

ReplicaSet
= Enforcer
```

---

## Self-Healing Validation

Result:

✅ Self-healing behavior validated

Learning:

```text
Desired State
>
Individual Pod
```

---

## Service Validation

Result:

✅ Service architecture validated

Learning:

```text
Service
= Stable Identity

Service
= Front Door
```

---

## Namespace Validation

Created:

```text
monitoring
```

Result:

✅ Namespace isolation validated

Learning:

```text
Namespace
= Compartment
```

---

## Multi-Workload Validation

Environment:

```text
default
└─ nginx

monitoring
└─ nginx-monitor
```

Result:

✅ Multi-workload operation validated

---

## Major Architecture Realizations

```text
Terraform
= Desired Infrastructure

Ansible
= Desired Configuration

Kubernetes
= Desired Applications

KrakkenOS
= Desired Asset Operations
```

---

## Current Status

### Completed

- Infrastructure Foundation
- Cluster Formation
- Workloads
- Scaling
- Self-Healing
- Services
- Namespaces

### Next Phase

- Ingress
- Persistent Storage
- Observability
- CI/CD

---

# Session 04

## Ingress, Namespace Architecture, and Storage Planning

Date: August 2026

### Objective

Transition from Kubernetes fundamentals into platform architecture, ingress, storage strategy, and CI/CD planning.

---
## Namespace Architecture

Created:

```text
monitoring
cicd
ingress
```

Current organization:

```text
default
monitoring
cicd
ingress
```

Learning:

```text
Namespace
= Department

Namespace
= Blast Radius Boundary
```

Major realization:

```text
Not Everything Needs To Break.
```

Result:

✅ Multi-namespace architecture validated

---

## Ingress Controller Deployment

Installed:

```text
ingress-nginx
```

Validation:

```bash
kubectl get pods -n ingress-nginx
```

Observed:

```text
ingress-nginx-controller
Running
```

Result:

✅ Ingress controller operational

---
## First Ingress Rule

Implemented:

```text
nginx.lab.local
```

Traffic Flow:

```text
DNS
↓
Ingress
↓
Service
↓
Pods
```

Learning:

```text
Ingress
= Reception Desk

Service
= Front Door

Pods
= Workers
```

Result:

✅ Host-based routing concept validated

---

## Storage Architecture Investigation

Instead of deploying Jenkins immediately, storage architecture was reviewed first.

Primary Storage:

```text
/mnt/externalbackup

Approx. 1.9 TB
```

Replication Storage:

```text
/srv/storage

RAID1-STORAGE
Approx. 1.8 TB
```

Learning:

```text
Application
≠
Data

Pod
≠
Storage
```

Result:

✅ Storage-first platform design approach established

---
## Jenkins Storage Decision

Preferred architecture:

```text
Jenkins
↓
PVC
↓
Drive A
↓
RAID Replication
↓
Archive
↓
Cloud
```

Learning:

```text
Backup Strategy

Must Be Designed

Before Application Deployment
```

Result:

✅ Backup-aware platform design established

---

## Harbor Planning

Future namespace:

```text
cicd
```

Planned services:

```text
Jenkins
Harbor
```

Target Architecture:

```text
cicd
├── Jenkins
└── Harbor
```

Result:

✅ CI/CD platform architecture defined

---

## Major Architecture Realizations

```text
Deployment
= Blueprint

Pod
= Worker

Service
= Front Door

Namespace
= Department

Ingress
= Reception Desk
```

Learning:

```text
Application
≠
Data

Pod
≠
Storage

Recovery
Should Be Designed
Before Deployment
```

---

## Next Session

1. Verify RAID health
2. Review storage architecture
3. Learn Persistent Volumes (PV)
4. Learn Persistent Volume Claims (PVC)
5. Deploy Jenkins with persistent storage
6. Configure Jenkins ingress
7. Plan Harbor deployment

### Future Platform Vision

```text
Dev-Ops-10
│
├── ingress
│   └── ingress-nginx
│
├── cicd
│   ├── Jenkins
│   └── Harbor
│
├── automation
│   ├── Ansible
│   └── Terraform
│
├── networking
│   └── Bastion
│
├── krakken
│   ├── Inventory
│   ├── Knowledge
│   └── Lifecycle
│
└── monitoring
    ├── Grafana
    └── Prometheus
```
---

# Session 05

## Jenkins, Persistent Storage, and First CI/CD Validation

Date: September 2026

### Objective

Deploy a real application on Kubernetes, investigate persistent storage concepts, validate ingress routing, and execute the first Jenkins pipeline.

---
## Kubernetes Storage Investigation

Created dedicated storage locations for future Kubernetes workloads.

Conceptual structure:

```text
Kubernetes
├── Jenkins
└── Harbor
```

Validated:

```text
✅ Shared storage accessible

✅ SMB connectivity validated

✅ Linux mount validation completed

✅ Cross-platform access confirmed
```

Learning:

```text
Storage
Must Be Designed

Before
Application Deployment
```

---
## PV / PVC Learning

Successfully created:

```text
jenkins-pv

jenkins-pvc
```

Observed lifecycle:

```text
Available
↓
Bound
```

Learning:

```text
PV
= Storage Room

PVC
= Reserved Filing Cabinet
```

Alternative Mental Model:

```text
PV
= Parking Lot

PVC
= Reserved Parking Spot
```

Result:

✅ Persistent storage concepts validated

---

## HostPath Failure Analysis

Initial design:

```yaml
hostPath:
  path: /mnt/kubernetes-share/Jenkins
```

Observed:

```text
PVC Bound ✅

Jenkins Failed ❌
```

Investigation:

```text
Control Plane
└── SMB Mounted

Worker-02
└── Jenkins Pod
```

Discovery:

```text
hostPath
=
Node Storage

NOT

Cluster Storage
```

Learning:

```text
Networking
≠
Storage
```

A node may have network connectivity while lacking access to the underlying storage path.

Result:

✅ Storage architecture limitation identified

---

## Storage Architecture Direction

Future storage should leverage cluster-shared storage mechanisms such as:

```text
SMB CSI Driver

or

NFS

or

Cluster-Wide Shared Storage
```

Avoid relying on:

```text
hostPath
```

for production-style shared workloads.

Result:

✅ Future storage architecture defined

---

## Jenkins Deployment Success

To continue storage troubleshooting independently from application deployment, Jenkins was temporarily deployed without persistent storage.

Created:

```text
Deployment

Service

Ingress
```

Architecture:

```text
Jenkins Pod
↓
Service
↓
Ingress
```

Observed:

```text
Jenkins Pod
Running
```

Result:

✅ Jenkins successfully deployed on Kubernetes

---

## Service Learning

Created:

```text
jenkins Service
```

Learning:

```text
Service
=
Permanent Phone Number
```

Service survives pod recreation and provides a stable application endpoint.

Result:

✅ Service concept validated

---

## Ingress Learning

Created:

```text
jenkins-ingress
```

Learning:

```text
Ingress
=
Reception Desk
```

Traffic Flow:

```text
Host Header
↓
Ingress
↓
Service
↓
Pod
```

Result:

✅ Ingress routing concept validated

---

## Browser Troubleshooting

Observed:

```text
404 Not Found
```

Initial Assumption:

```text
Ingress Failure
```

Actual Discovery:

```text
Ingress Working ✅

Host Header Mismatch ❌
```

Learning:

```text
Ingress
Requires
Hostname Matching
```

Result:

✅ Ingress troubleshooting skills improved

---
## Jenkins Dashboard Success

Successfully reached:

```text
Jenkins Setup Wizard
```

Completed:

```text
Suggested Plugin Installation

Administrative User Creation

Initial Configuration
```

Reached:

```text
Jenkins Dashboard
```

Result:

✅ Jenkins operational and accessible through the Kubernetes platform

---

## First Pipeline Success

Created:

```text
hello-world
```

Executed:

```text
Build #1
```

Observed:

```text
SUCCESS
```

Learning:

```text
Jenkins
=
Robot Arm
```

Purpose:

```text
Build

Test

Deploy

Automate
```

Result:

✅ First Jenkins pipeline executed successfully

---

## Mental Models Learned

```text
Git
= History Book

Jenkins
= Robot Arm

Harbor
= Warehouse

Kubernetes
= Workers

Service
= Phone Number

Ingress
= Reception Desk

PV
= Storage Room

PVC
= Reserved Filing Cabinet
```

---

## Current Cluster Status

```text
✅ Kubernetes Cluster

✅ Ingress Controller

✅ NGINX Test Application

✅ Monitoring Test Application

✅ Jenkins Deployment

✅ Jenkins Service

✅ Jenkins Ingress

✅ DNS / Hosts Resolution

✅ Jenkins Dashboard

✅ First Pipeline Success
```

---

## Recommended Resume Point

Continue from:

```text
Jenkins Dashboard
```

Next objectives:

```text
1. Explore Jenkins UI

2. Understand Pipeline Stages

3. Connect GitHub

4. Create Git-Based Pipeline

5. Learn Build History

6. Deploy Harbor

7. Revisit Persistent Storage

8. Implement Shared Storage Architecture

9. Complete:

Git
↓
Jenkins
↓
Harbor
↓
Kubernetes
```

---

## Major Takeaway

The most important lesson of the session was:

```text
Networking
≠
Storage
```

Kubernetes networking succeeded because a complete path existed:

```text
Ingress
↓
Service
↓
Pod
```

Storage failed because no cluster-wide storage path existed:

```text
Worker Node
↓
PVC
↓
hostPath
↓
Control Plane Mount

❌ Not Shared Across Nodes
```

Result:

✅ Platform architecture understanding significantly improved

---

