# Docker Node.js Application on AWS with Docker

<p align="center">

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![MIT License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

</p>

---

# Project Overview

This project demonstrates how to containerize a Node.js application using Docker and deploy it in a consistent, isolated, and reproducible environment.

The primary objective of this project was to gain hands-on experience with the complete Docker image lifecycle—from creating a Dockerfile to building a custom Docker image, running containers, inspecting logs, troubleshooting issues, and managing container execution on an AWS-hosted Linux environment.

Instead of running the application directly on the operating system, Docker packages the application together with its runtime, dependencies, and configuration into a portable container image. This approach ensures that the application behaves consistently regardless of where it is deployed.

This repository documents the practical implementation, commands executed, architectural design, screenshots, lessons learned, and engineering decisions made throughout the project.

---

# Project Objectives

The main objectives of this project were to:

- Understand Docker's architecture and core components.
- Learn the difference between Docker images and containers.
- Create a production-ready Dockerfile for a Node.js application.
- Build custom Docker images using Docker Build.
- Run containerized applications with Docker.
- Expose applications through port mapping.
- Inspect running containers.
- Debug containers using Docker logs and interactive shell sessions.
- Stop, restart, and remove containers.
- Develop a repeatable deployment workflow using Docker.
- Document the complete implementation process for future reference.

---

# Key Skills Demonstrated

This project demonstrates practical experience with:

- Docker Installation
- Docker Engine
- Docker Images
- Docker Containers
- Dockerfile
- Docker Build
- Docker Run
- Docker CLI
- Container Lifecycle Management
- Image Tagging
- Port Mapping
- Docker Logs
- Docker Exec
- Container Debugging
- Linux Command Line
- AWS EC2
- Node.js Deployment
- Application Containerization
- Infrastructure Documentation

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| Node.js | Backend Application |
| Docker | Containerization Platform |
| Docker CLI | Container Management |
| Dockerfile | Image Definition |
| AWS EC2 | Cloud Compute Environment |
| Ubuntu Linux | Operating System |
| Git | Version Control |
| GitHub | Source Code Repository |

---

# Architecture Overview

The application follows a straightforward containerization workflow.

1. The Node.js application source code is stored inside the project directory.

2. Docker reads the Dockerfile.

3. Docker builds a custom image.

4. The image is stored locally on the Docker host.

5. A container is created from the image.

6. Docker maps the application port from the container to the EC2 instance.

7. Users access the running application through a web browser.

---

# Architecture Diagram

> **Replace the placeholder below with your Draw.io architecture diagram after exporting it as a PNG.**

```
images/architecture.png
```

<p align="center">

![Architecture Diagram](images/architecture.png)

</p>

---

# High-Level Workflow

```text
Developer
     │
     ▼
Node.js Source Code
     │
     ▼
Dockerfile
     │
docker build
     │
     ▼
Docker Image
     │
docker run
     │
     ▼
Running Docker Container
     │
Port Mapping
     │
     ▼
AWS EC2 Instance
     │
     ▼
Web Browser
```

---

# Repository Structure

```text
Docker-nodejs-app
│
├── README.md
├── LICENSE
├── .gitignore
│
├── app/
│   ├── Node.js Source Code
│
├── docker/
│   └── Dockerfile
│
├── architecture/
│   └── architecture.drawio
│
├── docs/
│   ├── setup.md
│   ├── troubleshooting.md
│   └── lessons-learned.md
│
├── images/
│   ├── architecture.png
│   ├── docker-version.png
│   ├── docker-build.png
│   ├── docker-images.png
│   ├── docker-run.png
│   ├── docker-ps.png
│   ├── docker-logs.png
│   ├── docker-exec.png
│   ├── application-browser.png
│   └── docker-stop.png
│
├── commands.md
│
└── video-script.md
```

---

# Learning Outcomes

By completing this project, I gained practical experience in:

- Building Docker images from source code.
- Writing and understanding Dockerfiles.
- Packaging applications into portable containers.
- Running applications in isolated environments.
- Managing Docker containers through the command line.
- Inspecting application logs.
- Troubleshooting running containers.
- Understanding Docker's image-to-container workflow.
- Deploying containerized applications on AWS infrastructure.
- Documenting engineering work using GitHub as a professional portfolio.

---
