---
title: "🐳 Docker & Docker Compose Cheat Sheet."
datePublished: Sun Feb 23 2025 13:41:22 GMT+0000 (Coordinated Universal Time)
cuid: cm7hogaqr000508jj6nq92eeh
slug: docker-and-docker-compose-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740317886496/8f010b14-3aa4-4154-b289-869629ab8a3a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1740318052565/9e98ae21-74d4-4bdc-bb9b-9d79486ae219.png
tags: 90daysofdevops, trainwithshubham, 90daysofdevops-chanllenge, 90daysofdevopschallenge

---

### **🐳 Docker & Docker Compose Cheat Sheet**

| **Category** | **Command** | **Description** |
| --- | --- | --- |
| **🛠️ Container Management** | `docker run -d --name my_container image` | Run container in detached mode |
|  | `docker ps -a` | List all containers (running & stopped) |
|  | `docker stop container_id` | Stop a running container |
|  | `docker start container_id` | Start a stopped container |
|  | `docker restart container_id` | Restart a container |
|  | `docker rm container_id` | Remove a stopped container |
|  | `docker logs container_id` | View container logs |
|  | `docker exec -it container_id bash` | Open a shell inside a container |
| **📦 Image Management** | `docker images` | List all Docker images |
|  | `docker pull image_name` | Download an image from Docker Hub |
|  | `docker build -t my_image .` | Build an image from a Dockerfile |
|  | `docker rmi image_id` | Remove an image |
| **🌐 Networking** | `docker network ls` | List available networks |
|  | `docker network create my_network` | Create a new network |
|  | `docker network connect my_network container_id` | Connect a container to a network |
| **💾 Volume Management** | `docker volume ls` | List all volumes |
|  | `docker volume create my_volume` | Create a volume |
|  | `docker run -v my_volume:/data image_name` | Mount a volume to a container |
| **🧹 Cleanup Commands** | `docker system prune` | Remove unused containers, networks, and images |
|  | `docker container prune` | Remove all stopped containers |
|  | `docker image prune` | Remove dangling images |
| **🚀 Docker Compose** | `docker-compose up -d` | Start services in detached mode |
|  | `docker-compose down` | Stop and remove services |
|  | `docker-compose ps` | List running services |
|  | `docker-compose logs` | View service logs |
