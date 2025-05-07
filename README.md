# SIT323 - Week 10 Task: Cloud Native Application Deployment

## Overview

This project involved creating a simple Node.js application, containerizing it using Docker, deploying it on a Kubernetes cluster on Google Cloud Platform (GCP), and enabling monitoring and logging using GCP’s built-in tools.

## Steps I followed to complete the task

1. **Created a Simple Node.js Application**
   - Developed a basic Express server (`server.js`) that responds with "Hello from Node.js app" on port 3000.

2. **Created a Dockerfile**
   - Used Node.js base image.
   - Installed dependencies and copied the app files.
   - Exposed port 3000 and started the server.

3. **Built and Pushed Docker Image to Google Container Registry (GCR)**
   - Command used for the same:
    
     docker build -t gcr.io/[PROJECT_ID]/monitoring-app .
     docker push gcr.io/[PROJECT_ID]/monitoring-app
    

4. **Created a Kubernetes Cluster on GCP**
   - Command used:
      gcloud container clusters create monitoring-cluster \
       --zone=asia-southeast1-a \
       --num-nodes=1 \
       --machine-type=e2-micro \
       --disk-size=12 \
       --release-channel=regular \
       --logging=SYSTEM \
       --monitoring=SYSTEM
     ```

5. **Wrote Kubernetes Deployment and Service Files**
   - `deployment.yaml`: Deployed the container using `gcr.io/[PROJECT_ID]/monitoring-app`.
   - `service.yaml`: Exposed the application to the internet using a LoadBalancer.

6. **Applied Kubernetes Configurations**
   - Deployed the application using the following two commands:
    
     kubectl apply -f deployment.yaml
     kubectl apply -f service.yaml
    

7. **Verified Application Deployment**
   - Checked deployment and pods using `kubectl get all`.
   - Accessed the external IP from the LoadBalancer service to view the running application.

8. **Enabled Monitoring and Logging**
   - Used GCP's built-in **Cloud Monitoring** and **Cloud Logging** (through Stackdriver).
   - Verified logs and metrics in the GCP console.
   - Took screenshots of dashboards and logs as evidence.

9. **Deleted the Cluster After Use to Save Resources**
   Lastly I deleted the cluster by typing the following command: 
    
     gcloud container clusters delete monitoring-cluster --zone=asia-southeast1-a
    

