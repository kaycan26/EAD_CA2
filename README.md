# EAD CA2 - Microservices CI/CD Deployment

## Overview
This project implements a microservice-based architecture for a Recipe Tracker application.  
The system is composed of three main components:

- Frontend (Node.js)
- Backend (Spring Boot)
- MongoDB database

The application allows users to create and view recipes through a web interface, with data persisted in a NoSQL database.

---

## Architecture
The system follows a layered microservices architecture:

Frontend → Backend → Database (MongoDB)

- The **frontend** provides the user interface.
- The **backend** exposes REST APIs and handles business logic.
- The **database** stores recipe data.

---

## Features
The following DevOps and cloud-native practices are implemented:

- Docker containerisation of all services
- Docker Compose for multi-container orchestration
- CI/CD pipeline using GitHub Actions
- Automated Docker image build and push to Docker Hub
- DevSecOps integration using Trivy security scanning
- Environment-based configuration using Spring Boot

---

## Services

 Service    URL / Port 

 Frontend  http://localhost:22137 
 Backend   http://localhost:8080 
 Database  MongoDB (port 27017) 

---

## CI/CD Pipeline

The CI/CD pipeline is implemented using **GitHub Actions** and performs the following steps:

1. Checkout source code from repository  
2. Build backend and frontend services  
3. Build Docker images for each service  
4. Authenticate with Docker Hub using repository secrets  
5. Push images to Docker Hub repositories  
6. Perform vulnerability scanning using Trivy  

### Pipeline Outcome
This pipeline ensures that the application is:

- Automatically built on each change
- Consistently deployed using containers
- Continuously checked for security vulnerabilities

---

## Security (DevSecOps)

Security is integrated into the CI/CD pipeline using **Trivy**, which scans Docker images for vulnerabilities.

- Scans both backend and frontend images  
- Detects vulnerabilities in OS packages and dependencies  
- Focuses on HIGH and CRITICAL severity issues  
- Ensures secure deployment practices  

Secrets such as Docker credentials are securely stored using **GitHub Actions Secrets**.

---

## How to Run the Application

To run the full application locally:

```bash
docker compose up --build