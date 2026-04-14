# 🚀 DevOps CI/CD Deployment Project – Trend Application

## 📌 Project Overview

This project demonstrates a complete **DevOps CI/CD pipeline** for deploying a production-ready application using:

* GitHub (Version Control)
* Docker (Containerization)
* Jenkins (CI/CD Automation)
* AWS EKS (Kubernetes Cluster)
* Kubernetes (Deployment & Service)
* AWS LoadBalancer (External Access)

---

## 📁 Repository Structure

```
Trend/
│── dist/                # Production build files
│── k8s/                 # Kubernetes YAML files
│── terraform/           # Infrastructure setup
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

## 🐳 Docker Setup

### Build Image

```bash
docker build -t hemanth10bh1010/trend-app .
```

### Push to DockerHub

```bash
docker push hemanth10bh1010/trend-app:latest
```

---

## ☸️ Kubernetes Deployment

### Apply configurations

```bash
kubectl apply -f k8s/namespace.yaml
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

### Verify

```bash
kubectl get pods -n trend
kubectl get svc -n trend
```

---

## 🔄 Jenkins CI/CD Pipeline

### Pipeline Stages

1. **Checkout Code**
2. **Build Docker Image**
3. **Push to DockerHub**
4. **Update kubeconfig**
5. **Deploy to EKS**
6. **Verify Deployment**

---

## 🔗 GitHub Webhook

* Configured webhook to trigger Jenkins pipeline automatically on every push
* Endpoint:

```
http://<jenkins-ip>:8080/github-webhook/
```

---

## 🌍 Application Access

### LoadBalancer URL:

```
http://a1b5bdf47b39742fb96b005da5fb8a6e-fa6387083b4c932b.elb.ap-south-1.amazonaws.com:3000
```

---

## 📊 Monitoring (Optional)

Basic monitoring can be done using:

* kubectl logs
* kubectl describe
* AWS CloudWatch

---

## 🎯 Key Achievements

✔ Automated CI/CD pipeline using Jenkins
✔ Dockerized application
✔ Deployed on AWS EKS
✔ Exposed using LoadBalancer
✔ GitHub webhook integration

---

## 📸 Screenshots (Add These)

* Jenkins Pipeline Success
* Pods Running
* Service LoadBalancer
* Application UI in Browser

---

## 🏁 Conclusion

Successfully implemented an end-to-end DevOps pipeline for deploying a production-ready application using modern cloud-native tools.

---

