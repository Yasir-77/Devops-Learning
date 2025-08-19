# 🐳 Docker essentials

This resource is designed to help you understand containerization, simplify application deployment, and build a strong foundation in Docker—one of the most powerful tools in modern software development and DevOps.

---

## 📚 Table of contents:

### [Chapter 1: Introduction to Containers and Docker](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-1-introduction-to-containers-and-docker)

### [Chapter 2: Creating Docker images](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-2-creating-docker-images)

### [Chapter 3: Docker networking](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-3-docker-networking)

### [Chapter 4: Docker compose](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-4-docker-compose)

### [Chapter 5: Docker registries](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-5-docker-registries)

### [Chapter 6: Kubernetes Introduction](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-6-kubernetes-introduction)

---

### [Chapter 1: Introduction to Containers and Docker](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-1-introduction-to-containers-and-docker)
- What are containers?
- What is Docker?
- Images and containers
- Importance in Modern Development
- IMPORTANT INTERVIEW QUESTION: VMs vs Containers

### [Chapter 2: Creating Docker images](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-2-creating-docker-images)
- Understanding Dockerfile
- Writing a Dockerfile
- Creating a simple application to Dockerise
- Containerise web application 

### [Chapter 3: Docker networking](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-3-docker-networking)
- Basic Networking concepts in Docker
- Linking containers together

### [Chapter 4: Docker compose](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-4-docker-compose)
- Introduction to Docker compose
- Writing a docker-compose.yml
- Importance in DevOps:

### [Chapter 5: Docker registries](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-5-docker-registries)
- Introduction to registries
- How to use DockerHub
- Pushing Images to Amazon ECR
- Using image from our ECR Repository
- Important Docker commands
- Multistage builds

### [Chapter 6: Kubernetes Introduction](https://github.com/Yasir-77/Devops-Learning/tree/main/Docker/notes#chapter-6-kubernetes-introduction)
- What is kubernetes?
- Why use kubernetes?
- Docker swarm vs Kubernetes
- Why use Orchestration tools?

---

## 🚀 Hands-on Project: CoderCo Containers Challenge

To reinforce the concepts in this guide, I completed a **multi-container Docker project** that ties everything together:

### Project Overview
- **Application:** A simple Python Flask web app with two routes:  
  - `/` → Displays a welcome message  
  - `/count` → Increments & displays a visit counter stored in Redis  
- **Database:** Redis is used as a key-value store for tracking visits  
- **Containerization:** Both Flask and Redis are dockerized with their own Dockerfiles  
- **Orchestration:** Docker Compose manages the multi-container setup  

### 🔹 Features Implemented
- ✅ Flask + Redis integration  
- ✅ Dockerized both services  
- ✅ Managed using **docker-compose**  
- ✅ Persistent Redis storage using volumes  
- ✅ Environment variables for flexible Redis connection config  
- ✅ Scaled Flask service to multiple instances with load balancing  

👉 Check out the project here: [CoderCo Containers Challenge](https://github.com/Yasir-77/docker-learning2/tree/main/coderco-challenge)



