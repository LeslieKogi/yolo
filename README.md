# YOLO E-Commerce (Dockerized Application)

## Project Overview

- The YOLO E-Commerce project is a fully containerized web application that demonstrates the use of Docker and Docker Compose to build, deploy, and orchestrate a multi-service application.

### Components:

- Frontend => React app served via Nginx [port 3000 -> 80]

- Backend => Node.js + Express server [port 5000]

- Database => MongoDB [port 27017]

All the components were separated into micro services and connected using docker networksand volumes to enable them 
to persist data storage and communication between the containers.

### How to run the application

#### prerequisites
- Docker installed in your system
- Docker compose plugin installed

1. Clone the repo

```
git clone https://github.com/LeslieKogi/yolo.git
cd yolo
```
2. Build and start the containers

```
docker compose up
```

## Docker Setup Summary
- There are two docker files, one in the frontend and the other in the backend
- The app uses a shared Docker bridge network (app-net)
- MongoDB uses a volume (app-mong-data) for persistence

There is futher explanation in the explanation.md 

## Folder Structure 

## Repository Structure
```
.
├── ansible.cfg
├── backend
│   ├── Dockerfile
│   ├── models
│   ├── node_modules
│   ├── package.json
│   ├── package-lock.json
│   ├── routes
│   ├── server.js
│   └── upload.js
├── backend-deployment.yaml
├── client
│   ├── Dockerfile
│   ├── node_modules
│   ├── package.json
│   ├── package-lock.json
│   ├── public
│   ├── README.md
│   └── src
├── docker-compose.yaml
├── explanation.md
├── frontend-deployment.yaml
├── hosts
├── image.png
├── inventory.yml
├── playbook.yml
├── README.md
├── roles
│   ├── backend-deployment
│   ├── frontend-deployment
│   └── setup-mongodb
├── Screenshot from 2025-10-07 17-24-29.png
├── Structure
├── Vagrantfile
├── yolo-backend image.png
└── yolo-frontend image.png

```
---

## DockerHub Images 
- Frontend=>	*thandie/yolo-frontend*   	1.0.1
- Backend=>   *thandie/yolo-backend*       1.0.0

![Screenshot of DockerHub showing image ](./yolo-frontend%20image.png)
![Screenshot of DockerHub showing image ](./yolo-backend%20image.png)

# Author
Leslie Kogi