# Containerizing a Node.js Application Using Docker

<p align="center">

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Dockerfile](https://img.shields.io/badge/Dockerfile-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![MIT License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

</p>

---

# Table of Contents

- [Project Overview](#project-overview)
- [Project Objectives](#project-objectives)
- [Key Features](#key-features)
- [Application Architecture](#application-architecture)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [Architecture Diagram](#architecture-diagram)
- [Prerequisites](#prerequisites)
- [Clone the Repository](#clone-the-repository)
- [Running the Application](#running-the-application)
- [Building the Docker Image](#building-the-docker-image)
- [Managing Docker Containers](#managing-docker-containers)
- [Screenshot Gallery](#screenshot-gallery)
- [Lessons Learned](#lessons-learned)
- [Future Improvements](#future-improvements)
- [Documentation](#documentation)
- [References](#references)
- [Connect With Me](#connect-with-me)

---

# Project Overview

This project demonstrates how to containerize a **Node.js application** using Docker while following containerization best practices.

The application consists of a simple frontend built with **HTML, CSS, and JavaScript**, a backend powered by **Node.js and Express**, and a **MongoDB** database for storing user data. **Mongo Express** is used as a web-based interface for viewing and managing the database during development.

The primary goal of this project was to gain hands-on experience with the complete Docker workflow—from writing a Dockerfile and building a Docker image to running, inspecting, debugging, and managing Docker containers in a local development environment.

The entire implementation was completed using **Visual Studio Code**, **Docker Desktop**, and **Git**, before being published to GitHub as part of my DevOps engineering portfolio.

> **📌 Project Scope**
>
> This repository demonstrates **local application containerization using Docker**. It does **not** cover cloud deployment, Docker Compose, Kubernetes, or other container orchestration platforms.

---

# Project Objectives

The objectives of this project were to:

- Understand Docker architecture and core concepts.
- Learn the difference between Docker images and containers.
- Write a reusable Dockerfile for a Node.js application.
- Build custom Docker images.
- Run applications inside Docker containers.
- Connect the application to a MongoDB database.
- Use Mongo Express to inspect stored data.
- Publish application ports.
- Inspect running containers.
- Debug applications using Docker logs.
- Access containers using an interactive shell.
- Manage the complete Docker container lifecycle.
- Document the implementation process for future reference and portfolio purposes.

---

# Key Features

- Dockerized Node.js application
- Custom Dockerfile
- MongoDB database integration
- Mongo Express database management interface
- Docker image creation
- Container lifecycle management
- Port mapping
- Interactive container debugging
- Docker log inspection
- Technical documentation
- GitHub portfolio ready

---

# Application Architecture

The application is composed of four primary components that work together to provide a complete containerized development environment.

```text
                    Web Browser
                         │
                         ▼
                Node.js Application
                  (Express Server)
                         │
                         ▼
                 Docker Container
                         │
                         ▼
                  MongoDB Database
                         ▲
                         │
                   Mongo Express
```

The Node.js application runs inside a Docker container and communicates with a MongoDB database to store and retrieve application data. Mongo Express provides a browser-based interface for viewing and managing the database during development.

> **📌 Note**
>
> MongoDB and Mongo Express were used as supporting services for local development. The focus of this repository is learning Docker fundamentals and containerizing a Node.js application.

---

## Application Components

### Frontend

The user interface consists of:

- HTML
- CSS
- JavaScript

The frontend communicates with the backend through HTTP requests.

---

### Backend

The backend is built with:

- Node.js
- Express

The Express server handles incoming requests, processes application logic, and communicates with the MongoDB database.

---

### Database

MongoDB serves as the application's database.

It stores user information entered through the web application, allowing data to persist even after the application is refreshed.

---

### Database Administration

Mongo Express provides a web-based interface for:

- Viewing databases
- Browsing collections
- Managing stored documents
- Verifying application data

This made it easier to inspect database records during development and testing.

---

### Containerization

Docker provides the runtime environment for the application by:

- Packaging the application and its dependencies into a Docker image
- Running the application inside an isolated container
- Providing a consistent execution environment
- Simplifying application deployment and testing

---

# Technologies Used

| Technology | Purpose |
|------------|---------|
| Node.js | JavaScript runtime for the backend application |
| Express | Web framework used to build the application server |
| MongoDB | NoSQL database for storing application data |
| Mongo Express | Browser-based MongoDB administration interface |
| Docker | Containerization platform |
| Docker Engine | Runtime used to build and run containers |
| Docker CLI | Command-line interface for managing Docker |
| Dockerfile | Defines how the application image is built |
| HTML | Frontend structure |
| CSS | Frontend styling |
| JavaScript | Client-side functionality |
| Git | Version control |
| GitHub | Repository hosting |
| Visual Studio Code | Development environment |
| Docker Desktop | Local Docker runtime |

---

# Project Structure

```text
Docker-nodejs-app/
│
├── app/
│   ├── images/
│   ├── index.html
│   ├── package.json
│   ├── package-lock.json
│   └── server.js
│
├── docs/
│   ├── commands.md
│   ├── lessons-learned.md
│   ├── setup.md
│   ├── troubleshooting.md
│   └── video-script.md
│
├── images/
│   ├── architecture.gif
│   ├── docker-installation-verification.png
│   ├── docker-build.png
│   ├── docker-images.png
│   ├── docker-run.png
│   ├── docker-ps.png
│   ├── application-running.png
│   ├── docker-logs.png
│   └── docker-exec.png
│
├── Dockerfile
├── docker_commands.md
├── README.md
└── .gitignore
```

> **💡 Repository Organization**
>
> The project is organized into separate folders for source code, documentation, screenshots, and supporting assets to make it easy to navigate and understand the implementation workflow.

---

# Architecture Diagram

The following diagram illustrates the overall architecture of the application.

<p align="center">
    <img src="images/architecture.gif" alt="Application Architecture Diagram" width="900">
</p>

### Architecture Summary

The workflow consists of the following steps:

1. The user accesses the application through a web browser.
2. Requests are handled by the Node.js application running inside a Docker container.
3. The application communicates with MongoDB to store and retrieve data.
4. Mongo Express provides a web interface for inspecting and managing the database.
5. Docker ensures the application runs in a consistent and isolated environment.

---

# Prerequisites

Before running this project, ensure the following software is installed on your local machine.

| Requirement | Purpose |
|-------------|---------|
| Docker Desktop | Build and run Docker containers |
| Docker Engine | Container runtime |
| Git | Clone the repository |
| Visual Studio Code | View and edit the project |
| Web Browser | Access the application and Mongo Express |

> **📌 Note**
>
> Docker Desktop includes Docker Engine and the Docker CLI, so installing Docker Desktop is sufficient for this project.

---

# Clone the Repository

Clone the repository to your local machine.

```bash
git clone https://github.com/Chukwuemeka-Peter-Eze/Docker-nodejs-app.git
```

Navigate into the project directory.

```bash
cd Docker-nodejs-app
```

---

## Repository Cloned Successfully

<p align="center">
  <img src="images/git-clone-repository.png" alt="Git Clone Repository" width="900">
</p>

*The repository cloned successfully and is ready for use.*

---

# Running the Application

The application depends on three services working together:

- MongoDB
- Mongo Express
- Node.js Application

Start each service using the commands below.

---

## Step 1 — Create a Docker Network

Create a custom Docker network so the containers can communicate with one another.

```bash
docker network create mongo-network
```

### Screenshot

<p align="center">
  <img src="images/docker-network-create.png" alt="Docker Network Creation" width="900">
</p>

---

## Step 2 — Start MongoDB

```bash
docker run -d \
-p 27017:27017 \
-e MONGO_INITDB_ROOT_USERNAME=admin \
-e MONGO_INITDB_ROOT_PASSWORD=password \
--name mongodb \
--network mongo-network \
mongo
```

### Screenshot

<p align="center">
  <img src="images/mongodb-container-running.png" alt="MongoDB Container Running" width="900">
</p>

---

## Step 3 — Start Mongo Express

```bash
docker run -d \
-p 8081:8081 \
-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
-e ME_CONFIG_MONGODB_SERVER=mongodb \
--network mongo-network \
--name mongo-express \
mongo-express
```

### Screenshot

<p align="center">
  <img src="images/mongo-express-running.png" alt="Mongo Express Running" width="900">
</p>

---

## Step 4 — Open Mongo Express

Open your browser and navigate to:

```text
http://localhost:8081
```

Create:

- Database: `user-account`
- Collection: `users`

### Screenshot

<p align="center">
  <img src="images/mongo-express-browser.png" alt="Mongo Express Interface" width="900">
</p>

---

## Step 5 — Start the Node.js Application

Navigate to the application directory.

```bash
cd app
```

Install the required dependencies.

```bash
npm install
```

Start the application.

```bash
node server.js
```

---

## Application Running

Open your browser.

```text
http://localhost:3000
```

If everything is configured correctly, the application should load successfully.

<p align="center">
  <img src="images/application-running.png" alt="Node.js Application Running" width="900">
</p>

> **✅ Success**
>
> At this stage, the application is connected to MongoDB and any submitted data is stored in the database. Mongo Express can be used to verify that the records have been saved successfully.

---

# Building the Docker Image

The application can be packaged into a reusable Docker image using the project's Dockerfile.

Run the following command from the project root.

```bash
docker build -t docker-nodejs-app .
```

Docker performs the following actions:

1. Reads the Dockerfile.
2. Downloads the required base image (if necessary).
3. Copies the application source code.
4. Installs project dependencies.
5. Builds the image layers.
6. Creates the final Docker image.

### Screenshot

<p align="center">
  <img src="images/docker-build.png" alt="Docker Build Output" width="900">
</p>

---

## Verify the Image

```bash
docker images
```

You should see the newly created image listed.

### Screenshot

<p align="center">
  <img src="images/docker-images.png" alt="Docker Images" width="900">
</p>

---

## Run the Docker Image

```bash
docker run -d \
-p 3000:3000 \
--name nodejs-app \
docker-nodejs-app
```

### Screenshot

<p align="center">
  <img src="images/docker-run.png" alt="Running Docker Container" width="900">
</p>

---

## Verify the Running Container

```bash
docker ps
```

This confirms that the container is running and the port mapping has been applied successfully.

### Screenshot

<p align="center">
  <img src="images/docker-ps.png" alt="Docker PS Output" width="900">
</p>

---

---

# Managing Docker Containers

Once the application is running, Docker provides several commands to inspect, manage, and troubleshoot containers throughout their lifecycle.

---

## View Running Containers

Display all currently running containers.

```bash
docker ps
```

### Screenshot

<p align="center">
  <img src="images/docker-ps.png" alt="Running Docker Containers" width="900">
</p>

---

## View Container Logs

Inspect application logs.

```bash
docker logs nodejs-app
```

Logs are useful for:

- Verifying application startup
- Identifying runtime errors
- Monitoring application output
- Troubleshooting unexpected behavior

### Screenshot

<p align="center">
  <img src="images/docker-logs.png" alt="Docker Container Logs" width="900">
</p>

---

## Access the Running Container

Open an interactive shell inside the container.

```bash
docker exec -it nodejs-app sh
```

This allows you to:

- Inspect application files
- Verify installed dependencies
- Explore the container filesystem
- Execute diagnostic commands

### Screenshot

<p align="center">
  <img src="images/docker-exec.png" alt="Interactive Docker Shell" width="900">
</p>

---

# Container Lifecycle Management

## Stop the Container

```bash
docker stop nodejs-app
```

Gracefully stops the running container.

---

## Start the Container

```bash
docker start nodejs-app
```

Starts an existing stopped container.

---

## Restart the Container

```bash
docker restart nodejs-app
```

Restarts the running container.

---

## Remove the Container

```bash
docker rm nodejs-app
```

Deletes the container while preserving the Docker image.

---

## Remove the Docker Image

```bash
docker rmi docker-nodejs-app
```

Deletes the Docker image from your local machine.

---

# Common Docker Commands

| Command | Purpose |
|----------|---------|
| `docker --version` | Verify Docker installation |
| `docker info` | Display Docker Engine information |
| `docker build` | Build a Docker image |
| `docker images` | List Docker images |
| `docker run` | Create and start a container |
| `docker ps` | Display running containers |
| `docker ps -a` | Display all containers |
| `docker logs` | View container logs |
| `docker exec -it` | Open a shell inside a running container |
| `docker stop` | Stop a running container |
| `docker start` | Start a stopped container |
| `docker restart` | Restart a container |
| `docker rm` | Remove a container |
| `docker rmi` | Remove a Docker image |

For a complete command reference, see **`docker_commands.md`**.

---

# Screenshot Gallery

This repository includes screenshots documenting the implementation process.

Examples include:

- Docker installation verification
- Docker image build
- Docker image listing
- Running Docker containers
- MongoDB container
- Mongo Express interface
- Node.js application running
- Docker logs
- Interactive Docker shell

---

# Challenges Encountered

During implementation, several common Docker issues were encountered and resolved.

### Container Name Conflict

Attempting to create a container with an existing name resulted in:

```text
Conflict. The container name is already in use.
```

**Resolution**

- Listed existing containers.
- Removed or renamed the conflicting container.
- Restarted the workflow.

---

### Port Already in Use

A running application was already using the selected port.

**Resolution**

- Identified the conflicting process.
- Stopped the process or selected another available port.

---

### Image Build Errors

Some image builds failed because of configuration or dependency issues.

**Resolution**

- Reviewed Docker build output.
- Corrected the Dockerfile.
- Rebuilt the image.

---

### Application Not Loading

The application was inaccessible through the browser.

**Resolution**

- Verified the container was running.
- Confirmed port mappings.
- Reviewed container logs.
- Verified MongoDB connectivity.

---

# Lessons Learned

Completing this project strengthened my understanding of:

- Docker fundamentals
- Docker images and containers
- Writing Dockerfiles
- Building Docker images
- Running containerized applications
- Connecting applications to MongoDB
- Managing container lifecycles
- Inspecting logs
- Interactive debugging
- Technical documentation
- GitHub portfolio development

The project also reinforced the importance of reproducible environments and container-based application deployment.

---

# Future Improvements

Potential enhancements include:

- Multi-stage Docker builds
- Running containers as a non-root user
- Docker health checks
- Environment variable management
- Private container registries
- CI/CD integration
- Kubernetes deployment
- Container image security scanning

---

# Documentation

Additional project documentation is available in the **docs/** directory.

- `commands.md`
- `setup.md`
- `troubleshooting.md`
- `lessons-learned.md`
- `video-script.md`

---

# References

- Docker Documentation
- Docker CLI Reference
- Dockerfile Best Practices
- Node.js Documentation
- Express Documentation
- MongoDB Documentation
- Mongo Express Documentation

---

# Project Summary

This project demonstrates the complete workflow of containerizing a Node.js application using Docker in a local development environment.

The implementation included:

- Writing a Dockerfile
- Building Docker images
- Running Docker containers
- Connecting the application to MongoDB
- Managing data with Mongo Express
- Inspecting logs
- Debugging containers
- Managing the container lifecycle
- Documenting the implementation

This repository represents a practical hands-on Docker project and serves as part of my growing DevOps engineering portfolio.

---

# Connect With Me

If you'd like to discuss Docker, DevOps, Cloud Engineering, or Software Engineering, feel free to connect.

- **GitHub:** https://github.com/Chukwuemeka-Peter-Eze
- **LinkedIn:** https://www.linkedin.com/in/chukwuemekapetereze/

If you found this repository useful, consider giving it a ⭐.