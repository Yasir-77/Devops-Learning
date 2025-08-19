# Docker & Containers Summary

## 1 Containers & Docker Basics

### Containers
- Lightweight, portable, and isolated environments.
- Bundle application + dependencies → run consistently anywhere.
- **Benefits**:
  - **Isolation**: Separate FS, libraries, configs.
  - **Portability**: Same behavior across dev, test, prod.
  - **Lightweight**: Share host OS kernel → faster & smaller than VMs.

### Docker
- Open-source platform for container automation.
- **Key Components**:
  - **Docker Engine**: Runs/manages containers.
  - **Docker Hub**: Public registry for images.
  - **Docker Compose**: Define/run multi-container apps.

### Images vs Containers
- **Image**: Immutable template (built via `Dockerfile`).
- **Container**: Running instance of an image.

---

## 2 VMs vs Containers (Interview Key Point)

### Virtual Machines
- Each VM has its own **guest OS** + binaries + libraries.
- Heavy (high CPU/memory usage).
- Slower startup (boot full OS).
- Strong isolation (hardware-level).

### Containers
- Share host OS kernel (no guest OS).
- Lightweight, faster startup (seconds).
- Process-level isolation (less strict).
- Highly portable (as long as runtime is available).

---

## 3 Building Docker Images

### Dockerfile
- Defines steps to build images.
- Each instruction = new layer.
- Example (Flask app):
### Commands
- Build: `docker build -t hello-flask .`
- Run: `docker run -d -p 5002:5002 hello-flask`
- Check: `docker ps`

---

## 4. Docker Networking

### Modes
- **Bridge** → default, isolated but containers can talk.
- **Host** → shares host network.
- **None** → no networking.

### Custom Networks
- Allow containers to connect by **name**.
- Example: Flask + MySQL on same custom network.

---

## 5. Docker Compose

### Purpose
- Define & run multi-container apps (`docker-compose.yml`).
- Manages services as a group.

### Benefits
- Simplifies dev/test environments.
- Consistency across teams.
- Easy to share setups.

### Example (Flask + MySQL)

```
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5002:5002"
    depends_on:
      - mydb

  mydb:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```
## 6. Docker Registries

### Types
- **Public** → Docker Hub (official/community images).
- **Private** → AWS ECR, Azure, GCP, self-hosted registries.

### Workflow
- Login:  
  ```bash
  docker login -u <username>

### Tag & Push:
- docker build -t user/repo:tag .
- docker push user/repo:tag


### Pull:
- docker pull user/repo:tag

### Example: AWS ECR

1. Authenticate with AWS CLI.

2. Build & tag image.

3. Push to ECR repo.

4. Pull & run from ECR in Compose.

## 7. Useful Docker Commands

- docker images → list local images.
- docker ps → running containers.
- docker stop <id> → stop container.
- docker rm <id> → remove container.
- docker rmi <id> → remove image.
- docker inspect <id> → inspect details (JSON).
- docker system prune → cleanup unused objects.

## 8. Multistage Builds

### Why?
- Separate build environment (with compilers/tools) from runtime environment.
- - Smaller & cleaner production images.

Example

```
FROM python:3.8-slim as build
WORKDIR /app
RUN apt-get update && apt-get install -y gcc python3-dev libmariadb-dev pkg-config
COPY . .
RUN pip install flask mysqlclient

# Production stage
FROM python:3.8-slim
WORKDIR /app
COPY --from=build /app /app
EXPOSE 5002
CMD ["python", "app.py"]
```

9. Kubernetes Introduction

### What is Kubernetes?
- Open-source container orchestration tool.
- Automates deployment, scaling, self-healing.

### Benefits

- High availability.
- Autoscaling (up/down based on demand).
- Self-healing (restart/replace failed containers).
- Focus on apps, not infra.

### Docker Swarm vs Kubernetes

| Docker Swarm       | Kubernetes              |
|---------------------|-------------------------|
| Easier to set up    | More complex            |
| Limited scaling     | Advanced autoscaling    |
| Good community      | Very large ecosystem    |
| Docker API-based    | Independent, broader capabilities |



