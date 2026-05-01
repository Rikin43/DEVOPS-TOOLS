# Docker Guide

## 🐳 What is Docker?

Docker is a platform that allows developers to build, package, and run applications in containers.

- **Containers include** code, runtime, libraries, and dependencies
- **Works the same** across different environments
- **Lightweight** compared to virtual machines

**Simple idea:** Run your app anywhere without "it works on my machine" issues

---

## ⚙️ Why Docker is Useful

Docker is widely used in modern development and DevOps.

- **Consistency** – Same environment in dev, test, and production
- **Fast deployment** – Containers start quickly
- **Resource efficient** – Uses fewer resources than VMs
- **Scalability** – Easily scale applications
- **Portability** – Run anywhere (local, cloud, servers)

---

## 🏗️ Docker Architecture — Overview

Docker follows a client-server architecture.

### Components

| Component | Description |
|-----------|-------------|
| **Docker Client** | Command line tool (docker) that sends commands to Docker daemon |
| **Docker Daemon** | Runs in background and manages containers, images, networks |
| **Docker Registry** | Stores Docker images (Example: Docker Hub) |
| **Docker Objects** | Images, Containers, Networks, Volumes |

### Simple Flow

```
User runs command → Client → Daemon → Executes action
```

---

## 💻 Installing Docker — Overview

### Local Machine (Laptop)

Install Docker Desktop (Windows/Mac), which includes Docker Engine, CLI, GUI, and Kubernetes.

**Verify installation:**

```bash
docker --version
docker run hello-world
```

### Linux Installation (Example: Ubuntu)

```bash
sudo apt update
sudo apt install docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### ☁️ Docker on AWS (EC2)

1. Launch EC2 instance
2. Connect using SSH
3. Install Docker

```bash
sudo yum update -y
sudo amazon-linux-extras install docker
sudo service docker start
```

**Add user:**

```bash
sudo usermod -aG docker ec2-user
```

---

## 📦 Docker Images — Overview

### What is an Image?

A Docker image is a read-only template used to create containers.

- Built using a Dockerfile
- Contains application and dependencies

### Example Dockerfile

```dockerfile
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
CMD ["node", "app.js"]
```

### Common Commands

```bash
docker build -t myapp .
docker images
docker pull nginx
```

---

## 📦 Docker Containers — Overview

### What is a Container?

A container is a running instance of an image.

- Isolated environment
- Fast startup
- Temporary by default

### Common Commands

```bash
docker run nginx
docker ps
docker stop <container_id>
docker rm <container_id>
```

---

## 🌐 Docker Networking — Overview

Docker allows containers to communicate using networks.

### Types of Networks

| Network Type | Purpose |
|--------------|---------|
| **Bridge** | Default, same host communication |
| **Host** | Uses host network |
| **None** | No network |
| **Overlay** | Multi-host networking |

### Common Commands

```bash
docker network ls
docker network create mynet
docker run --network=mynet nginx
```

---

## 💾 Docker Volumes & Storage — Overview

Containers are temporary, so data is lost when removed.

### Solution: Volumes

**Types:**
- Volumes (recommended)
- Bind mounts
- tmpfs (in-memory)

### Common Commands

```bash
docker volume create myvol
docker run -v myvol:/data nginx
```

### Use Cases

- Databases
- Logs
- Persistent data

---

## 📄 Docker Compose — Overview

Docker Compose is used to run multi-container applications.

### Example docker-compose.yml

```yaml
version: "3"
services:
  web:
    image: nginx
    ports:
      - "80:80"
  db:
    image: mysql
```

### Common Commands

```bash
docker-compose up
docker-compose down
```

---

## 📦 Docker Registry — Overview

A Docker registry stores Docker images.

### Types

| Registry Type | Example |
|---------------|---------|
| **Public** | Docker Hub |
| **Private** | AWS ECR, self-hosted |

### Common Commands

```bash
docker login
docker push myimage
docker pull myimage
```

---

## 🏗️ Multi-Stage Docker Builds — Overview

Used to create optimized and smaller images.

### Example

```dockerfile
FROM node:18 AS builder
WORKDIR /app
COPY . .
RUN npm install

FROM node:18-slim
COPY --from=builder /app /app
CMD ["node", "app.js"]
```

### Benefits

- Smaller size
- Better security
- Faster builds

---

## 📊 Monitoring & Logging in Docker — Overview

### Logging

Docker stores container logs and supports multiple log drivers.

```bash
docker logs <container_id>
```

### Monitoring

```bash
docker stats
```

### Tools

- Prometheus
- Grafana
- ELK Stack

### Metrics

- CPU usage
- Memory usage
- Network usage
- Disk usage

---

## ☸️ Kubernetes (Docker Orchestration) — Overview

Docker runs containers, but large systems need orchestration.

### What is Kubernetes?

A system for managing containerized applications.

### Key Concepts

| Concept | Description |
|---------|-------------|
| **Pod** | Smallest unit (containers) |
| **Node** | Machine running pods |
| **Cluster** | Group of nodes |
| **Deployment** | Manages replicas |
| **Service** | Exposes apps |

### Why Kubernetes?

- Auto scaling
- Load balancing
- Self-healing
- Rolling updates

---

## ⚖️ Docker vs Kubernetes — Quick Comparison

| Feature | Docker | Kubernetes |
|---------|--------|-----------|
| **Scope** | Container runtime | Orchestration |
| **Scaling** | Manual | Automatic |
| **Multi-node** | Limited | Full support |

---

## 🚀 Docker Ecosystem — Quick Summary

- **Images** → Application blueprint
- **Containers** → Running applications
- **Volumes** → Persistent storage
- **Networks** → Communication
- **Compose** → Multi-container apps
- **Registry** → Image storage
- **Kubernetes** → Orchestration
