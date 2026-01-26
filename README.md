This project demonstrates a 3-tier web application deployed on AWS EKS, consisting of:

Frontend: React application served via NGINX

Backend: Node.js + Express REST API

Database: MongoDB

CI/CD: Jenkins pipeline

Container Orchestration: Kubernetes (EKS)

The application is exposed externally using ALB, while internal service communication happens via Kubernetes services.

# Frontend (React + NGINX)

 Built using React

 Served as static files using NGINX

 Proxies /api requests to backend service

 # Backend (Node.js + Express)

 REST API built using Express

 Uses Mongoose to connect to MongoDB

 Exposed internally via ClusterIP service

# Backend dependencies

express

mongoose

cors

# Database (MongoDB)

Runs inside Kubernetes

Uses Persistent Volume + PVC

Accessed only by backend service

# CI/CD (Jenkins)

Jenkins pipeline:

Pulls code from GitHub

Builds Docker images

Pushes images to Docker Hub / ECR

Deploys to EKS using kubectl

# Kubernetes (EKS)

Cluster created using AWS

Worker nodes across multiple AZs

Frontend and backend deployed as Deployments

MongoDB deployed as StatefulSet
