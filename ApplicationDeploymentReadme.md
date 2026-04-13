deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: brain-tasks-app
  labels:
    app: brain-tasks-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: brain-tasks-app
  template:
    metadata:
      labels:
        app: brain-tasks-app
    spec:
      containers:
        - name: brain-tasks-app
          image: 949934294801.dkr.ecr.ap-south-2.amazonaws.com/brain-app:latest
          ports:
            - containerPort: 3000

service.yaml
apiVersion: v1
kind: Service
metadata:
  name: brain-tasks-service
spec:
  type: LoadBalancer
  selector:
    app: brain-tasks-app
  ports:
    - protocol: TCP
      port: 3000
      targetPort: 3000

Dockerfile
FROM nginx:alpine

COPY dist/ /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]

nginx.conf
server {
    listen 3000;
    server_name _;

    root /usr/share/nginx/html;
    index index.html;

    location / {
        try_files $uri /index.html;
    }
}

buildspec.yml:
version: 0.2

env:
  variables:
    AWS_DEFAULT_REGION: ap-south-2
    IMAGE_REPO_NAME: brain-app
    IMAGE_TAG: latest
    EKS_CLUSTER_NAME: brain-tasks-cluster

phases:
  install:
    runtime-versions:
      docker: 20
    commands:
      - echo Installing required tools
      - aws --version
      - docker --version

  pre_build:
    commands:
      - echo Logging in to Amazon ECR
      - ACCOUNT_ID=$(aws sts get-caller-identity --query Account --output text)
      - REPOSITORY_URI=$ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com/$IMAGE_REPO_NAME
      - echo $REPOSITORY_URI
      - aws ecr get-login-password --region $AWS_DEFAULT_REGION | docker login --username AWS --password-stdin $REPOSITORY_URI

  build:
    commands:
      - echo Building Docker image
      - docker build -t $IMAGE_REPO_NAME:$IMAGE_TAG .
      - docker tag $IMAGE_REPO_NAME:$IMAGE_TAG $REPOSITORY_URI:$IMAGE_TAG

  post_build:
    commands:
      - echo Pushing Docker image
      - docker push $REPOSITORY_URI:$IMAGE_TAG
      - echo Updating kubeconfig for EKS
      - aws eks update-kubeconfig --region $AWS_DEFAULT_REGION --name $EKS_CLUSTER_NAME
      - echo Deploying to EKS
      - kubectl apply -f deployment.yaml
      - kubectl apply -f service.yaml
      - kubectl rollout status deployment/brain-tasks-app
      - kubectl get pods
      - kubectl get svc
      - printf '[{"name":"brain-tasks-app","imageUri":"%s"}]' $REPOSITORY_URI:$IMAGE_TAG > imagedefinitions.json

artifacts:
  files:
    - deployment.yaml
    - service.yaml
    - imagedefinitions.json
    - appspec.yaml# Brain Tasks App – Production Deployment on AWS

README.md:
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
Open in browser:
http://Publicipofinstance:3000

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
