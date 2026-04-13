# Brain Tasks App – Production Deployment on AWS

## Project Overview
This project demonstrates production-style deployment of the Brain Tasks React application using Docker, Amazon ECR, Amazon EKS, AWS CodeBuild, AWS CodePipeline, and CloudWatch Logs.

## Repository URL
- Application Repo: https://github.com/hemanth1244/brain-tasks-app
- Documentation Repo / Submission File: https://github.com/hemanth1244/HCL/blob/hemanth1244-patch-1/Application%20Deployment.md

## Architecture
1. Source code stored in GitHub
2. CodePipeline pulls latest code from GitHub
3. CodeBuild builds Docker image
4. Docker image pushed to Amazon ECR
5. Kubernetes manifests applied to Amazon EKS
6. Service of type LoadBalancer exposes application
7. CloudWatch Logs used for monitoring build and deployment logs

## Application Deployment Requirement
- Application deployed in container
- Application exposed on port 3000
- Kubernetes service type: LoadBalancer

## Files Included
- Dockerfile
- nginx.conf
- deployment.yaml
- service.yaml
- buildspec.yml
- imagedefinitions.json
- README.md

## Docker Steps
```bash
git clone https://github.com/Vennilavanguvi/Brain-Tasks-App.git
cd Brain-Tasks-App

docker build -t brain-app:latest .
docker run -d -p 3000:3000 brain-app:latest
Amazon ECR Steps
aws ecr create-repository --repository-name brain-app --region ap-south-2
aws ecr get-login-password --region ap-south-2 | docker login --username AWS --password-stdin <account-id>.dkr.ecr.ap-south-2.amazonaws.com
docker tag brain-app:latest <account-id>.dkr.ecr.ap-south-2.amazonaws.com/brain-app:latest
docker push <account-id>.dkr.ecr.ap-south-2.amazonaws.com/brain-app:latest

Amazon EKS Steps
eksctl create cluster --name brain-tasks-cluster --region ap-south-2 --nodes 2 --node-type t3.medium
aws eks update-kubeconfig --region ap-south-2 --name brain-tasks-cluster
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get svc

CodeBuild
CodeBuild is used to:
Build Docker image
Push image to ECR
Update kubeconfig
Deploy manifests to EKS using kubectl

CodePipeline
Pipeline stages:
Source – GitHub
Build – CodeBuild
Deploy – EKS deployment

Monitoring:
CloudWatch Logs used to monitor:
CodeBuild logs
Deployment execution logs
Application-related logs as configured

Validation Commands
kubectl get nodes
kubectl get pods
kubectl get svc
kubectl describe svc brain-tasks-service
