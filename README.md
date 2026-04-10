# Multi-Cloud DevOps Architecture (AWS + GCP)

## Project Overview

This project demonstrates a **multi-cloud DevOps architecture** integrating AWS and GCP with secure networking, containerization, and CI/CD automation.

### Key Features

* Secure access via VPN
* AWS-based scalable Node.js application
* GCP-based ML API service
* Dockerized applications
* Automated CI/CD pipeline using GitHub Actions
* Centralized container registry (Docker Hub)

---

## Architecture Overview

### Flow

User → VPN Server → AWS VPC → ALB → EC2 (Node.js App) → GCP VM (ML API)

### CI/CD Flow

GitHub → GitHub Actions → Docker Hub → Deploy to AWS & GCP

---

## AWS Infrastructure

### Components:

* VPC (10.0.0.0/16)
* Public Subnet (VPN Server)
* Private Subnet (Application Servers)
* Application Load Balancer (ALB)
* EC2 Auto Scaling Group

### Features:

* Secure private networking
* Load balancing for high availability
* Scalable Node.js backend

---

## GCP Infrastructure

### Components:

* Compute Engine VM
* ML API (Docker container)

### Features:

* Lightweight inference API
* Secure access (restricted firewall rules)
* Integrated with AWS application

---

## Containerization

### Applications:

* AWS Node.js API
* GCP ML API

### Docker Features:

* Lightweight images
* Consistent runtime environments
* Easy deployment across clouds

---

## CI/CD Pipeline

Implemented using GitHub Actions.

### Workflow:

1. Code push to repository
2. Build Docker image
3. Run basic test
4. Login to Docker Hub
5. Tag Docker image
6. Push image to Docker Hub

---

## Docker Hub Repository

Docker images are stored in Docker Hub:

```
https://hub.docker.com/r/sivachikkala22/devops-app
```

---

## Security

* VPN-based access to private infrastructure
* Restricted Security Groups in AWS
* GCP firewall rules allow only trusted IPs
* No direct public access to private services

---

## Testing

### AWS App:

```
http://app-alb-1674674274.ap-south-1.elb.amazonaws.com/:3000
```

### GCP API:

```
http://<GCP-IP>:5000/predict
```

---

## Project Structure

```
.
├── app.js
├── Dockerfile
├── package.json
├── .github/
│   └── workflows/
│       └── main.yml
└── README.md
```

---

## Evaluation Highlights

* Multi-cloud integration (AWS + GCP)
* Secure networking (VPN + private subnets)
* Containerized applications
* Automated CI/CD pipeline
* Scalable and production-ready design

---

## Conclusion

This project showcases real-world DevOps including:

* Infrastructure design
* Automation
* Cloud integration
* Security best practices

---

## Author

DevOps Engineer siva chikkala
