# CloudPaxos

## Overview

CloudPaxos is a cloud-native, distributed, sharded key-value store powered by the Paxos consensus algorithm. Designed for scalability, fault tolerance, and high availability, it is containerized and deployable on Kubernetes, making it ideal for modern cloud environments. This repository emphasizes **containerization, deployment infrastructure, and cloud-native scalability**, while leveraging existing implementations of Paxos-based consensus and sharded key-value logic.

---

## Features

- **Paxos Consensus**: Ensures consistency across distributed nodes.
- **Sharded Key-Value Store**: Dynamically manages shards for load balancing and fault recovery.
- **Cloud-Native Deployment**: Fully containerized services orchestrated via Kubernetes.
- **Monitoring & Observability**: Integrated with Prometheus, Grafana, and OpenTelemetry for real-time insights.
- **Security**: Encrypted communication between nodes with TLS and API-level authentication.

---

## Use Cases

- **Distributed Key-Value Stores**:
  - Backend storage for microservices and scalable cloud applications.
- **Consensus-Based Systems**:
  - Metadata management, leader election, and configuration management.
- **Cloud-Native Applications**:
  - Deployable in AWS, GCP, or Azure with built-in observability and scalability.
- **Fault-Tolerant State Management**:
  - Systems requiring strong consistency under network partitions or node failures.

---

## Technical Architecture

### Core Components

1. **Consensus Layer (`paxos.go`)**:
   - Implements the Paxos consensus algorithm to ensure consistent agreement across distributed replicas.
   - **Attribution**: The `paxos.go` implementation is derived from a distributed systems course project (**CS134**) at **UCLA Computer Science Department**, designed to achieve consensus within a local environment.
   - This repository adapts and extends the Paxos logic for cloud-native deployment, focusing on infrastructure and scalability.

2. **Shard Manager (`shardmanager/`)**:
   - Handles shard allocation and rebalancing across replica groups.
   - Dynamically reassigns shards during node joins, leaves, or failures to maintain even load distribution.
   - **Attribution**: The `shardmanager` logic is derived from the same CS134 project, which focused on sharded key-value storage in a local setup. This repository emphasizes deploying and scaling this service in cloud environments.

3. **Sharded Key-Value Store (`kvstore/`)**:
   - Provides a consistent distributed key-value store across shards.
   - Supports `Put`, `Get`, and `Append` operations while ensuring strong consistency.
   - **Attribution**: The `kvstore` module originates from the CS134 project’s implementation of sharded storage with Paxos-based consensus. In this repository, it is containerized and deployed to enable cloud-native scalability.

---

### Infrastructure

- **Containerization**: Dockerized services ensure portability and consistency.
- **Orchestration**: Kubernetes manages scaling, service discovery, and fault recovery.
- **CI/CD Pipelines**: GitHub Actions automates builds, tests, and deployments.
- **Monitoring and Observability**:
  - Prometheus and Grafana for real-time metrics and visualization.
  - OpenTelemetry for distributed tracing of operations.

---

## Directory Structure

```plaintext
cloudpaxos/
├── consensus/         # Paxos consensus implementation
│   ├── paxos.go       # Core Paxos logic
│   └── tests/         # Unit and integration tests for Paxos
├── shardmanager/      # ShardMaster service
│   ├── manager.go     # Logic for shard allocation and rebalancing
│   ├── common.go      # Shared data structures
│   └── tests/         # Unit and integration tests
├── kvstore/           # Sharded Key-Value Store
│   ├── store.go       # Core KV store logic
│   ├── common.go      # Shared data structures
│   └── tests/         # Unit and integration tests
├── infra/             # Infrastructure-related files
│   ├── docker/        # Dockerfiles for services
│   ├── k8s/           # Kubernetes manifests
│   └── terraform/     # Cloud provisioning scripts
├── ci/                # CI/CD pipeline configurations
├── docs/              # Documentation
│   ├── README.md      # Project overview and instructions
│   └── architecture.md # Detailed technical design
└── tests/             # End-to-end and integration tests
```

---

## Getting Started

### Prerequisites

- **Docker**: Ensure Docker is installed for containerization.
- **Kubernetes**: Install `kubectl` and configure access to a Kubernetes cluster.
- **Prometheus & Grafana**: Optionally set up for monitoring and observability.

### Setup Instructions

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/cloudpaxos.git
   cd cloudpaxos
   ```

2. **Build Docker Images**:
   ```bash
   docker-compose build
   ```

3. **Deploy to Kubernetes**:
   ```bash
   kubectl apply -f infra/k8s/
   ```

4. **Monitor the System**:
   - Access Prometheus and Grafana for system metrics and visualization.

---

## License

This project is licensed under the MIT License.
