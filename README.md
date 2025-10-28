# YOLO E-Commerce (Dockerized Application)

## Project Overview

This project automates the deployment of the **YOLO e-commerce web application** using **Vagrant**, **Ansible**, and **Docker**.  
It provisions a virtual machine, installs Docker, pulls the necessary container images from Docker Hub, and runs the application stack (MongoDB, backend, frontend) in isolated containers.

The goal of this project is to demonstrate **Infrastructure as Code ** using **Ansible roles**

## Setup Instructions

### 1. Prerequisites
Ensure the following are installed on your host machine:
- Vagrant
- VirtualBox
- Git

### 2. Clone this repository
```bash
git clone https://github.com/LeslieKogi/yolo.git
cd yolo
```

### 3. Start and provision the VM
```bash
vagrant provision
```

### 4.Verify setup
```bash
vagrant ssh
docker ps
```

## Summary

- The Vagrantfile provisions the virtual machine, ansible runs inside the VM
- The playbook executes the roles in sequence(basic-setup -> docker -> database -> backend -> frontend )
- The roles install dependancies, pull images and start containers.
- The application becomes accessible through the forwarded ports.

## Screenshots
- Results of running Vagrant provision
 ![Sucessful vagrant provision](./sucessful%20provision.png)

- Containers running in VM
 ![Containers running in VM ](./VM%20containers.png)

### Author 
Leslie Kogi