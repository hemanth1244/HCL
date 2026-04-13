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
    - appspec.yaml
