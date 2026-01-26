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
#  Install Java

```bash

sudo amazon-linux-extras install java-openjdk11 -y

```

# Check version:

```bash

java -version

```

 # Jenkins Server Setup (on Amazon Linux AMI)
 
 Connect to EC2 (Jenkins server)

 ```bash

chmod 400 your-key.pem
ssh -i your-key.pem ec2-user@<your-jenkins-ec2-public-ip>

```

# Update system packages
 
```bash

sudo yum update -y

```

# Install Java (required for Jenkins)

```bash

sudo amazon-linux-extras install java-openjdk17 -y

```
# Check version:

```bash

java -version

```
# Install Jenkins

 ```bash

sudo wget -O /etc/yum.repos.d/jenkins.repo \

    https://pkg.jenkins.io/redhat-stable/jenkins.repo

sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

sudo yum upgrade -y

sudo yum install jenkins -y

```bash

 Start Jenkins service

```bash

sudo systemctl start jenkins

sudo systemctl enable jenkins

sudo systemctl status jenkins

```

# Open Jenkins in Browser

```bash

http://<your-jenkins-ec2-public-ip>:8080

```

# Get Jenkins initial password

```bash
 
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

```

# Install Docker

```bash

sudo apt install docker.io -y

```

# Install kubectl

```bash

sudo apt install -y apt-transport-https ca-certificates curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt update && sudo apt install -y kubectl

```
# Install AWS CLI (for EKS)

```bash

sudo apt install awscli -y

```

# Install eksctl

```bash

curl -sL "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz
sudo mv eksctl /usr/local/bin

```

# Create an EKS Cluster 

```bash

eksctl create cluster --name devops-cluster --region us-east-1 --nodes 2

```
# To check the cluster 

```bash

kubectl get nodes

```

