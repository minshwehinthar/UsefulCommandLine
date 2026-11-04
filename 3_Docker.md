# 🐳 Docker & Docker Compose Quick Reference Guide

A full quick-reference guide covering Docker image management, container operations, networking, storage volumes, and Docker Compose workflows.

---

## 📑 Table of Contents
- [Image Operations](#-image-operations)
- [Container Management](#-container-management)
- [Container Lifecycle](#-container-lifecycle)
- [Volumes & Data Persistence](#-volumes--data-persistence)
- [Networks](#-networks)
- [Docker Compose Operations](#-docker-compose-operations)
- [System Cleanup & Diagnostics](#-system-cleanup--diagnostics)

---

## 🖼️ Image Operations

| Command | Description |
| :--- | :--- |
| `docker pull <image>:<tag>` | Download image from Docker Hub |
| `docker images` | List stored local images |
| `docker rmi <image_id>` | Remove a local image |
| `docker build -t <name>:<tag> .` | Build an image from a Dockerfile |
| `docker image prune` | Remove unused/dangling images |
| `docker image prune -a` | Remove all unused images (not just dangling) |
| `docker save -o archive.tar <image>` | Export image to a tar file |
| `docker load -i archive.tar` | Import image from a tar file |

---

## 🚀 Container Management

```bash
# Run container in background with port mapping and volume mount
docker run -d \
  -p 8080:80 \
  -v $(pwd)/app:/var/www/html \
  --name web_app \
  nginx:alpine

# List running containers
docker ps

# List all containers (including stopped ones)
docker ps -a

# Access container interactive terminal shell
docker exec -it web_app /bin/bash

# View live log output
docker logs -f web_app
```

---

## 🔄 Container Lifecycle

| Action | Command |
| :--- | :--- |
| **Start** | `docker start <container_id>` |
| **Stop** | `docker stop <container_id>` |
| **Restart** | `docker restart <container_id>` |
| **Kill (Force Stop)** | `docker kill <container_id>` |
| **Remove Container** | `docker rm <container_id>` |
| **Force Remove Running Container** | `docker rm -f <container_id>` |

---

## 💾 Volumes & Data Persistence

| Command | Description |
| :--- | :--- |
| `docker volume create app_data` | Create a managed volume |
| `docker volume ls` | List all volumes |
| `docker volume inspect app_data` | Inspect volume details (host storage mount location) |
| `docker volume rm app_data` | Remove a volume |
| `docker volume prune` | Delete unused volumes |

---

## 🌐 Networks

| Command | Description |
| :--- | :--- |
| `docker network create my_bridge_network` | Create a bridge network |
| `docker network ls` | List networks |
| `docker network inspect my_bridge_network` | Inspect network details |
| `docker network connect my_bridge_network web_app` | Attach container to existing network |
| `docker network disconnect my_bridge_network web_app` | Detach container from network |
| `docker network prune` | Remove unused networks |

---

## 🐙 Docker Compose Operations

| Command | Description |
| :--- | :--- |
| `docker compose up -d` | Build, create, and start services in background |
| `docker compose down` | Stop and remove containers, networks created by `up` |
| `docker compose down -v` | Stop containers and delete associated named volumes |
| `docker compose ps` | List containers managed by Compose file |
| `docker compose logs -f <service>` | Tail log streams for a specific service |
| `docker compose exec <service> <cmd>` | Run command inside a running service container |
| `docker compose build --no-cache` | Rebuild images from scratch |

---

## 🧹 System Cleanup & Diagnostics

```bash
# View disk usage by containers, images, and volumes
docker system df

# Clean stopped containers, unused networks, and dangling images
docker system prune

# Comprehensive cleanup (removes ALL unused images and volumes)
docker system prune -a --volumes
```