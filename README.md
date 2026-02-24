MEAN Stack Application Deployment on AWS using Docker & Nginx
Project Overview

This project demonstrates the deployment of a MEAN Stack (MongoDB, Express, Angular, Node.js) application on AWS EC2.
The application is fully containerized using Docker and orchestrated with Docker Compose.
Nginx is configured as a reverse proxy to expose the entire application through port 80.

The application provides a CRUD interface for managing tutorials.

Architecture

Browser
│
│ HTTP (Port 80)
▼
Nginx (Reverse Proxy)
├── / → Angular Frontend (4200)
└── /api → Node.js Backend (8080)
                │
                ▼
            MongoDB (27017)

Technology Stack

Frontend: Angular

Backend: Node.js, Express

Database: MongoDB

Containerization: Docker, Docker Compose

Reverse Proxy: Nginx

Cloud Platform: AWS EC2 (Ubuntu 22.04)

AWS EC2 Configuration

Operating System: Ubuntu 22.04

Inbound Security Group Rules:

SSH (22)

HTTP (80)

Frontend (4200) – optional for testing

Backend (8080) – optional for testing

Project Structure

crud-dd-task-mean-app/
├── backend/
│ ├── Dockerfile
│ └── server.js
├── frontend/
│ ├── Dockerfile
│ └── Angular application files
├── docker-compose.yml
└── README.md

Docker Configuration
Backend Service

Runs on port 8080

Connects to MongoDB using Docker service name mongo

Frontend Service

Runs using Angular development server

Bound to 0.0.0.0 for external access

Docker Compose

Services: frontend, backend, mongo

Uses a shared Docker network

Running the Application

docker-compose down
docker-compose up -d --build

Verify running containers:

docker ps

Nginx Reverse Proxy Configuration

Nginx exposes the application through port 80.

/ routes to Angular frontend (4200)

/api routes to Node.js backend (8080)

After configuration:

sudo nginx -t
sudo systemctl restart nginx

Application Access

Frontend UI
http://13.234.114.140

Backend API
http://13.234.114.140/api

Screenshots

frontend_ui_port_80.png

frontend_tutorials_list_port_80.png

frontend_add_tutorial_page.png

backend_api_via_nginx.png

containers_running.png

Key Learnings

Docker container networking using service names

Reverse proxy configuration using Nginx

Debugging 502 Bad Gateway and port mismatch issues

End-to-end cloud deployment on AWS

Conclusion

This project demonstrates a production-style deployment of a MEAN stack application using Docker, Docker Compose, and Nginx on AWS EC2.
The application is accessible through a single HTTP endpoint and follows modern DevOps best practices.

Author

Sudharsan B
