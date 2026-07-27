# Project Setup Guide

This document provides a step-by-step guide for setting up and running the Dockerized Node.js application in a local development environment. By following these instructions, you will install Docker (if necessary), clone the project, build the Docker image, run the application container, and verify that the application is working correctly.

The guide is intended to provide a repeatable workflow for building, running, and managing containerized applications during local development.

---

# Table of Contents

- Architecture Overview
- Prerequisites
- Development Environment
- Prepare the Local Environment
- Install Docker
- Verify Docker Installation
- Clone the Repository
- Review the Project Structure
- Build the Docker Image
- Verify the Image
- Run the Docker Container
- Verify the Container
- Access the Application
- View Container Logs
- Access the Running Container
- Stop and Remove the Container
- Clean Up Resources
- Summary

---

# Architecture Overview

The deployment workflow follows the sequence below.

```text
Developer
      │
      ▼
GitHub Repository
      │
      ▼
Local Development Machine
      │
      ▼
Docker Engine
      │
      ▼
Docker Image
      │
      ▼
Running Docker Container
      │
      ▼
Node.js Application
      │
      ▼
Web Browser
```

---

# Prerequisites

Before beginning, ensure the following requirements are available.

- Docker Desktop or Docker Engine
- Git
- Node.js (optional, for local application testing)
- Visual Studio Code (recommended)
- Terminal or Command Prompt
- Internet Connectivity
- Web Browser

---

# Development Environment

The project was implemented and tested in a local development environment.

| Component | Description |
|-----------|-------------|
| Development Environment | Local Machine |
| Container Runtime | Docker Engine |
| Source Code Repository | GitHub |
| Application Runtime | Node.js |
| Database | MongoDB |
| Database Administration | Mongo Express |
| Version Control | Git |

---

# Step 1: Prepare the Local Development Environment

Ensure Docker Engine (or Docker Desktop) is installed and running on your computer.

Verify the installation:

```bash
docker --version
```

Expected output:

```text
Docker version xx.x.x
```

Also verify that Git is installed:

```bash
git --version
```

Once these tools are available, you're ready to clone and run the project.

---

# Step 2: Install Docker

If Docker is not already installed on your local machine, install Docker Engine or Docker Desktop according to your operating system.

After installation, verify that Docker is running before continuing.

```bash
docker --version
```

Expected result:

```text
Docker version xx.x.x
```

---

# Step 3: Verify Docker Engine

Check that the Docker daemon is running.

```bash
docker info
```

The output should display Docker Engine information, including the number of images, containers, storage driver, and system resources.

---

# Step 4: Clone the Repository

Clone the project repository to your local development environment.

```bash
git clone https://github.com/Chukwuemeka-Peter-Eze/Docker-nodejs-app.git
```

Navigate into the project directory.

```bash
cd Docker-nodejs-app
```

---

# Step 5: Review the Project Structure

Ensure the repository contains the required project files.

Example:

```text
Docker-nodejs-app/

Dockerfile

package.json

package-lock.json

server.js

README.md

images/

docs/
```

---

# Step 6: Build the Docker Image

Build the application image.

```bash
docker build -t docker-nodejs-app .
```

Docker will:

- Read the Dockerfile
- Download the base image
- Copy application files
- Install dependencies
- Build image layers
- Produce the final image

---

# Step 7: Verify the Image

Confirm that the image was successfully created.

```bash
docker images
```

Verify that the repository name and image tag appear in the list.

---

# Step 8: Run the Application

Create and start the container.

```bash
docker run -d \
-p 3000:3000 \
--name nodejs-app \
docker-nodejs-app
```

The application should now be running inside an isolated Docker container.

---

# Step 9: Verify the Running Container

Display active containers.

```bash
docker ps
```

Confirm:

- Container is running
- Port mapping is correct
- Status is healthy

---

# Step 10: Access the Application

Open a browser and navigate to:

```text
http://localhost:3000
```

The successful loading of the application confirms that:

- Docker image built correctly
- Container started successfully
- Port mapping is functioning
- Network connectivity is working

---

# Step 11: Inspect Container Logs

View the application logs.

```bash
docker logs nodejs-app
```

Logs are useful for:

- Startup verification
- Runtime troubleshooting
- Error identification

---

# Step 12: Access the Running Container

Open an interactive shell.

```bash
docker exec -it nodejs-app sh
```

Use this shell to inspect the container filesystem, verify application files, and perform troubleshooting if necessary.

---

# Step 13: Stop the Container

Gracefully stop the running application.

```bash
docker stop nodejs-app
```

---

# Step 14: Restart the Container

Restart the previously stopped container.

```bash
docker start nodejs-app
```

---

# Step 15: Remove the Container

Delete the container when it is no longer required.

```bash
docker rm nodejs-app
```

This removes the container while keeping the Docker image available for future deployments.

---

# Step 16: Remove the Docker Image (Optional)

Delete the locally stored image.

```bash
docker rmi docker-nodejs-app
```

Only perform this step if the image is no longer needed.

---

# Step 17: Clean Up Unused Docker Resources

Remove unused Docker resources.

```bash
docker system prune
```

To remove all unused images as well:

```bash
docker system prune -a
```

This helps reclaim disk space on the host system.

---

# Deployment Verification Checklist

- Docker installed successfully
- Docker Engine running
- Repository cloned locally
- Docker image built successfully
- Image verified using `docker images`
- Container started successfully
- Container visible in `docker ps`
- Application accessible at `http://localhost:3000`
- Application logs available
- Interactive shell accessible using `docker exec`

---

# Summary

This setup guide demonstrates the complete process of building, running, and managing a containerized Node.js application using Docker in a local development environment.

By following these steps, the application can be cloned, built into a Docker image, deployed as a container, verified, and managed using standard Docker commands. The workflow provides a repeatable process suitable for local development, testing, and future deployment to other environments.

The project emphasizes reproducibility, portability, and operational simplicity—core principles of modern containerized application development and a strong foundation for future topics such as Docker Compose, Kubernetes, CI/CD pipelines, and cloud-based deployments.
