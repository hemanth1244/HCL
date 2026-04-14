# 🚀 DevOps CI/CD Deployment Project – Trend Application

---

## 📌 Project Overview

This project demonstrates an **end-to-end DevOps CI/CD pipeline** to deploy a production-ready application using modern cloud-native tools.

### 🔧 Technologies Used

* GitHub (Version Control)
* Docker (Containerization)
* Jenkins (CI/CD Automation)
* Terraform (Infrastructure as Code)
* AWS EKS (Kubernetes Cluster)
* Kubernetes (Deployment & Service)
* AWS LoadBalancer (External Access)

---

## 📁 Repository Structure

```
Trend/
│── dist/                # Production build files
│── k8s/                 # Kubernetes YAML files
│── terraform/           # Infrastructure as Code
│── Dockerfile           # Docker build file
│── Jenkinsfile          # CI/CD pipeline
│── nginx.conf           # Nginx configuration
│── README.md            # Documentation
```

---

## ⚙️ Pre-requisites

* AWS Account
* EC2 Instance (Jenkins Server)
* Docker installed
* kubectl installed
* AWS CLI configured
* Jenkins installed
* DockerHub account

---

# 🏗️ Terraform – Infrastructure Setup

## 📌 Purpose

Terraform is used to **provision AWS infrastructure** required for this project.

### 🔧 Resources Created

* VPC & Subnets
* Internet Gateway
* Route Tables
* Security Groups
* EC2 Instance (Jenkins Server)
* IAM Roles

---

## 🚀 Terraform Commands

### Initialize

```bash
terraform init
```

### Validate

```bash
terraform validate
```

### Plan

```bash
terraform plan
```

### Apply

```bash
terraform apply
```

Type:

```text
yes
```

---

## 🧹 Destroy (Cost Saving)

```bash
terraform destroy
```

---

## 🔐 IAM Role Used

```text
trend-jenkins-ec2-role
```

---

## 🎯 Terraform Workflow

1. Provision infrastructure using Terraform
2. Launch EC2 instance
3. Install Jenkins on EC2
4. Use Jenkins for CI/CD pipeline

---

# 🐳 Docker Setup

### Build Image

```bash
docker build -t hemanth10bh1010/trend-app .
```

### Push to DockerHub

```bash
docker push hemanth10bh1010/trend-app:latest
```

---

# 🔄 Jenkins CI/CD Pipeline

## 📌 Pipeline Stages

1. Checkout Code from GitHub
2. Build Docker Image
3. Push Image to DockerHub
4. Update kubeconfig
5. Deploy to EKS
6. Verify Deployment

---

## 🔗 GitHub Webhook

Configured webhook to trigger Jenkins automatically on every push:

```text
http://43.204.19.97:8080/github-webhook/
```

---

# ☸️ Kubernetes Deployment

### Apply YAML files

```bash
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

---

## 🔍 Verify Deployment

```bash
kubectl get pods -n trend
kubectl get svc -n trend
```

---

# 🌍 Application Access

## 🔗 LoadBalancer URL

```
http://a1b5bdf47b39742fb96b005da5fb8a6e-fa6387083b4c932b.elb.ap-south-1.amazonaws.com:3000
```

---

# 📊 Monitoring (Optional)

* kubectl logs
* kubectl describe
* AWS CloudWatch

---

# 🎯 Key Achievements

✔ Automated CI/CD pipeline using Jenkins
✔ Dockerized application
✔ Infrastructure provisioned using Terraform
✔ Deployed on AWS EKS
✔ Exposed using LoadBalancer
✔ GitHub webhook integration

---

# 📸 Screenshots (Add These)

* Jenkins Pipeline Success
* Pods Running
* Service LoadBalancer
* Application UI in Browser

---

# 🏁 Conclusion

Successfully implemented a **complete DevOps pipeline** integrating:

* Infrastructure provisioning (Terraform)
* CI/CD automation (Jenkins)
* Containerization (Docker)
* Container orchestration (Kubernetes on EKS)

---

# 💡 Interview Explanation

> This project automates the deployment of an application using Jenkins CI/CD. Code is pushed to GitHub, which triggers Jenkins via webhook. Jenkins builds a Docker image, pushes it to DockerHub, and deploys it to AWS EKS using Kubernetes manifests. Terraform is used to provision infrastructure like EC2 and IAM roles. The application is exposed using a LoadBalancer.

---


---

