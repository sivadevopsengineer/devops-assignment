Multi-Cloud DevOps Architecture (AWS + GCP)
 Project Overview

This project demonstrates a production-style multi-cloud DevOps architecture integrating:

AWS (VPC, EC2, ALB, VPN/Bastion)
GCP (VM for ML API)
Docker (containerization)
GitHub Actions (CI/CD automation)
Docker Hub (container registry)

The system is designed to simulate a real-world secure deployment pipeline with private networking and automated delivery.

Architecture
 Flow
User
  ↓
VPN Server (AWS EC2 - Public)
  ↓
Private VPC (AWS)
  ↓
Application Load Balancer
  ↓
EC2 (Private Subnet - Docker App)
  ↓
Calls →
GCP VM (ML API - Docker)
 CI/CD Pipeline
GitHub → GitHub Actions → Docker Hub → AWS Deployment via VPN (SSH)
 Key Features
✅ Secure access using VPN/Bastion host
✅ Private EC2 instances (no public IP)
✅ Dockerized Node.js application
✅ Cross-cloud communication (AWS → GCP)
✅ Fully automated CI/CD pipeline
✅ Zero manual deployment
 Tech Stack
Layer	Technology
Cloud	AWS + GCP
Compute	EC2
Networking	VPC, ALB, VPN
Containers	Docker
CI/CD	GitHub Actions
Registry	Docker Hub
Backend	Node.js
  CI/CD Pipeline
  Pipeline Steps
Checkout code
Build Docker image
Run basic test
Login to Docker Hub
Push Docker image
Deploy to AWS EC2 via VPN (Bastion SSH)
  GitHub Actions File

Located at:

.github/workflows/main.yml
     Required Secrets
Secret Name	Description
DOCKER_USERNAME	Docker Hub username
DOCKER_PASSWORD	Docker Hub password/token
EC2_HOST	Public IP of VPN/Bastion
EC2_USERNAME	EC2 username (ubuntu)
EC2_SSH_KEY	Private key for SSH
    Deployment Process
Git push triggers pipeline
Docker image is built & pushed to Docker Hub
GitHub Actions connects to VPN server
VPN server SSH into private EC2
Application container is deployed automatically
   Application
Node.js app running inside Docker
Exposed on port 3000
Accessible via ALB or VPN
   GCP Integration
Separate VM running ML API (Dockerized)
AWS app communicates via private/internal networking
  Setup Instructions
1. Clone Repository
git clone https://github.com/<your-username>/devops-assignment.git
cd devops-assignment
2. Build Docker Image
docker build -t devops-app .
3. Run Locally
docker run -d -p 3000:3000 devops-app
   SSH Access Flow
# Step 1: Connect to VPN/Bastion
ssh -i key.pem ubuntu@<VPN_PUBLIC_IP>

# Step 2: Connect to Private EC2
ssh -i key.pem ubuntu@<PRIVATE_IP>
      Deliverables
✅ GitHub Repository
✅ Architecture Diagram
✅ CI/CD Pipeline
✅ Deployment Setup
✅ Multi-cloud integration
  Notes
Private EC2 is not publicly accessible
Deployment is done securely via VPN
Docker containers are rebuilt on every push
  Author

Siva DevOps Engineer

 Conclusion

This project showcases:

Real-world DevOps practices
Secure infrastructure design
Multi-cloud integration
Automated CI/CD pipeline
