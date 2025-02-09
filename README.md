# Docker Tutorial with Spring Boot: A Beginner-Friendly Guide

## Introduction to Docker

Docker is an open-source platform that helps developers package applications with all dependencies into containers. These containers ensure that applications run seamlessly across different environments (development, testing, and production).

## Why Use Docker?

*   **Portability:** Containers run consistently across different systems.
*   **Efficiency:** Shares the host OS kernel, making it lightweight.
*   **Scalability:** Easily scale applications in production environments.
*   **Consistency:** Eliminates dependency issues.

## Key Docker Concepts

*   **Dockerfile:** A script containing instructions to build a Docker image.
*   **Docker Image:** A blueprint of the application, created from a Dockerfile.
*   **Docker Container:** A running instance of a Docker image.
*   **Docker Hub:** A repository for storing and sharing images.

## Setting Up Docker

**Installation (Windows & macOS):**

1.  Download and Install Docker Desktop:
    *   [Windows](https://www.docker.com/products/docker-desktop)
    *   [Mac](https://www.docker.com/products/docker-desktop)
2.  Enable WSL2 backend (For Windows users).
3.  Verify installation by running: `docker --version`

## Dockerizing a Spring Boot Application

**Step 1: Create a Spring Boot Application**

Generate a project from [Spring Initializr](https://start.spring.io/) with dependencies like Spring Web and Spring Boot DevTools.

**Step 2: Write the Dockerfile**

Inside your project root folder, create a file named `Dockerfile` and add:

```dockerfile
# Use an official OpenJDK runtime as a parent image
FROM openjdk:17

# Set the working directory inside the container
WORKDIR /app

# Copy the JAR file from the target folder into the container
COPY target/myapp.jar app.jar  # Replace myapp.jar with your JAR file name

# Expose port 8080 for the application
EXPOSE 8080

# Command to run the application
CMD ["java", "-jar", "app.jar"]



# Dockerizing a Spring Boot Application

## Step 3: Build the Docker Image

Ensure your Spring Boot project is compiled, and the JAR file is available in the `target/` directory. Run:

```bash
docker build -t springboot-app .  # Replace springboot-app with your desired image name
```

## Step 4: Run the Docker Container

```bash
docker run -p 8080:8080 springboot-app  # Replace springboot-app with your image name
```
Now, your application will be accessible at [http://localhost:8080](http://localhost:8080).

## Step 5: Verify Running Containers

```bash
docker ps
```
To stop and remove the container:

```bash
docker stop <container_id>
docker rm <container_id>
```

## Pushing Image to Docker Hub

### Log in to Docker Hub:
```bash
docker login
```

### Tag the image:
```bash
docker tag springboot-app your-dockerhub-username/springboot-app  # Replace with your Docker Hub username
```

### Push the image:
```bash
docker push your-dockerhub-username/springboot-app
```

## Basic Docker Commands

| Command | Description |
|---------|-------------|
| `docker pull <image>` | Downloads an image from Docker Hub |
| `docker images` | Lists available images |
| `docker ps` | Lists running containers |
| `docker ps -a` | Lists all containers (including stopped ones) |
| `docker run -d --name <container_name> <image>` | Runs a container in detached mode |
| `docker stop <container_name>` | Stops a running container |
| `docker rm <container_name>` | Removes a container |
| `docker rmi <image_name>` | Removes an image |
| `docker exec -it <container_name> bash` | Access the terminal of a running container |

## Conclusion
By following these steps, you have successfully Dockerized a Spring Boot application! Docker ensures your application runs in a consistent environment, eliminating dependency conflicts and making deployments easier.

🚀 **Next Steps**: Try deploying the Docker container on AWS, Kubernetes, or a cloud platform.
