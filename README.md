
# CloudPaxos

## Overview

CloudPaxos is a cloud-native, distributed, sharded key-value store powered by the Paxos consensus algorithm. Designed for scalability, fault tolerance, and high availability, it is containerized and deployable on Kubernetes, making it ideal for modern cloud environments.

## Features

- **Paxos Consensus**: Ensures consistency across distributed nodes.
- **Sharded Key-Value Store**: Dynamically manages shards for load balancing.
- **Cloud-Native Deployment**: Fully containerized with Docker and orchestrated via Kubernetes.
- **Monitoring & Observability**: Integrated with Prometheus, Grafana, and OpenTelemetry.
- **Security**: Encrypted inter-node communication and API-level authentication.

## Use Cases

- High-performance distributed key-value stores for cloud-native applications.
- Consensus-based systems like configuration management and metadata storage.
- Fault-tolerant, stateful applications requiring strong consistency.

## Technical Architecture

### Core Components

1. **Consensus Layer (Paxos)**: Manages distributed consensus for operation ordering.
2. **Shard Manager (ShardMaster)**: Dynamically allocates and rebalances shards.
3. **Sharded Key-Value Store (ShardKV)**: Implements a consistent distributed key-value store.

### Infrastructure

- **Containerization**: Dockerized services for portability.
- **Orchestration**: Kubernetes for scaling and fault tolerance.
- **CI/CD**: Automated pipelines with GitHub Actions.

## Directory Structure

```plaintext
cloudpaxos/
├── consensus/         # Paxos consensus implementation
├── shardmanager/      # ShardMaster service
├── kvstore/           # Sharded Key-Value store
├── infra/             # Docker, Kubernetes, and Terraform files
├── ci/                # CI/CD pipeline scripts
├── docs/              # Documentation
└── tests/             # End-to-end and unit tests
```

## Origins and Attribution

The `paxos.go` implementation originates from a distributed systems course project (**CS134**) at **UCLA Computer Science Department**. CloudPaxos extends this foundation with cloud-native deployment, shard rebalancing, and modern distributed systems practices.

## Getting Started

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
   - Access Prometheus and Grafana for metrics and visualization.

## License

This project is licensed under the [MIT License](LICENSE).
