# Java Spring Boot - Dockerised REST API

A Spring Boot REST API containerised with Docker.  
Built as part of my hands-on Docker upskilling — June 2026.

---

## Author

**Shyam Sunder Kavali**  
Senior Java Application Engineer | kavalishyam@gmail.com

---

## What This Project Does

A REST API built with Spring Boot, packaged as a JAR, and containerised using Docker.  
Demonstrates end-to-end containerisation of a Java application — from source code to running container.

---

## Tech Stack

| Technology | Version |
|---|---|
| Java | 17 |
| Spring Boot | 3.2 |
| Maven | 3.9 |
| Docker | 28 |
| Embedded Server | Apache Tomcat (included in Spring Boot) |

---

## How To Run

### Prerequisites
- Docker installed on your machine — https://www.docker.com/products/docker-desktop

### Step 1 — Clone the repository
git clone https://github.com/your-username/java-docker-demo.git
cd java-docker-demo

### Step 2 — Build the JAR
mvnw package -DskipTests

### Step 3 — Build the Docker image
docker build -t shyam-demo-app .

### Step 4 — Run the container
docker run -d -p 8080:8080 --name shyam-app shyam-demo-app

### Step 5 — Test the API
Open your browser and go to:
http://localhost:8080/hello

Expected response:
Hello from Docker - Shyam Sunder Kavali

---

## Project Structure

java-docker-demo/
├── src/
│   └── main/
│       └── java/
│           └── com/shyam/demo/
│               └── DemoApplication.java
├── Dockerfile
├── pom.xml
└── README.md

---

## Dockerfile Explained

FROM openjdk:17-jdk-slim
Sets the base image — minimal Linux with Java 17 pre-installed.
No manual Java installation needed.

WORKDIR /app
Creates and sets the working directory inside the container.
All subsequent commands run from here.

COPY target/demo-0.0.1-SNAPSHOT.jar app.jar
Copies the Maven-built JAR from the host machine into the container.
The JAR contains the application code plus embedded Tomcat server.

EXPOSE 8080
Documents that the container listens on port 8080.
Spring Boot's embedded Tomcat uses this port by default.

ENTRYPOINT ["java", "-jar", "app.jar"]
The command that runs when the container starts.
Starts the Spring Boot application with embedded Tomcat.

---

## Key Docker Commands Used

| Command | Purpose |
|---|---|
| docker build -t shyam-demo-app . | Build image from Dockerfile |
| docker run -d -p 8080:8080 --name shyam-app shyam-demo-app | Run container in background |
| docker ps | List running containers |
| docker ps -a | List all containers including stopped |
| docker stop shyam-app | Stop the container |
| docker rm shyam-app | Remove the container |
| docker images | List all images on machine |
| docker logs shyam-app | View container logs |

---

## Why Docker For Java Applications

Traditional Java deplo