# Project Setup Guide

This document provides a step-by-step guide for reproducing the Docker Node.js application deployment on an AWS EC2 instance. Following these instructions will allow you to provision the environment, install Docker, build the application image, run the container, and verify that the application is working correctly.

---

# Table of Contents

- Architecture Overview
- Prerequisites
- AWS Infrastructure
- Launch an EC2 Instance
- Connect to the Server
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
AWS EC2 Instance
      │
      ▼
Ubuntu Linux
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

- AWS Account
- Amazon EC2 Instance
- Ubuntu Linux Server
- SSH Client
- Docker Engine
- Git
- Internet Connectivity
- Web Browser

---

# AWS Infrastructure

The project was deployed using the following cloud components.

| Component | Description |
|-----------|-------------|
| Cloud Provider | Amazon Web Services |
| Compute Service | Amazon EC2 |
| Operating System | Ubuntu Linux |
| Container Runtime | Docker Engine |
| Source Code Repository | GitHub |
| Application Runtime | Node.js |

---

# Step 1 — Launch an EC2 Instance

Create an Ubuntu EC2 instance from the AWS Management Console.

Recommended configuration:

- Ubuntu Server LTS
- t2.micro (or equivalent)
- Public IP enabled
- Security Group configured
- SSH access enabled

Open the necessary inbound ports.

Example:

| Port | Purpose |
|------|----------|
| 22 | SSH |
| 3000 | Node.js Application |

---

# Step 2 — Connect to the Server

Connect to the EC2 instance using SSH.

Example:

```bash
ssh -i your-key.pem ubuntu@<EC2-Public-IP>
```

After connecting, verify the server is accessible.

---

# Step 3 — Update the System

Update installed packages.

```bash
sudo apt update

sudo apt upgrade -y
```

Keeping the operating system updated helps ensure compatibility and security.

---

# Step 4 — Install Docker

Install Docker Engine on the EC2 instance.

After installation, start the Docker service if required.

Verify the installation.

```bash
docker --version
```

Expected result:

```text
Docker version xx.x.x
```

---

# Step 5 — Verify Docker Engine

Check that the Docker daemon is running.

```bash
docker info
```

The output should display Docker Engine information, including the number of images, containers, storage driver, and system resources.

---

# Step 6 — Clone the Repository

Clone the project repository.

```bash
git clone https://github.com/Chukwuemeka-Peter-Eze/Docker-nodejs-app.git
```

Navigate into the project directory.

```bash
cd Docker-nodejs-app
```

---

# Step 7 — Review the Project Structure

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

# Step 8 — Build the Docker Image

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

# Step 9 — Verify the Image

Confirm that the image was successfully created.

```bash
docker images
```

Verify that the repository name and image tag appear in the list.

---

# Step 10 — Run the Application

Create and start the container.

```bash
docker run -d \
-p 3000:3000 \
--name nodejs-app \
docker-nodejs-app
```

The application should now be running inside an isolated Docker container.

---

# Step 11 — Verify the Running Container

Display active containers.

```bash
docker ps
```

Confirm:

- Container is running
- Port mapping is correct
- Status is healthy

---

# Step 12 — Access the Application

Open a browser and navigate to:

```text
http://<EC2-Public-IP>:3000
```

The successful loading of the application confirms that:

- Docker image built correctly
- Container started successfully
- Port mapping is functioning
- Network connectivity is working

---

# Step 13 — Inspect Container Logs

View the application logs.

```bash
docker logs nodejs-app
```

Logs are useful for:

- Startup verification
- Runtime troubleshooting
- Error identification

---

# Step 14 — Access the Running Container

Open an interactive shell.

```bash
docker exec -it nodejs-app sh
```

Use this shell to inspect the container filesystem, verify application files, and perform troubleshooting if necessary.

---

# Step 15 — Stop the Container

Gracefully stop the running application.

```bash
docker stop nodejs-app
```

---

# Step 16 — Restart the Container

Restart the previously stopped container.

```bash
docker start nodejs-app
```

---

# Step 17 — Remove the Container

Delete the container when it is no longer required.

```bash
docker rm nodejs-app
```

This removes the container while keeping the Docker image available for future deployments.

---

# Step 18 — Remove the Docker Image (Optional)

Delete the locally stored image.

```bash
docker rmi docker-nodejs-app
```

Only perform this step if the image is no longer needed.

---

# Step 19 — Clean Up Unused Docker Resources

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

Use the following checklist to confirm a successful deployment.

- Docker installed successfully
- Docker Engine running
- Repository cloned
- Docker image built
- Image verified
- Container started
- Container visible in `docker ps`
- Application accessible through browser
- Logs available
- Interactive shell accessible

---

# Summary

This setup guide demonstrates the complete process of deploying a containerized Node.js application on AWS using Docker. By following these steps, the application can be built, deployed, verified, and managed consistently across environments, providing a repeatable workflow suitable for development, testing, and future production deployments.

The workflow emphasizes reproducibility, portability, and operational simplicity—key principles of modern containerized application development.
