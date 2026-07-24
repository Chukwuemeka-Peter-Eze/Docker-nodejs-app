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

---

# Prerequisites

Before getting started, ensure the following tools and services are available in your environment.

| Requirement | Description |
|-------------|-------------|
| AWS Account | Used to provision the EC2 instance for hosting the application |
| Amazon EC2 Instance | Linux virtual machine where Docker was installed |
| Ubuntu Linux | Operating system used during implementation |
| Docker Engine | Container runtime used to build and run containers |
| Git | Used to clone the project repository |
| Node.js Application | Sample application used for containerization |
| Terminal Access | SSH connection to the EC2 instance |
| Web Browser | Used to verify the deployed application |

---

# Environment Details

The project was implemented in a cloud environment hosted on AWS.

| Component | Value |
|-----------|-------|
| Cloud Provider | Amazon Web Services (AWS) |
| Compute Service | Amazon EC2 |
| Operating System | Ubuntu Linux |
| Container Runtime | Docker Engine |
| Programming Language | JavaScript |
| Runtime | Node.js |
| Version Control | Git |
| Repository Hosting | GitHub |

---

# Project Workflow

The implementation followed a structured workflow that mirrors how containerized applications are typically deployed in modern engineering environments.

```text
Create Node.js Application
            │
            ▼
Write Dockerfile
            │
            ▼
Build Docker Image
            │
            ▼
Verify Image Creation
            │
            ▼
Run Docker Container
            │
            ▼
Verify Running Container
            │
            ▼
Access Application in Browser
            │
            ▼
Inspect Logs
            │
            ▼
Troubleshoot if Necessary
            │
            ▼
Stop and Remove Container
```

---

# Clone the Repository

Clone the repository to your local machine or EC2 instance.

```bash
git clone https://github.com/Chukwuemeka-Peter-Eze/Docker-nodejs-app.git
```

Navigate into the project directory.

```bash
cd Docker-nodejs-app
```

---

# Project Structure Verification

Verify that the project contains the required application files before building the Docker image.

Example:

```text
Docker-nodejs-app/
│
├── Dockerfile
├── package.json
├── package-lock.json
├── server.js
├── src/
└── ...
```

---

# Dockerfile Overview

The Dockerfile defines how Docker should package the Node.js application into a reusable image.

The implementation includes:

- Selecting an appropriate Node.js base image
- Setting the working directory
- Copying project files
- Installing dependencies
- Exposing the application port
- Defining the startup command

This process ensures that every container created from the image starts with the same runtime environment and application configuration.

---

# Build the Docker Image

Build the application image using Docker.

Example command:

```bash
docker build -t docker-nodejs-app .
```

Docker performs the following operations:

1. Reads the Dockerfile.
2. Downloads the required base image (if not already available).
3. Copies the application source code.
4. Installs dependencies.
5. Creates image layers.
6. Produces a reusable Docker image.

---

## Screenshot Placeholder — Building the Docker Image

> Replace the placeholder below with your screenshot showing the image build process.

```text
images/docker-build.png
```

<p align="center">

![Docker Build](images/docker-build.png)

</p>

---

# Verify the Docker Image

After the build completes successfully, verify that the image exists.

Example command:

```bash
docker images
```

Expected outcome:

- Repository name
- Image tag
- Image ID
- Creation time
- Image size

This confirms that Docker successfully packaged the application into a reusable image.

---

## Screenshot Placeholder — Docker Images

```text
images/docker-images.png
```

<p align="center">

![Docker Images](images/docker-images.png)

</p>

---

# Run the Docker Container

Create and start a container from the newly built image.

Example:

```bash
docker run -d \
-p 3000:3000 \
--name nodejs-app \
docker-nodejs-app
```

Explanation:

- `-d` runs the container in detached mode.
- `-p` maps the host port to the container port.
- `--name` assigns a readable container name.
- The final argument specifies the image used to create the container.

---

## Screenshot Placeholder — Running the Container

```text
images/docker-run.png
```

<p align="center">

![Running Container](images/docker-run.png)

</p>

---

# Verify Running Containers

Confirm that the container is running correctly.

Example:

```bash
docker ps
```

Typical information displayed includes:

- Container ID
- Image
- Command
- Status
- Port mappings
- Container name

Verifying container status is one of the first troubleshooting steps when deploying Dockerized applications.

---

## Screenshot Placeholder — Running Containers

```text
images/docker-ps.png
```

<p align="center">

![Docker PS](images/docker-ps.png)

</p>

---

# Access the Application

Once the container is running successfully, access the application through a web browser using your EC2 instance's public IP address and the mapped application port.

Example:

```text
http://<EC2-Public-IP>:3000
```

If the application loads successfully, it confirms that:

- The Docker image was built correctly.
- The container is running.
- Port mapping is configured correctly.
- The application is listening on the expected port.
- Network connectivity is functioning as intended.

---

## Screenshot Placeholder — Application Running

```text
images/application-browser.png
```

<p align="center">

![Application Running](images/application-browser.png)

</p>

---

# Implementation Summary

By this stage of the project, the following milestones have been completed:

- Docker environment prepared on AWS EC2
- Project source code cloned
- Dockerfile reviewed
- Custom Docker image successfully built
- Docker image verified
- Application container launched
- Running container verified
- Web application successfully accessed through the browser

These steps establish a repeatable workflow for packaging and deploying Node.js applications using Docker.

---

---

# Dockerfile Breakdown

The Dockerfile is the blueprint that defines how Docker should build a container image for the Node.js application. Instead of manually installing dependencies and configuring the runtime environment every time, Docker executes each instruction in the Dockerfile to produce a consistent and reusable image.

A simplified Docker build process follows these stages:

```text
Dockerfile
     │
     ▼
Read Instructions
     │
     ▼
Pull Base Image
     │
     ▼
Copy Application Files
     │
     ▼
Install Dependencies
     │
     ▼
Expose Application Port
     │
     ▼
Configure Startup Command
     │
     ▼
Create Docker Image
```

Each instruction creates a new image layer, allowing Docker to cache unchanged layers and significantly reduce rebuild times.

---

# Understanding the Image Build Process

When the `docker build` command is executed, Docker performs the following sequence:

1. Reads the Dockerfile from the project directory.
2. Downloads the required base image if it is not already available locally.
3. Creates an isolated build environment.
4. Executes each Dockerfile instruction in order.
5. Creates immutable image layers.
6. Packages the application into a Docker image.
7. Stores the completed image in the local Docker image repository.

This layered approach improves efficiency because Docker can reuse previously built layers when rebuilding the image after small code changes.

---

# Docker Image Lifecycle

The lifecycle of the application image can be summarized as follows:

```text
Application Source Code
            │
            ▼
        Dockerfile
            │
            ▼
      docker build
            │
            ▼
      Docker Image
            │
            ▼
       docker run
            │
            ▼
    Running Container
            │
            ▼
 docker stop / restart
            │
            ▼
 docker rm (optional)
```

Understanding this lifecycle helps distinguish between an image (a reusable template) and a container (a running instance of that image).

---

# Inspecting Container Logs

Container logs provide valuable information for monitoring application startup, diagnosing failures, and troubleshooting runtime issues.

Example command:

```bash
docker logs nodejs-app
```

Logs can help identify:

- Application startup messages
- Runtime errors
- Missing dependencies
- Server initialization
- Unexpected exceptions

Reviewing logs is often the first step when a container does not behave as expected.

---

## Screenshot Placeholder — Viewing Container Logs

```text
images/docker-logs.png
```

<p align="center">

![Docker Logs](images/docker-logs.png)

</p>

---

# Accessing the Running Container

Docker allows administrators to open an interactive shell inside a running container for inspection and troubleshooting.

Example:

```bash
docker exec -it nodejs-app sh
```

Using an interactive shell makes it possible to:

- Inspect application files
- Verify installed packages
- Explore the container filesystem
- Run diagnostic commands
- Validate environment configuration

Interactive access is especially useful during development and debugging.

---

## Screenshot Placeholder — Interactive Shell

```text
images/docker-exec.png
```

<p align="center">

![Docker Exec](images/docker-exec.png)

</p>

---

# Managing the Container Lifecycle

Docker provides commands to control the state of a container throughout its lifecycle.

## Stop a Running Container

```bash
docker stop nodejs-app
```

Gracefully stops the application and releases allocated resources.

---

## Start an Existing Container

```bash
docker start nodejs-app
```

Starts a previously stopped container without rebuilding the image.

---

## Restart a Container

```bash
docker restart nodejs-app
```

Stops and immediately starts the container again.

---

## Remove a Container

```bash
docker rm nodejs-app
```

Deletes the container while leaving the underlying Docker image intact.

---

## Remove a Docker Image

```bash
docker rmi docker-nodejs-app
```

Deletes the locally stored image when it is no longer required.

---

## Screenshot Placeholder — Stopping the Container

```text
images/docker-stop.png
```

<p align="center">

![Stopping Container](images/docker-stop.png)

</p>

---

# Common Docker Commands

| Command | Purpose |
|----------|---------|
| `docker build` | Build a Docker image from a Dockerfile |
| `docker images` | List available Docker images |
| `docker run` | Create and start a container |
| `docker ps` | Display running containers |
| `docker ps -a` | Display all containers |
| `docker logs` | View container logs |
| `docker exec -it` | Open an interactive shell inside a running container |
| `docker stop` | Stop a running container |
| `docker start` | Start a stopped container |
| `docker restart` | Restart a container |
| `docker rm` | Remove a container |
| `docker rmi` | Remove a Docker image |

---

# Container Debugging Workflow

When troubleshooting a Dockerized application, the following sequence provides a structured approach:

```text
Application Not Responding
            │
            ▼
Check Running Containers
(docker ps)
            │
            ▼
Inspect Logs
(docker logs)
            │
            ▼
Access Container
(docker exec -it)
            │
            ▼
Verify Application Process
            │
            ▼
Identify Root Cause
            │
            ▼
Apply Fix
            │
            ▼
Rebuild Image
            │
            ▼
Redeploy Container
```

Following a consistent debugging workflow helps reduce troubleshooting time and improves operational reliability.

---

# Docker Best Practices Applied

The implementation followed several widely accepted Docker practices:

- Built the application using a dedicated Dockerfile.
- Used Docker images to package application code and dependencies together.
- Assigned meaningful names to images and containers.
- Verified image creation before deployment.
- Used detached mode to run containers in the background.
- Published application ports explicitly.
- Verified container status after startup.
- Used Docker logs for troubleshooting.
- Accessed running containers for inspection using an interactive shell.
- Maintained a repeatable workflow that can be executed consistently across environments.

---

# Skills Demonstrated

This project demonstrates hands-on experience with:

- Docker image creation
- Dockerfile authoring
- Container lifecycle management
- Linux command-line operations
- Container debugging
- Image verification
- Port mapping
- Docker CLI
- Application deployment
- AWS-based container execution
- Technical documentation
- Engineering workflow documentation

---

---

# Implementation Walkthrough

This section documents the complete implementation process followed during the project, from preparing the environment to successfully running the Node.js application inside a Docker container.

The workflow demonstrates how Docker enables applications to be packaged, deployed, and executed consistently across environments.

---

## Phase 1 — Environment Preparation

The first phase involved preparing the development environment on an AWS EC2 instance.

Activities completed included:

- Launching an Ubuntu EC2 instance
- Connecting to the server via SSH
- Installing Docker Engine
- Verifying the Docker installation
- Confirming Docker daemon functionality

### Screenshot Placeholder

```text
images/docker-version.png
```

<p align="center">

![Docker Version](images/docker-version.png)

</p>

---

## Phase 2 — Preparing the Application

The Node.js application source code was prepared for containerization.

Tasks completed included:

- Reviewing the application structure
- Verifying package dependencies
- Understanding the application entry point
- Preparing the Docker build context

This ensured that all required files were available before creating the Docker image.

---

## Phase 3 — Creating the Dockerfile

A Dockerfile was created to define the application's build process.

The Dockerfile specifies:

- The base image
- Working directory
- File copy instructions
- Dependency installation
- Exposed application port
- Startup command

By defining these instructions declaratively, the application can be rebuilt consistently whenever needed.

### Screenshot Placeholder

```text
images/dockerfile-created.png
```

<p align="center">

![Dockerfile](images/dockerfile-created.png)

</p>

---

## Phase 4 — Building the Docker Image

The Docker image was built from the application source code using the Dockerfile.

During this stage Docker:

- Read the Dockerfile
- Pulled the required base image
- Executed build instructions
- Installed dependencies
- Created image layers
- Produced a reusable application image

This image became the deployment artifact for the application.

### Screenshot Placeholder

```text
images/docker-build.png
```

<p align="center">

![Docker Build](images/docker-build.png)

</p>

---

## Phase 5 — Running the Container

After the image was successfully created, a container was launched.

The container:

- Started successfully
- Exposed the configured application port
- Ran in an isolated environment
- Executed independently from the host operating system

This validated that the image was functional and ready for execution.

### Screenshot Placeholder

```text
images/docker-run.png
```

<p align="center">

![Running Container](images/docker-run.png)

</p>

---

## Phase 6 — Verification

Several verification steps were performed to confirm that the deployment was successful.

Checks included:

- Listing Docker images
- Confirming container status
- Accessing the application
- Reviewing application logs
- Entering the running container
- Stopping and restarting the container

These verification activities ensured that both the image and the container behaved as expected.

---

# Screenshot Gallery

Replace each placeholder below with your corresponding screenshots.

| Activity | Screenshot |
|-----------|------------|
| Docker Installation Verification | `images/docker-version.png` |
| Dockerfile Creation | `images/dockerfile-created.png` |
| Building Docker Image | `images/docker-build.png` |
| Docker Images | `images/docker-images.png` |
| Running Container | `images/docker-run.png` |
| Running Containers | `images/docker-ps.png` |
| Browser Verification | `images/application-browser.png` |
| Container Logs | `images/docker-logs.png` |
| Interactive Shell | `images/docker-exec.png` |
| Container Stop | `images/docker-stop.png` |

---

# Challenges Encountered

During the implementation of this project, several common challenges were encountered and resolved.

## Container Failed to Start

Possible causes:

- Incorrect startup command
- Missing application dependency
- Incorrect working directory

Resolution:

- Reviewed the Dockerfile
- Checked application logs
- Rebuilt the Docker image

---

## Port Already in Use

Possible causes:

- Another application was already listening on the selected port.

Resolution:

- Identified the conflicting process.
- Stopped the existing service or selected an alternative host port.

---

## Image Build Errors

Possible causes:

- Missing files
- Incorrect Dockerfile instructions
- Dependency installation failures

Resolution:

- Reviewed build output.
- Corrected Dockerfile configuration.
- Rebuilt the image.

---

## Application Not Accessible

Possible causes:

- Incorrect port mapping
- Application not listening on the expected port
- Security group configuration on AWS

Resolution:

- Verified port mapping.
- Confirmed the application was running.
- Checked EC2 security group rules.

---

# Lessons Learned

This project provided practical experience in applying containerization concepts to a real application.

Key lessons include:

- Docker images provide a portable and consistent deployment artifact.
- Containers isolate application dependencies from the host system.
- Dockerfiles make deployments repeatable and version-controlled.
- Logging is essential for troubleshooting containerized workloads.
- Interactive container access simplifies debugging.
- Image layering improves build efficiency through caching.
- Infrastructure documentation improves reproducibility and knowledge sharing.
- Running workloads on AWS demonstrates how containerization integrates with cloud infrastructure.

---

# Future Improvements

Possible enhancements for this project include:

- Implementing multi-stage Docker builds to reduce image size.
- Running the application as a non-root user.
- Adding Docker health checks.
- Integrating automated image scanning into a CI/CD pipeline.
- Publishing images to a private container registry.
- Adding automated testing during image builds.
- Managing configuration with environment variables and secrets.
- Orchestrating the application using Docker Compose or Kubernetes.

---

# References

The following resources were used throughout this project:

- Docker Official Documentation
- Docker CLI Reference
- Dockerfile Best Practices
- Node.js Documentation
- AWS EC2 Documentation

---

# Project Summary

This project demonstrates the end-to-end process of containerizing a Node.js application using Docker and running it on AWS infrastructure.

The implementation covered:

- Creating a Dockerfile
- Building a Docker image
- Running a container
- Verifying deployment
- Inspecting logs
- Troubleshooting issues
- Managing the container lifecycle
- Documenting the engineering workflow

Beyond simply running an application in Docker, this project highlights the importance of repeatable deployments, infrastructure consistency, and technical documentation. These are foundational practices for modern DevOps and cloud engineering workflows.

---

# Connect With Me

If you found this project helpful or would like to discuss Docker, DevOps, Cloud Engineering, or Infrastructure Automation, feel free to connect.

- **GitHub:** https://github.com/Chukwuemeka-Peter-Eze
- **LinkedIn:** https://www.linkedin.com/in/chukwuemekapetereze/

If you found this repository useful, consider giving it a ⭐ to support the project.

---
