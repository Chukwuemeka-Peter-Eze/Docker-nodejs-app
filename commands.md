# Docker Commands Reference

This document contains the Docker commands used throughout this project, along with explanations of their purpose and common use cases.

---

# Table of Contents

- Verify Docker Installation
- Docker Images
- Build Docker Image
- Run Docker Container
- List Containers
- Stop Containers
- Start Containers
- Restart Containers
- Remove Containers
- Remove Images
- View Logs
- Access Running Container
- Inspect Container
- Docker System Cleanup
- Networking Commands
- Useful Development Commands
- Command Summary

---

# Verify Docker Installation

Verify that Docker is installed and running correctly.

```bash
docker --version
```

Example Output

```text
Docker version 28.x.x
```

---

# Verify Docker Engine

```bash
docker info
```

Purpose

Displays detailed information about:

- Docker Engine
- Storage Driver
- Running Containers
- Images
- CPU
- Memory
- Network Configuration

---

# Download an Image

Download an image from Docker Hub.

```bash
docker pull node
```

Another example

```bash
docker pull nginx
```

---

# List Available Images

```bash
docker images
```

Example Output

```text
REPOSITORY          TAG       IMAGE ID
node               latest    xxxxxxxxx
ubuntu             latest    xxxxxxxxx
```

---

# Build a Docker Image

Build an image from the Dockerfile in the current directory.

```bash
docker build -t docker-nodejs-app .
```

Explanation

- `docker build` builds an image.
- `-t` assigns a name (tag).
- `.` specifies the current directory as the build context.

---

# Run a Docker Container

Start a container from an image.

```bash
docker run -d \
-p 3000:3000 \
--name nodejs-app \
docker-nodejs-app
```

Explanation

- `-d` Detached mode
- `-p` Port mapping
- `--name` Assign container name

---

# Run Container in Interactive Mode

```bash
docker run -it ubuntu bash
```

Useful for testing Linux environments.

---

# List Running Containers

```bash
docker ps
```

Displays only active containers.

---

# List All Containers

```bash
docker ps -a
```

Displays:

- Running containers
- Stopped containers
- Exited containers

---

# Stop a Container

```bash
docker stop nodejs-app
```

Gracefully terminates the running container.

---

# Start a Container

```bash
docker start nodejs-app
```

Starts a previously stopped container.

---

# Restart a Container

```bash
docker restart nodejs-app
```

Stops and immediately starts the container again.

---

# Remove a Container

```bash
docker rm nodejs-app
```

Deletes the container while preserving the Docker image.

---

# Remove an Image

```bash
docker rmi docker-nodejs-app
```

Deletes the Docker image from the local image cache.

---

# View Container Logs

```bash
docker logs nodejs-app
```

Useful for:

- Startup verification
- Error detection
- Application debugging

---

# Follow Logs in Real Time

```bash
docker logs -f nodejs-app
```

Displays live log output.

---

# Access a Running Container

Open an interactive shell.

```bash
docker exec -it nodejs-app sh
```

If Bash is available:

```bash
docker exec -it nodejs-app bash
```

Common uses

- Inspect files
- Check installed packages
- Debug applications
- Verify configuration

---

# Copy Files into a Container

```bash
docker cp file.txt nodejs-app:/app
```

---

# Copy Files from a Container

```bash
docker cp nodejs-app:/app/log.txt .
```

---

# Inspect a Container

```bash
docker inspect nodejs-app
```

Provides detailed JSON information including:

- Networking
- Volumes
- Ports
- Environment variables
- Mounts

---

# Display Resource Usage

```bash
docker stats
```

Displays:

- CPU usage
- Memory usage
- Network I/O
- Block I/O

---

# View Running Processes

```bash
docker top nodejs-app
```

Shows running processes inside the container.

---

# Remove Unused Resources

```bash
docker system prune
```

Removes:

- Stopped containers
- Unused networks
- Dangling images
- Build cache

To remove everything:

```bash
docker system prune -a
```

---

# Remove Unused Volumes

```bash
docker volume prune
```

Deletes unused Docker volumes.

---

# Docker Networks

List available networks.

```bash
docker network ls
```

Inspect a network.

```bash
docker network inspect bridge
```

Create a custom network.

```bash
docker network create my-network
```

---

# Tag an Image

```bash
docker tag docker-nodejs-app docker-nodejs-app:v1
```

Useful when maintaining multiple image versions.

---

# Search Docker Hub

```bash
docker search node
```

Searches public Docker Hub repositories.

---

# Remove All Stopped Containers

```bash
docker container prune
```

---

# Remove Dangling Images

```bash
docker image prune
```

---

# Useful Development Workflow

```bash
docker build -t docker-nodejs-app .

docker images

docker run -d \
-p 3000:3000 \
--name nodejs-app \
docker-nodejs-app

docker ps

docker logs nodejs-app

docker exec -it nodejs-app sh

docker stop nodejs-app

docker rm nodejs-app
```

This represents the complete workflow used during this project.

---

# Command Summary

| Command | Purpose |
|----------|---------|
| docker --version | Verify Docker installation |
| docker info | Docker Engine information |
| docker images | List images |
| docker build | Build image |
| docker run | Create and start container |
| docker ps | List running containers |
| docker ps -a | List all containers |
| docker logs | View logs |
| docker exec | Enter running container |
| docker inspect | Inspect container |
| docker stats | Monitor resource usage |
| docker top | View running processes |
| docker stop | Stop container |
| docker start | Start container |
| docker restart | Restart container |
| docker rm | Remove container |
| docker rmi | Remove image |
| docker network ls | List networks |
| docker volume prune | Remove unused volumes |
| docker system prune | Clean up unused Docker resources |

---

# Conclusion

This command reference serves as a quick guide to the Docker operations performed throughout this project. Understanding these commands is essential for building, running, managing, debugging, and maintaining containerized applications in both development and production environments.
