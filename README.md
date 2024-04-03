# Learning Management System (LMS) Deployment on AWS

Welcome to the Learning Management System (LMS) project, where I've successfully deployed an LMS application on Amazon Web Services (AWS) infrastructure. This repository serves as a guide and reference for understanding the deployment process and managing the deployed application.

## Overview

In this project, I've utilized AWS services to deploy a scalable and reliable Learning Management System. The LMS facilitates seamless learning experiences for users, providing access to courses, resources, and interactive learning materials.

## Deployment Process
**1.Infrastructure Setup**
- I've utilized AWS services, including EC2 instances, to setup the primary infrastructure for hosting the LMS application. EC2 provides sc scalability and flexibility in resource allocation, ensuring optimal performance.

**2.Build and Deployment Automation**
- I've integrated NPM for managing dependencies and facilitating the build processes of the application. Additionally, Jenkins CI/CD pipeline automates the deployment process, ensuring smooth and efficient deployment cycles.

**3.Containerization with Docker**
- Docker containers are employed for deploying the LMS application, providing consistency in deployment environments and enabling scalability. Docker ensures that the application runs consistently across different environments, from development to production.

**4.Monitoring and Insights**
- To monitor the performance and health of the deployed application, we've configured Prometheus and Grafana. These tools provide real-time monitoring and insights into system performance, enabling proactive management and optimization.

## AWS EKS

I've Successfully deployed LMS application **Kubernetes** by creating a kubernetes cluster and utilizing replicas in deployment to auto-healing and ease of auto-scaling, configured application load balancer then exposed the application to the outside world through an external IP.

## Deployment Process

**1.Kubernetes Cluster Creation**
- I've created a Kubernetes cluster to serve as the orchestration platform for our LMS application. Kubernetes provides powerful features for managing containerized applications, ensuring scalability and reliability.

**2.Replicas in Deployment**
- Utilizing Kubernetes deployment resources, we specified the number of replicas for our LMS application. This enables auto-healing, ensuring that if a pod fails, Kubernetes automatically restarts it to maintain the desired number of replicas.

**3.Auto-Scaling**
- Kubernetes allows us to set up horizontal auto-scaling based on metrics such as CPU utilization or custom metrics. This ensures that the application can handle varying loads efficiently by automatically adjusting the number of replicas.

**4.Application Load Balancer**
- configured an application load balancer (ALB) to distribute incoming traffic among the replicas of the LMS application. The ALB ensures high availability and fault tolerance by evenly distributing traffic and rerouting it in case of failures.

**Exposing the Application**
- By assigning an external IP address to the ALB, we exposed the LMS application to the outside world. Users can access the application using this IP address, allowing seamless interaction with the learning platform.



