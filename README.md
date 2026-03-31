# Ec2-nginx-cicd-project
This project demonstrates a complete end-to-end DevOps workflow by deploying a web server on AWS EC2 and automating deployments using GitHub Actions.

## Project Overview
The goal of this project is to simulate a real-world DevOps pipeline where:
A web application is hosted on an EC2 instance
NGINX is used as the web server
Code is stored in GitHub
CI/CD is implemented using GitHub Actions
Updates are automatically deployed to the server via SSH

## Architecture
Developer → GitHub Repo → GitHub Actions → EC2 (NGINX) → Browser

## Technologies Used
AWS EC2 (Amazon Linux 2)
NGINX Web Server
Git & GitHub
GitHub Actions (CI/CD)
SSH Authentication
Linux (CLI)

## Step-by-Step Implementation
  ## 1. Launch EC2 Instance
AMI: Amazon Linux 2
Instance type: t2.micro
Security Group:
SSH (22)
HTTP (80)

  ## 2. Install and Configure NGINX
sudo yum update -y
sudo yum install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx

### 3. Deploy Web Page
```bash
echo "<h1>Welcome to My Web Server</h1>" | sudo tee /var/www/html/index.html
```

## 3. Deploy Web Page
echo"<h1>Welcome to My Web Server</h1>" | sudo tee /var/www/html/index.html.

## 4. Set Up GitHub Repository
Create repository
Push project files:
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main

## 5. Configure GitHub Secrets
Navigate to:
 ## Settings → Secrets and variables → Actions
Add the following:
EC2_HOST → EC2 Public IP
EC2_USER → ec2-user
EC2_SSH_KEY → Contents of .pem file

## 6. Create CI/CD Pipeline
Create:
.github/workflows/deploy.yml

Pipeline automatically:

Triggers on push to main
Connects to EC2 via SSH
Deploys updated HTML

## Access the Application
Open in browser:
http://<your-ec2-public-ip>
