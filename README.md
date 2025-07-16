# Case Study for DevSecOps Role at Yarowa AG

This repository is the base for the case study for all potential **DevSecOps engineers** at Yarowa AG.

---

## Requirements

- Node.js  
- Docker  
- Minikube  
- kubectl  
- Helm  
- Helmfile  

---

## Instructions

You can run the application in three ways:

1. **Locally using Node.js**  
2. **In Docker**  
3. **In Kubernetes (via Helm & Helmfile)**  

---

## 🖥️ Option 1: Run the App Locally

```bash
npm install
node index.js

```
# 🚀 Option 2: Run in Kubernetes (Minikube)
 ### You do not need to build any Docker image — it is already pushed to Docker Hub as shahid274/yarowa-app.
###  Step 1: Start Minikube 
 ```bash
minikube start --driver=docker --cpus=2 --memory=4000mb
```
### Step 2: Enable Ingress Addon
 ```bash
minikube addons enable ingress
```
### Step 3: Edit Your Hosts File
Add the following entry to your /etc/hosts file:
 ```bash
sudo nano /etc/hosts
```
Add this line at the end of the file: 
 ```bash
127.0.0.1 casestudy.local.yarowa.io
```
### Step 4: Start Minikube Tunnel
and dont terminate the process, run the commands from step 6 in new terminal
 ```bash
sudo minikube tunnel
 ```

### Step 5: Create Namespace

 ```bash
kubectl create namespace yarowa
 ```
###  Step 6: Deploy Using Helmfile
 ```bash
cd helmfile.d
helmfile apply
 ```
### Verify Deployment
Check that your pods, services, and ingress are running:
 ```bash
kubectl get pods,svc,ing -n yarowa
 ```
### Access the Application
Open your browser and visit:

http://casestudy.local.yarowa.io/






