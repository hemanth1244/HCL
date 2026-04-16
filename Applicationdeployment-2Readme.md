# 🚀 DevOps CI/CD Pipeline Project

## 📌 Overview
This project demonstrates a complete DevOps workflow:

- GitHub (Version Control)
- Jenkins (CI/CD Automation)
- Docker (Containerization)
- Docker Hub (Image Registry)
- Multibranch Pipeline (dev & master)
- Uptime Kuma (Monitoring & Alerts)

---

## 🏗️ Architecture

| Branch | Purpose | Docker Repo | Port |
|--------|--------|------------|------|
| dev | Development | myapp-dev | 3000 |
| master | Production | prod (private) | 3001 |

---

## ⚙️ Technologies Used

- Jenkins
- GitHub
- Docker
- Docker Hub
- Ubuntu EC2
- Uptime Kuma

---

## 🧑‍💻 Application Setup

```bash
git clone https://github.com/hemanth1244/devops-build-submission.git
cd devops-build-submission
🐳 Docker
Build Image
docker build -t myapp .
Run Container
docker run -d -p 3000:80 myapp
⚙️ Jenkins Setup
sudo apt update
sudo apt install openjdk-17-jdk -y
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins

Access:

http://<EC2-IP>:8080
🔐 Initial Setup
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

Install suggested plugins.

🔧 Plugins Required
Git
GitHub
Pipeline
Docker Pipeline
Multibranch Pipeline
Credentials Binding
🔗 GitHub Webhook

Payload URL:

http://<EC2-IP>:8080/github-webhook/

Event:

Push
🌿 Multibranch Pipeline
Create Multibranch Pipeline
Connect GitHub repo
Detect branches: dev, master
🔄 CI/CD Flow
Dev Branch
git checkout dev
git push origin dev

✔ Build image
✔ Push to Docker Hub (dev repo)
✔ Deploy on port 3000

Master Branch
git checkout master
git push origin master

✔ Build image
✔ Push to private Docker Hub repo
✔ Login to Docker Hub
✔ Deploy on port 3001

🚀 Deployment URLs
Dev → http://<EC2-IP>:3000
Prod → http://<EC2-IP>:3001
🔑 Docker Credentials
Stored in Jenkins as:
dockerhub-creds
📊 Monitoring (Uptime Kuma)
Run Monitoring Tool
docker run -d \
  --restart=always \
  -p 3002:3001 \
  -v uptime-kuma:/app/data \
  --name uptime-kuma \
  louislam/uptime-kuma:1
Access Dashboard
http://<EC2-IP>:3002
📈 Monitors
Dev → http://<EC2-IP>:3000
Prod → http://<EC2-IP>:3001
🔔 Alerts
Email notifications configured
Alerts triggered only when app goes down
🧪 Testing Monitoring
docker stop myapp-dev-container
docker start myapp-dev-container

✔ Down → Alert
✔ Up → Recovery

📁 Project Structure
.
├── Dockerfile
├── Jenkinsfile
├── build.sh
├── deploy.sh
├── docker-compose.yml
├── README.md
🎯 Key Achievements
CI/CD using Jenkins
Multibranch pipeline (dev & master)
Docker build & push
Private Docker Hub integration
Automated deployment
Monitoring with alerts
🧠 Conclusion

This project demonstrates an end-to-end DevOps pipeline from code commit to deployment and monitoring with real-time alerts.
