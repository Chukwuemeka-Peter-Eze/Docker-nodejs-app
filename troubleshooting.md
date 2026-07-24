# Troubleshooting Guide

This document outlines common issues that may occur while building, running, and managing the Dockerized Node.js application. It also provides likely causes, diagnostic steps, and recommended resolutions based on the implementation performed in this project.

---

# Table of Contents

- Docker Installation Issues
- Docker Service Issues
- Image Build Failures
- Container Startup Failures
- Port Binding Errors
- Application Not Accessible
- Container Exits Immediately
- Docker Logs
- Interactive Debugging
- Network Connectivity Issues
- Image Management Issues
- Cleanup Issues
- Troubleshooting Workflow
- Best Practices

---

# Troubleshooting Methodology

Whenever an issue occurs, follow a structured troubleshooting process instead of making random changes.

```text
Issue Detected
      │
      ▼
Read Error Message
      │
      ▼
Check Docker Service
      │
      ▼
Verify Docker Image
      │
      ▼
Verify Running Containers
      │
      ▼
Review Container Logs
      │
      ▼
Access Running Container
      │
      ▼
Identify Root Cause
      │
      ▼
Apply Solution
      │
      ▼
Rebuild Image (if necessary)
      │
      ▼
Redeploy Container
```

---

# Issue 1 — Docker Command Not Found

## Symptoms

```text
docker: command not found
```

## Possible Cause

Docker is not installed or the executable is not available in the system PATH.

## Resolution

Verify the installation.

```bash
docker --version
```

If Docker is not installed, install Docker Engine before continuing.

---

# Issue 2 — Docker Service Not Running

## Symptoms

```text
Cannot connect to the Docker daemon
```

## Possible Cause

The Docker daemon is stopped.

## Diagnostic Command

```bash
docker info
```

## Resolution

Start the Docker service and verify it is running before executing Docker commands.

---

# Issue 3 — Docker Image Build Failed

## Symptoms

The image fails to build successfully.

## Possible Causes

- Dockerfile syntax error
- Missing project files
- Invalid build context
- Dependency installation failure

## Diagnostic Steps

Review the build output carefully.

```bash
docker build -t docker-nodejs-app .
```

Correct the reported issue and rebuild the image.

---

# Issue 4 — Image Not Found

## Symptoms

```text
Unable to find image
```

## Possible Cause

The image has not been built or the image name is incorrect.

## Resolution

Verify available images.

```bash
docker images
```

If necessary, rebuild the image.

---

# Issue 5 — Container Does Not Start

## Symptoms

The container exits immediately after creation.

## Possible Causes

- Incorrect startup command
- Missing dependency
- Application crash
- Incorrect configuration

## Diagnostic Commands

```bash
docker ps -a

docker logs nodejs-app
```

Review the logs and correct the application or Dockerfile before rebuilding.

---

# Issue 6 — Port Already Allocated

## Symptoms

```text
Bind for 0.0.0.0:3000 failed
```

## Possible Cause

Another application is already using the requested port.

## Resolution Options

Option 1

Stop the conflicting application.

Option 2

Run the container using a different host port.

Example

```bash
docker run -d -p 8080:3000 docker-nodejs-app
```

---

# Issue 7 — Application Cannot Be Accessed

## Symptoms

Browser displays:

- Connection refused
- Timeout
- Page cannot be reached

## Possible Causes

- Container not running
- Incorrect port mapping
- Application listening on another port
- EC2 security group not allowing inbound traffic

## Diagnostic Commands

```bash
docker ps

docker logs nodejs-app
```

Verify:

- Container status
- Port mapping
- Application startup
- AWS security group configuration

---

# Issue 8 — Container Stops Unexpectedly

## Symptoms

Container status changes to Exited.

## Possible Causes

- Runtime exception
- Application crash
- Missing environment configuration
- Startup failure

## Diagnostic Steps

Review container logs.

```bash
docker logs nodejs-app
```

Resolve the underlying application issue before restarting the container.

---

# Issue 9 — Unable to Enter the Container

## Symptoms

```text
No such container
```

## Possible Cause

The container is not running or the container name is incorrect.

## Diagnostic Commands

```bash
docker ps

docker ps -a
```

Restart the container if necessary.

---

# Issue 10 — Changes Not Reflected

## Symptoms

Application changes are not visible after updating the source code.

## Possible Cause

The Docker image was not rebuilt.

## Resolution

Rebuild the image.

```bash
docker build -t docker-nodejs-app .
```

Remove the old container.

```bash
docker rm nodejs-app
```

Run a new container from the updated image.

---

# Issue 11 — Docker Logs Show Errors

## Diagnostic Command

```bash
docker logs nodejs-app
```

Review:

- Startup messages
- Missing modules
- Runtime exceptions
- Port conflicts
- Configuration errors

Logs often provide the quickest indication of the underlying problem.

---

# Issue 12 — Interactive Debugging

Access the running container.

```bash
docker exec -it nodejs-app sh
```

Useful checks include:

- Verify application files
- Confirm installed dependencies
- Inspect environment variables
- Review log files
- Execute diagnostic commands

---

# Issue 13 — Image Consumes Excessive Disk Space

## Diagnostic Command

```bash
docker images
```

Identify unused images.

Remove unnecessary images.

```bash
docker image prune
```

Or remove all unused images.

```bash
docker system prune -a
```

---

# Issue 14 — Too Many Stopped Containers

List all containers.

```bash
docker ps -a
```

Remove stopped containers.

```bash
docker container prune
```

---

# Issue 15 — General Docker Cleanup

Free unused resources.

```bash
docker system prune
```

To remove unused images as well.

```bash
docker system prune -a
```

To remove unused volumes.

```bash
docker volume prune
```

---

# Useful Diagnostic Commands

| Command | Purpose |
|----------|---------|
| `docker info` | Verify Docker Engine |
| `docker images` | Verify images |
| `docker ps` | View running containers |
| `docker ps -a` | View all containers |
| `docker logs` | Inspect application logs |
| `docker exec -it` | Interactive debugging |
| `docker inspect` | View detailed container configuration |
| `docker stats` | Monitor resource usage |
| `docker top` | View running processes |
| `docker system df` | Check Docker disk usage |

---

# Troubleshooting Checklist

Before rebuilding the project, verify the following:

- Docker Engine is installed.
- Docker daemon is running.
- Dockerfile exists.
- Image builds successfully.
- Image appears in `docker images`.
- Container starts successfully.
- Container appears in `docker ps`.
- Correct ports are mapped.
- AWS security group allows application traffic.
- Application responds through the browser.
- Logs contain no critical errors.

---

# Best Practices for Troubleshooting

- Read the complete error message before making changes.
- Verify one component at a time (Docker service, image, container, application).
- Use `docker logs` as the first source of diagnostic information.
- Avoid making multiple configuration changes simultaneously.
- Rebuild the image after modifying the Dockerfile or application source code.
- Remove obsolete containers to prevent confusion during testing.
- Keep Docker images and containers organized with meaningful names and tags.
- Document recurring issues and their resolutions for future reference.

---

# Conclusion

Effective troubleshooting is a critical DevOps skill. By following a structured diagnostic process and using Docker's built-in tools, most issues can be identified and resolved quickly. This guide provides a repeatable approach to diagnosing container, image, and runtime problems while maintaining a reliable and reproducible deployment workflow.
