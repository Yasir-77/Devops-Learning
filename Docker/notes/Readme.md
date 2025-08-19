## Chapter 1: Introduction to containers and Docker

### What are containers?

Containers are lightweight, portable, and isolated environments that allow developers to package applications and their dependencies together. This ensures that the application runs consistently across different computing environments, whether it's on a developer's local machine, a testing server, or in production.

![image](https://github.com/user-attachments/assets/10eebf5e-44b7-4f03-a402-00e9755ab01b)

Containers bundle an application with all its dependencies into a single portable unit ensuring that the application runs consistently across different environments. It provides isolation and improves resource efficiency.

Benefits of containers:

- Isolation: Each container runs in isolation from others, meaning it has its own file system, libraries, dependencies, and environment. This allows you to run multiple containers with different configurations on the same machine without conflicts.
- Portability: A containerized application includes all its dependencies, configurations, and settings, so it can run the same way across any environment—whether it's your local laptop, an on-premises server, or a cloud environment.
- Lightweight: Unlike VMs, containers don’t require a full OS for each instance. Instead, they share the host OS kernel, which makes them much more efficient in terms of memory and storage.

### What is Docker?

Docker is an open-source platform that automates the deployment, scaling, and management of applications inside containers. It allows developers to package applications and their dependencies into a standardized unit (a container), ensuring that applications can run consistently in any environment, from a developer's local machine to production servers.

Key Docker components:

- Docker Engine: Docker Engine is the core component of Docker that enables containers to run. This is the core service that runs and manages containers.
- Docker Hub: A repository where you can find and share container images. You can pull public images from Docker Hub (e.g., for web servers like Nginx or databases like MySQL) or push your custom images.
- Docker compose: A tool for defining and running multi container docker applications.

### Images and containers

Images are templates for creating containers, like a snapshot of an application at a certain time. Images are immutable, so they dont change once they are created, only way to change them is to recreate the image. The immutability ensures the application runs consistently no matter where its deployed.

Containers are running instances of the image. Containers are what you actually interact with, they run the application.

An image is created using a Dockerfile. A Dockerfile is a text file that contains instructions for building a Docker image. Each instruction in the Dockerfile creates a new layer in the image.

### Importance in Modern Development

- Simplified Deployment - Applications run consistently across different environments (e.g., development, testing, and production), avoiding the "it works on my machine" issue.
- Imporved effeciency - Traditional virtual machines can be resource heavy and slow to start. Containers share the host OS kernel, making them more lightweight than virtual machines, reducing overhead.
- Enhanced collaboration - Docker makes it easy to share development environments and applications with team members


## IMPORTANT INTERVIEW QUESTION: VMs vs Containers

A virtual machine allows multiple operating systems to run on a single physical machine. At the base you have the infrastructure, this is your physical or virtual hardware. On top of that sits the host operating system which is the primary operating system managing all the resources. Above the host OS is the hypervisor, the hypervisor is responsible for creating and managing virtual machines by allocating resources like CPU, memory and storage. Each virtual machine runs a full guest operating system insolated from the nothers. Within each virtual machine there is a guest operating system which is another operating system running ontop of the host. Each virtual machine would also have its own binaries and libraries and anything else an application needs to run. Within the setup there is strong isolation. Each VM is resource heavy which consumes alot of CPU memory and storage

![image](https://github.com/user-attachments/assets/0e1e91dd-8982-495e-ac5b-7777998f433f)

Containers are a more lightweight and efficient way to isolate applications. They share the host operating systems like VMs, but instead of using a hypervisor, theyll run on the docker engine. The docker engine sits on top of the host operating system and is responsible for running containers. Containers are isolated from each other at a process level, but they share the underlying OS Kernel making them much lighter than VMs. Difference is they dont have guest operating systems because they share the host operating system making them lighter than virtual machines. Within each container you have the application and its dependencies, binaries and libraries. This setup allows containers to start up quickly and use fewer resources compared to VMs

![image](https://github.com/user-attachments/assets/209ad5ec-d370-4c06-81c1-19bf4091bf6b)

###  Key differences between them:

1 - Usage and Startup time:
- VMs are heavier since each VM runs its own operating system. This increases overhead in terms of memory, CPU usage, and disk space. Booting a VM involves starting the entire OS, which can take time.
- Containers are lighter because they share the host's OS kernel. They use less memory and CPU. Containers start almost instantly, as there's no need to boot a full OS.

2 - Isolation:
- VMs provide stronger isolation since each VM runs a separate OS and is abstracted at the hardware level. Better suited for cases where complete isolation between workloads is critical (e.g., multi-tenant environments).
- Containers provide process-level isolation through the use of namespaces and cgroups. This isolation is effective but not as strong as VMs because containers share the OS kernel.

3 - Portability:
- VMs have less portability, can run on different hypervisors and platforms but require hypervisor compatibility. Moving VMs across different environments can be more complex because they carry a full OS and hardware abstraction.
- Containers are highly portable. An application in a container will run the same way regardless of where it's deployed (e.g., on a developer's laptop, in the cloud, or on a production server) as long as there’s a compatible container runtime like Docker.

---

## Chapter 2: Creating Docker images

### Understanding Dockerfile

A Dockerfile is a text file containing instructions on how to build a Docker image. It defines the environment and the steps needed to create a containerized application. Each instruction in the Dockerfile corresponds to a layer in the Docker image, making it easier to manage and track changes.

#### Basic structure:
![image](https://github.com/user-attachments/assets/43d320a0-1095-4d18-b257-08d27e806012)

#### Example Dockerfile:
![image](https://github.com/user-attachments/assets/288d0d9b-0a93-45ef-b2c7-3cb001f1747c)

## Writing a Dockerfile

### First create a docker Git repositry 

Create a docker folder on desktop
```
cd Desktop/Docker
```
Then create a README.md file, Type:
```
echo "# Dockerr Learning" > README.md
```
Then initialise folder as a git repository. Type:
```
git init
```

Then add README.md file to the staging area
```
git add README.md
```

Then commit by typing:
```
git commit -m "Inital commit"
```
Then to change the branch from master to main type:
```
git branch -M main
```

### Creating a simple application to Dockerise

First open the Docker learning file and open the terminal on VSCODE.

Download Python to check this is installed type:
```
python --version
```
Then install Flask, flask is a simple and lightweight framework for creating web applications in Python. type:
```
pip install flask
```
Create a new directory, type:
```
mkdir hello_flask
```
Enter the directory, type:
```
cd hello_flask  
```
Create the appliction type:
```
touch app.py
```
In VSCODE copy the following script in the file:
```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5002)
```
Code breakdown:
from flask import Flask - This imports the Flask class from the flask module, which allows you to create a Flask web application.

app = Flask(__name__) - This line initializes the Flask application by creating an instance of the Flask class. The __name__ variable is used to indicate the name of the module in which the app is being initialized, which helps Flask locate resources.
python

@app.route('/') - This is a route decorator that defines the URL endpoint (/) for this function. In this case, when a user visits the root of the web app (e.g., http://localhost:5002/), this function will be called.

def hello_world():
    return 'Hello, World!'

This is the function that is executed when a user visits the / route. It simply returns the string 'Hello, World!', which is displayed on the webpage.
python

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5002)

This block ensures that the Flask app runs when the script is executed directly.
The app.run() method starts the Flask development server.
host='0.0.0.0': This allows the server to be accessed externally (not just on localhost but also from other devices on the same network).
port=5002: The application will run on port 5002 (instead of Flask's default port 5000).

To run the code type:
```
python app.py
```

### Containerise web application 1:

- First create a dockerfile type:
```
touch Dockerfile
```
- Write out the contents in the Dockerfile:
```
FROM python:3.8-slim
WORKDIR /app
COPY . .
RUN pip install flask
EXPOSE 5002
CMD [ "python", "app.py" ] 
```
FROM python:3.8-slim - This sets the base image to Python 3.8-slim, which is a smaller, lightweight image of Python, making the resulting container more efficient. The slim version contains only the essentials for running Python applications.

WORKDIR /app - This sets the working directory inside the container to /app. Any commands or files copied will now work relative to this directory.

COPY . . - This copies the contents of the current directory (where your Dockerfile and Python code reside) into the container’s /app directory.

RUN pip install flask - This runs the pip install flask command inside the container, installing Flask into the container’s Python environment.

EXPOSE 5002 - This tells Docker that the container will listen on port 5002, which you set in your Flask app (app.run(host='0.0.0.0', port=5002)).

CMD [ "python", "app.py" ] - This defines the command to run when the container starts. In this case, it starts the Flask app by running python app.py.

- Next step is to build the docker image. Go to command line and type:
```
docker build -t hello-flask .
```
**`docker build`** command initiates the build process

**`-t hello-flask`**  the -t tags the image with a name. In this case the name is hello-flask

The **`.`** represents the current directory and tells docker to look for the docker file there.

Docker will execute each intruction in Docker file. Image will be created and ready to use.


### Containerise web application 2:

With the docker image now built it can be run as a container. To run it as a container type:
```
docker run -d -p 5002:5002 hello-flask
```

Breakdown:

**`docker run`**: Starts a new Docker container from an image.

**`-d`**: Runs the container in detached mode, meaning it runs in the background.

**`-p 5002:5002`**: Maps port 5002 on your local machine (host) to port 5002 inside the container. This allows you to access the Flask app from your browser via http://localhost:5002.

**`hello-flask`**: Specifies the name of the image you built earlier, which Docker will use to create and run the container.

To verify docker container is running type:
```
docker ps
```
The container ID will appear aswell as other information

To stop the container use the command **`docker stop`** followed by the container ID.

---

## Chapter 3: Docker networking

### Basic Networking concepts in Docker

- Bridge network - A bridge network is a default network mode for containers on the same machine. containers connected to the bridge network can communicate with eachother using their own IP addresses. It is isolated from your host machine network which provides an extra layer of security.

- Host network - In host mode, a container uses the host machines network directly without any isolation between the container and the host.

- None network - The none network disables all networking for a container. The container can’t communicate with other containers, the host, or external networks.

Docker networking provides flexibility for container-to-container and container-to-host communication, with a range of networking drivers available to suit different use cases.

### Linking containers together

To link the flask application to a MySQL database container follow the following steps:

#### 1 - Modify the file og the existing flask app to connect to a MySQL database. Copy the following code:
```
# app.py

from flask import Flask
import MySQLdb

app = Flask(__name__)

@app.route('/')
def hello_world():
    # Connect to the MySQL database
    db = MySQLdb.connect(
        host="mydb",    # Hostname of the MySQL container
        user="root",    # Username to connect to MySQL
        passwd="My-secret-pw",  # Password for the MySQL user
        db="mysql"      # Name of the database to connect to
    )
    cur = db.cursor()
    cur.execute("SELECT VERSION()")
    version = cur.fetchone()
    return f'Hello, World! MySQL version: {version[0]}'

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5002)
```
Simple breakdown of code:

1. Imports
```
from flask import Flask
import MySQLdb
```
Flask: This is a lightweight Python web framework used to create web applications.

MySQLdb: This module allows the Flask application to connect to a MySQL database. It provides an interface for running SQL queries and interacting with the MySQL server.

2. Connecting to the MySQL Database
```
db = MySQLdb.connect(
    host="mydb",    # Hostname of the MySQL container
    user="root",    # Username to connect to MySQL
    passwd="my-secret-pw",  # Password for the MySQL user
    db="mysql"      # Name of the database to connect to
)
```
- MySQLdb.connect(): This function establishes a connection to the MySQL database.
- host="mydb": The hostname or IP address where the MySQL server is running. In this case, mydb is used, which would be the hostname of the MySQL container in a Docker Compose setup (since the containers are networked together and can communicate using service names).
- user="root": The MySQL username. Here, the root user is used.
- passwd="My-secret-pw": The password for the root user.
- db="mysql": The name of the database to connect to. In this case, it connects to the default mysql database.

#### 2 - Ensure Dockerfile is set up to install the necessary MySQL client library. Type the code: 
```
FROM python:3.8-slim

WORKDIR /app

COPY . .

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config

RUN pip install flask mysqlclient

EXPOSE 5002

CMD ["python", "app.py"]
```
Simple Breakdown of code:

The only changes that are made are:

1. Install System Dependencies
```
RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config
```
- apt-get update: Updates the package lists in the container to ensure you have the latest version information.
- gcc: The GNU C compiler is required because mysqlclient (a Python package that interacts with MySQL/MariaDB) needs to compile C extensions.
- python3-dev: Provides the header files and libraries needed to build Python packages that require compilation, such as mysqlclient.
- libmariadb-dev: Installs the MariaDB development libraries and headers, which are needed to compile the mysqlclient library (since MySQL and MariaDB are compatible).

pkg-config: Helps in managing compilation of libraries by making it easier to include paths and link necessary libraries.

2.  Install Python Dependencies
```
RUN pip install flask mysqlclient
```
pip install: Installs the required Python packages.

flask: The web framework used to create your application.

mysqlclient: A Python package that allows the Flask app to connect to MySQL/MariaDB databases. Since mysqlclient is a C-based library, it needs to be compiled, which is why the necessary system dependencies were installed earlier.

#### Next step is to build and run the updated containers.

1. Create a custom network - a custom network allows containers to communicate with each other using container names instead of IP addresses. In the integrated terminal in VSCode type:
```
docker network create my-custom-network
```
This will craste a custom network that will be used to connect the flask and MySQL containers together.

2. Run the containers:

To run the MySQL container type:
```
docker run -d --name mydb --network my-custom-network -e MYSQL_ROOT_PASSWORD=(My-secret-pw)
```
**`--name mydb`**: This names the container mydb, which makes it easier to refer to this container in commands or when linking other containers to it.

**`--network my-custom-network`**: Specifies the custom Docker network that the container will join. In this case, it will join the network my-custom-network. This network allows containers to communicate with each other by name (like how app.py connects to mydb).

**`-e MYSQL_ROOT_PASSWORD=your_password`**:

This environment variable sets the root password for the MySQL server inside the container. Replace your_password with a secure password of your choice.

#### Build the docker image for the flask app with the updated docker file. Type the following in the VSCode terminal:
```
docker build -t hello-flask-mysql .
```
Then run the flask application type:
```
docker run -d --name myapp2 --network my-custom-network -p 5002:5002 hello-flask-mysql
```

---

## Chapter 4: Docker compose

### Introduction to Docker compose

Docker compose is a tool that allows you to define and manage multi container docker applications. It simplifies the process of setting up and orchestrating multiple services (containers) that need to work together, such as a web server, a database, or other dependencies, all defined in a single file called docker-compose.yml.With Docker Compose, you can manage containers as a group instead of handling each container individually.

Key features:

- Docker-compose.yml file 
- Commands - 
- Networking

### Importance in DevOps:

- Makes Development and testing easier - instead of manually setting everything, you can define everything in a docker-compose.yml file and run a single command to start the environment.
- Ensures consistency - Ensures that everyone in your team is working in the same environment. By definig the environment in a docker-compose.yml file you guarantee that every developer, tester and CICD pipeline uses the exact same setup.
- Enhances teamwork - Becomes easier to share code configurations and the environment set up itself. Docker-compose makes it easier to version control your infrastructure

### Writing a docker-compose.yml

For the Hello World application that connects to MySQL database, a dock-compose.yml file is going to be created that runs both services with just one command

1- Create Docker-compose.yml file
```
touch docker-compose.yml
```
2- Open the file and type the following code:
```
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - mydb

  mydb:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```
Code Breakdown:

1. Version
```
version: '3.8'
```
This specifies the Compose file format version. Version 3.8 is commonly used with newer Docker features, and it ensures compatibility with Docker's latest capabilities.

2. Services
   
The services: section defines the containers that Docker Compose will create and manage. In this case, there are two services: web and db.
```
  web:
    build: .
    ports:
      - "5002:5002"
    depends_on:
      - mydb
```
- build: .: This means Docker will build the web service's image from the Dockerfile located in the current directory (.). This is where the application's source code resides, and the Dockerfile defines how to build the app.
- ports:: The web service will expose port 5002 on the host, mapped to port 5002 inside the container. This allows the Flask app to be accessible at http://localhost:5002.
- depends_on:: This specifies that the web service depends on the mydb service. This means that the mydb container will be started first before the web service. However, this does not wait for the database to be fully ready (i.e., it doesn’t guarantee the MySQL service is ready to accept connections), so you might still need a retry logic in the web app for connecting to the database.

3. Database (MySQL) Service
```
  mydb:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: (My-secret-pw)
```
- image: mysql:5.7: This specifies that the db service will use the MySQL 5.7 image from Docker Hub. This image contains the MySQL server software.
- environment:: This section defines environment variables for the MySQL container.
- MYSQL_ROOT_PASSWORD: This sets the root password for the MySQL server. In this case, it is set to "My-secret-pw". This password will be required to access the MySQL database as the root user.

---

## Chapter 5: Docker registries

### Introduction to registries

A docker registry is a storage and distribution hub for docker images, a system for storing and sharing docker images.

Key features:

- Public registry - Docker Hub is the most widely used public Docker registry provided by Docker Inc. It hosts millions of images that can be freely accessed by anyone.
- Private registry - A private Docker registry can be set up. This is especially useful for organizations that need to store images internally without exposing them to the public.
Tools like Docker Registry (self-hosted) and third-party services (like AWS Elastic Container Registry, Azure Container Registry, Google Container Registry) allow you to maintain your own image storage.

Importance of Docker registries in Devops:

- Streamline deployment: When docker images are stored in the registry, they can be easily accessed and deployed across multiple envirnoments from development to production. Makes it faster and more reliable to roll out new features and updates
- Enhance collaboration: When images are stored in a centralised registry, everyone in your team has access to the same resources. This makes it easier to share and manage images, improving overall teamwork and effieciency .
- Ensures consistency: By storing images in a registry , that exact same image is being used in development, testing and production.


### How to use DockerHub:

DockerHub is a public registry where you can store, share and access docker images.

Reasons why DockerHub is used:
- Accessibiltiy: Since Docker is public, you can easily pull images to start projects
- DockerHub hosts a large collection of community contributed images and official images maintained by trusted resources e.g mysql, neo4j and mongo. They are secure and up to date.
- DockerHub offers a free tier that allows you to host public repositories. Good for open source projects.


1 - On the command line connect DockerHub account to the terminal. Type the following: (Where <Username> enter actual username) Fololwed by your password
```
docker login -u <Username>
```
2 - To push image to DockerHub:

First create a repository on DockerHub by clicking on create repository. Name the repository flask-mysql.

Then you need to build and tag the image from Dockerfile with a specific name and version. Type the following:
```
docker build -t yasircoderco77/flask-mysql:v1 .
```
Once image is built, push it to dockerHub. Type:
```
docker push yasircoderco77/flask-mysql:v1 
```
To pull the image and download it to your local machine. Type:
```
docker pull yasircoderco77/flask-mysql:v1 
```

#### Pushing Images to Amazon ECR:

Step 1 - Create/log in to an Amazon AWS account. Then type in ECR (Elasic Container Registry and click on the service.

Step 2 - Create a private Repository and name it flask-mysql and leave everything else as default.  

Step 3 - Once created click on the repository. On the top right there is a ' View push commands button' click on it.

Step 4 - Follow the steps on the page to Push commands for flask-mysql:

Retrieve an authentication token and authenticate your Docker client to your registry. Use the AWS CLI:
```
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 654654437668.dkr.ecr.us-east-1.amazonaws.com
```
Note: if you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.

Build your Docker image using the following command. For information on building a Docker file from scratch, see the instructions here . You can skip this step if your image has already been built:
```
docker build -t flask-mysql .
```
After the build is completed, tag your image so you can push the image to this repository:
```
docker tag flask-mysql:latest 654654437668.dkr.ecr.us-east-1.amazonaws.com/flask-mysql:latest
```
Run the following command to push this image to your newly created AWS repository:
```
docker push 654654437668.dkr.ecr.us-east-1.amazonaws.com/flask-mysql:latest
```

#### Using image from our ECR Repository

1. Edit the Dockerfile
```
version: '3.8'

services:
  web:
    image: <ECR URL>
    ports:
      - "5002:5002"
    depends_on:
      - mydb

  mydb:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: my-secret-pw
```
Added image: <ECR URL> this is so the image is pulled from the ECR repository instead of building the image that we had locally.

2. Create a custom Docker network
```
docker network create my-app-network
```
This command creates a custom Docker network named my-app-network which allows containers to communicate with each other over this private network.
By connecting containers to the same network, they can communicate using container names instead of IP addresses.

3. Run a MySQL container on the custom network
```
docker run -d --name mydb --network my-app-network -e MYSQL_ROOT_PASSWORD=my-secret-pw mysql:5.7
```
This command runs a MySQL5.7 container in detached mode (-d), naming the container mydb.

The environment variable MYSQL_ROOT_PASSWORD is set to my-secret-pw to configure the MySQL root password.

The container is connected to the my-app-network so that other containers (e.g., your Flask app) can communicate with it by using the container name (mydb).

4. Run a Flask container on the custom network, mapping port 5002 and using the specified image
```
docker run -p 5002:5002 --network my-app-network <ECR URL>
```
This command runs a Flask application that is built into the flask-mysql image hosted in your AWS ECR repository.

The -p 5002:5002 option maps port 5002 on the host machine to port 5002 in the container, making the Flask app accessible from outside the container on port 5002.

The --network my-app-network option connects this container to the same custom network (my-app-network) as the MySQL container.

Inside the Flask app, mydb will be used as the hostname when connecting to the MySQL container.

### Important Docker commands:

**`docker images`** - The docker images command is used to list all the Docker images that are stored locally on your machine. It provides details about each image, such as the repository name, tag, image ID, creation date, and size.

**`docker inspect`** followed by image ID - The docker inspect command provides detailed, low-level information about Docker objects like containers, images, volumes, or networks. The information is returned in JSON format, giving a comprehensive view of the object's configuration and current status.

**`docker rmi`** followed by image ID - The docker rmi command is used to remove Docker images from your local machine. It's useful for cleaning up unused or outdated images to free up disk space.

**`docker system prune`** - The docker system prune command is used to clean up Docker resources that are not in use. It helps free up disk space by removing unused containers, images, networks, and volumes. By default, it removes stopped containers, unused networks, dangling images (untagged), and build caches.

**`docker ps`** - The docker ps command lists all running Docker containers on your system. By default, it shows only containers that are currently up and running.

**`docker stop`** follwed by container ID - The docker stop command is used to stop a running Docker container. When you stop a container, it sends a terminate signal to the container’s main process and allows it to shut down gracefully.

**`docker rm`** followed by container ID - The docker rm command is used to remove a Docker container. This command deletes the container and its metadata, but it does not delete the associated image or volumes unless explicitly specified.

### Multistage builds

Multistage bulds allow you to use multiple from statements in your dockerfile to create multiple build stages. This technique is mainly used to reduce the size of Docker images by separating the build and runtime environments.

The following is the original Dockerfile that was created:
```
FROM python:3.8-slim

WORKDIR /app

COPY . .

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config

RUN pip install flask mysqlclient

EXPOSE 5002

CMD ["python", "app.py"]
```
To utilize the multistage builds the code would change to:
```
# Stage 1: Build stage
FROM python:3.8-slim as build

WORKDIR /app

RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    libmariadb-dev \
    pkg-config

COPY . .

RUN pip install flask mysqlclient

#Stage 2: Production stage

FROM python:3.8-slim

WORKDIR /app

COPY --from=build /app /app

EXPOSE 5002

CMD ["python", "app.py"]
```

Breakdown:

Stage 1 (Build stage):

- You use python:3.8-slim as the base image.

- Install the required packages (like gcc, libmariadb-dev, etc.) to compile the mysqlclient library and other Python dependencies.

- Copy the source code into the /app directory.

- Use pip to install the necessary Python dependencies (flask and mysqlclient).

Stage 2 (Production stage):

- You start with a fresh python:3.8-slim image to avoid having build dependencies (like gcc or python3-dev) in the final production image.

- Use COPY --from=build to copy the application files and the installed dependencies from the first stage (build stage) to the production image.

- Expose port 5002 for the Flask application.

- Use the CMD to run the Flask app.

---

## Chapter 6: Kubernetes Introduction

### What is kubernetes?

Kubernetes (often abbreviated as K8s) is an open-source platform designed to automate the deployment, scaling, and operation of containerized application. It provides advanced features like container orchestration, automatic scaling and self-healing these features ensure application runs smoothly and efficiently.

### Why use kubernetes?

Kubernetes is a powerful amanager that oversees all of your containers. It makes sure all of the containers are deployed correctly, easy to scale up or down and meet demand and automatically recovers from faliure. This level of automation and management is crucial when dealing with complex distributed systems when manual intervention would be time consuming and error prone.

It helps solve the challenges that arise when you move beyond a handful of containers on a single machine to managiong a fleet of machines across multiple machines. Allows focus more on application than the intricacies of managing individual containers.

### Docker swarm vs Kubernetes

Docker Swarm and Kubernetes are both container orchestration platforms designed to manage, deploy, and scale containerized applications. However, they differ significantly in terms of features, complexity, and use cases. Here’s a comparison of Docker Swarm and Kubernetes:

| DockerSwarm  | Kubernetes  | 
|-------|------|
| No auto scaling  | Auto scaling |
| Good community | Great active community | 
| Easy to start a Cluster | Difficult to start a cluster   | 
| Limited to the Docker API's capabilities | Not limited to the Docker API's capabilities   | 

### Why use Orchestration tools?

- Are built to manage large-scale deployments - They can handle a large number of containers spread across multiple machines, this makes it easier to manage complex environments by automating the deployment operation and scaling of containers.
- Ensure High availability - They automatically monitor the state of your containers, they can restart or relocate them in case of faliure, applications can recover without manual intervention.
- Automate scaling and recovery - Orchestration tools monitor resource usage (CPU, memory, etc.) and can scale applications up or down based on real-time demand, ensuring efficient use of resources. Built-in self-healing capabilities automatically replace failed or unhealthy containers to maintain the desired state of the application.
- Simple to use, Enhances reliability and resource utilization.
