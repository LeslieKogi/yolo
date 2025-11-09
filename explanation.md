## Choice of Kubernetes Objects
- **Deployments** for frontend and backend to allow rolling updates and high availability.
- **StatefulSet** for MongoDB to ensure persistent data storage across pod restarts.

## Method to Expose Pods
- Used **LoadBalancer Services** to expose both backend and frontend to external traffic.

## Persistent Storage
- MongoDB StatefulSet uses a PersistentVolumeClaim to preserve data if the pod restarts.

## Git Workflow
- Project developed locally in VS Code.  
- Images built with Docker and pushed to Artifact Registry.  
- Manifests applied from Google Cloud Shell.  


## Debugging Measures
- Checked pod logs  
- Validated service exposure   
- Identified CORS issue causing frontend to fail data fetch.

## Note
Before deploying to GKE, I tested the setup locally using Minikube. The application ran successfully, and I was able to view the products from the backend on the frontend interface. This confirmed that the services and routes were functioning correctly in a local Kubernetes environment before moving to the cloud.

![Sucessful deployment](./added%20products.png)
