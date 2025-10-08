### Explanation

## Choice of base image
1. For yolo-backend :
 - I changed the base image from **node:14** to **node:14-slim**, which is a lighter, minimal variant of Node.js 14.
   This helps reduce the overall image size while providing all the necessary dependancies for running a Node.js server.

 - Multi- stage build was used to reduce the size of an image .I used  **alpine 3.16.7** which is lightweight.

2. For yolo-frontend :
 -  I retained the **node:14-slim** base image for the build stage since it is efficient and works well for building React applications.

 - For the production stage, I switched to **nginx:alpine** instead of **alpine:3.16.7**, because nginx is optimized for serving static files efficiently. (using it also reduces the size of the image)

## Dockerfile directives used
- I retained most of the directives used in the original repository.
---
1. *FROM* [It specifies the base image which the new image will be built on]
2. *WORKDIR* [It sets the working directory in the container]
3. *COPY* [It coppies the files containing the dependancies into the container ]
4. *RUN* [used to run application dependancies or build the application during image creation ]
5. *EXPOSE* [used to expose the port the app runs on]
6. *CMD* [used to define the command that will run the application]

## Docker-compose networking
- I used a custom bridge network **app-net** that allows inter-container communication.Port mapping made the service acessible externaly

- Port 3000 on the host maps to port 80 in the frontend container, for acessing the React app through the browser.
- Port 5000 maps to the backent API 
- Port 27017 exposes the MongoDB service

## Docker volumes 
- I defined a docker volume called **app-mongo-data** which is mounted inside the MongoDB container **app-ip-mongo**
the volume is used for data persistence.

## Running the appliaction
- The application successfully runs from three containers:

yolo-frontend (React)

yolo-backend (Node.js/Express)

app-mongo (MongoDB)

- Each container runs as an isolated microservice connected through a custom bridge network (app-net)
- The frontend loads correctly on the browser through port 3000 (mapped from container port 80).
- The backend server runs on port 5000, responding with “Cannot GET /”, which indicates the service is active.
- The backend logs show “Database connected successfully,” confirming a working connection to MongoDB
- Although the frontend currently loads and the containers communicate, the product data is not yet displaying on the UI
 *What I did to attempt resoleve the issue* - Updated the API URLs inside the frontend’s fetching components to use the internal Docker service name (yolo-backend) instead of localhost . I also Modified the proxy URL inside client/package.json from
"proxy": "http://localhost:5000" to "proxy": "http://yolo-backend:5000"

# Deployment of images 
- I tagged the images over semver conventions. 

- Below are the screenshots of my images on Dockerhub
--- 
![Screenshot of DockerHub showing image ](./Screenshot%20from%202025-10-07%2017-24-29.png)
![Screenshot of DockerHub showing image ](./yolo-frontend%20image.png)
![Screenshot of DockerHub showing image ](./yolo-backend%20image.png)





