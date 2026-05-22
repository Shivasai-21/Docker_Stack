# Docker Swarm Multi-Service Stack with NGINX Reverse Proxy

A production-style multi-service application deployed using Docker Swarm Stack with NGINX Reverse Proxy, Overlay Networking, Secrets Management, Resource Constraints, Persistent Volumes, and Service Replication.

---

# 📌 Project Overview

This project demonstrates how multiple containerized applications can be orchestrated using Docker Swarm and exposed through a centralized NGINX Reverse Proxy.

The stack contains:

- 🚌 Bus Booking Service
- 🎬 Movie Booking Service
- ✈️ Flight Booking Service
- 🌐 NGINX Reverse Proxy

All services are deployed as Docker Swarm services and communicate internally using an Overlay Network.

---

# 🚀 Technologies Used

- Docker
- Docker Swarm
- Docker Stack
- Docker Compose
- NGINX
- Overlay Networking
- Docker Secrets
- Persistent Volumes

---

# 📂 Project Structure

```bash
Docker_Stack_Project/
│
├── README.md
├── compose.yml
│
├── app1/
│   ├── Dockerfile
│   └── index.html
│
├── app2/
│   ├── Dockerfile
│   └── index.html
│
├── app3/
│   ├── Dockerfile
│   └── index.html
│
├── nginx/
│   └── nginx.conf
│
└── secrets/
    ├── api_key.txt
    ├── db_password.txt
    └── flight_token.txt
```

---

# ⚙️ Features Implemented

## ✅ Docker Swarm Stack Deployment
Multi-service orchestration using Docker Stack.

## ✅ NGINX Reverse Proxy
Routes incoming traffic to backend services.

## ✅ Overlay Networking
Secure internal communication between swarm services.

## ✅ Replicated Services
High availability using multiple container replicas.

## ✅ Docker Secrets
Secure management of sensitive information.

## ✅ Persistent Volumes
Attached volumes for persistent storage.

## ✅ Resource Constraints
CPU and memory limits configured for optimized resource allocation.

## ✅ Restart Policies
Automatic restart and recovery for failed containers.

---

# 🌐 Reverse Proxy Routing

| Route | Service |
|------|------|
| `/bus/` | Bus Booking Service |
| `/movie/` | Movie Booking Service |
| `/flight/` | Flight Booking Service |

---

# 🔧 NGINX Reverse Proxy Configuration

Example reverse proxy configuration:

```nginx
location /movie/ {
    proxy_pass http://movie_service/;
}
```

---

# 🚀 Deployment Steps

## 1️⃣ Initialize Docker Swarm

```bash
docker swarm init
```

---

## 2️⃣ Clone Repository

```bash
git clone https://github.com/Shivasai-21/Docker_Stack.git
cd Docker_Stack
```

---

## 3️⃣ Deploy Docker Stack

```bash
docker stack deploy -c compose.yml mystack
```

---

## 4️⃣ Verify Running Services

```bash
docker stack services mystack
```

---

# 🌍 Access Applications

```bash
http://<SERVER-IP>/bus/
http://<SERVER-IP>/movie/
http://<SERVER-IP>/flight/
```

---

# 🔐 Docker Secrets Used

| Secret | Purpose |
|------|------|
| `db_password` | Bus Service |
| `api_key` | Movie Service |
| `flight_token` | Flight Service |

---

# 📦 Persistent Volumes

| Volume | Service |
|------|------|
| `app1` | Bus Service |
| `app2` | Movie Service |
| `app3` | Flight Service |

---

# 📈 Resource Allocation

## Bus Service
- CPU Limit: 0.5
- Memory Limit: 512MB

## Movie Service
- CPU Limit: 1.0
- Memory Limit: 1GB

## Flight Service
- CPU Limit: 0.75
- Memory Limit: 768MB

---

# 🛠 Useful Commands

## Check Running Services

```bash
docker stack services mystack
```

## Check Service Logs

```bash
docker service logs mystack_reverse-proxy
```

## Scale a Service

```bash
docker service scale mystack_app1=5
```

## Remove Stack

```bash
docker stack rm mystack
```

---

# ⚠️ Special Note

Although Dockerfiles are included for all applications (`app1`, `app2`, and `app3`), the deployment intentionally uses pre-built Docker images from Docker Hub instead of building images locally during deployment.

Example:

```yaml
image: shivasai21/myimg:movie
```

This approach reflects real-world production practices where:

- Images are built during CI/CD pipelines
- Images are pushed to a container registry
- Production servers pull versioned images directly from registries

The Dockerfiles are included in this repository for reference and reproducibility purposes.

---

# 🎯 Learning Outcomes

This project demonstrates practical understanding of:

- Docker Swarm Orchestration
- Reverse Proxy Architecture
- Service Discovery
- Overlay Networking
- Docker Secrets
- Container Scaling
- Resource Management
- Production-Style Deployments

---

# 📌 Future Improvements

- HTTPS with SSL/TLS
- CI/CD Pipeline Integration
- Monitoring with Prometheus & Grafana
- Centralized Logging
- Auto Scaling
- Blue-Green Deployment Strategy
- Traefik Ingress Controller

---

# 👨‍💻 Author

Developed by Shivasai

GitHub:
https://github.com/Shivasai-21

---
