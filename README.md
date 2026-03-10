🚀 Trend Application – End-to-End DevOps CI/CD Pipeline

This project demonstrates a complete DevOps CI/CD pipeline for deploying the Trend Application on AWS EKS using Terraform, Jenkins, Docker, and Kubernetes.

The pipeline automates:

Infrastructure provisioning

Containerization

Image storage

Deployment

Monitoring

🔗 Git Repository
Project Repository
https://github.com/harshini-m-devops/trendapp-project.git
Application Source Repository
https://github.com/Vennilavanguvi/Trend.git
🏗 Infrastructure Provisioning (Terraform)

Infrastructure was provisioned using Terraform Infrastructure as Code (IaC).

Resources created using main.tf:

VPC

Public Subnets

Internet Gateway

Route Tables

IAM Roles

EC2 Instance for Jenkins Server

Terraform Commands
terraform init
terraform plan
terraform apply

Terraform automatically creates the infrastructure required to run the CI/CD pipeline.

🧰 Technologies Used

Terraform – Infrastructure provisioning

AWS EC2 – Jenkins server

Docker – Containerization

DockerHub – Container image registry

Kubernetes – Container orchestration

AWS EKS – Managed Kubernetes service

Jenkins – CI/CD automation

GitHub – Version control

kubectl – Kubernetes CLI

Prometheus – Monitoring

Grafana – Visualization dashboards

🏛 Project Architecture
Developer Push Code → GitHub
        ↓
GitHub Webhook
        ↓
Jenkins Pipeline
        ↓
Docker Build
        ↓
Push Docker Image to DockerHub
        ↓
Deploy Application to AWS EKS
        ↓
Kubernetes Deployment
        ↓
Kubernetes Service (LoadBalancer)
        ↓
Application accessible via Public URL
        ↓
Monitoring via Prometheus & Grafana
⚙ Steps Implemented
1️⃣ Application Setup

Clone the application repository:

git clone https://github.com/Vennilavanguvi/Trend.git

The application runs on:

Port 3000
2️⃣ Dockerization

Created a Dockerfile to containerize the application.

3️⃣ Container Registry (DockerHub)

Created DockerHub repository:

harshinimdocker/trend-app

Push Docker image:

docker tag trend-app harshinimdocker/trend-app:latest
docker push harshinimdocker/trend-app:latest
4️⃣ Kubernetes Deployment (AWS EKS)

Create the EKS cluster:

eksctl create cluster \
--name trend-cluster \
--region us-east-1 \
--node-type t3.micro \
--nodes 2

Verify cluster:

kubectl get nodes
5️⃣ Kubernetes Configuration

Created the following files:

deployment.yml

service.yml

These files are used to deploy the containerized application to the EKS cluster.

🔄 CI/CD Pipeline (Jenkins)

Jenkins automates the build and deployment process.

Pipeline flow:

GitHub Push
     ↓
GitHub Webhook
     ↓
Jenkins Pipeline (SCM)
     ↓
Jenkins automatically clones repository
     ↓
Build Docker Image
     ↓
Push Image to DockerHub
     ↓
Deploy Application to AWS EKS
🔔 GitHub Webhook Integration

GitHub webhook automatically triggers the Jenkins pipeline on every commit.

This enables continuous deployment of the application.

📊 Monitoring

Monitoring is implemented using Prometheus and Grafana.

Prometheus

Prometheus collects metrics such as:

Pod health

CPU usage

Memory usage

Kubernetes cluster metrics

Grafana

Grafana provides dashboards and visualization.

Features include:

Real-time cluster monitoring

Pod resource usage tracking

Alerting for system failures

🌐 Application Access

Application URL:

http://acfd01e48840b418caa2e28df5d40b68-859378692.us-east-1.elb.amazonaws.com
📦 LoadBalancer ARN
arn:aws:elasticloadbalancing:us-east-1:084396578047:loadbalancer/acfd01e48840b418caa2e28df5d40b68
