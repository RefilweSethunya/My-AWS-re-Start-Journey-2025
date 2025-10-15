## Project 4
# Medical Care System

## Project Overview
The **MediCare Hub** project focuses on building a **highly available and fault-tolerant healthcare management system** hosted on AWS.  
It simulates a hospital environment where patients, doctors, and administrators interact securely through a centralized platform.  
The architecture prioritizes **reliability, data resilience, and performance**, ensuring the system remains operational even during Availability Zone failures.

---

## Business & Technical Requirements
- **High Availability:** Deploy across multiple Availability Zones to ensure continuous operation.  
- **Resilience:** Database and storage layers must withstand zone-level failures.  
- **Scalability:** Compute resources scale automatically based on patient record traffic and appointment requests.  
- **Performance:** Load balancing and DNS routing to maintain low latency for medical operations.  
- **Security:** Identity management, encryption, and secure network segmentation.  
- **Monitoring:** Real-time system health visibility and proactive failure detection.  

---

## Architecture Diagram

*Click to view the zoomable SVG version.*  
[<img src="medicalcaresystem.drawio.png" alt="AWS Medical Care System Architecture" width="800"/>](medicalcaresystem.drawio.svg)

---

## Key AWS Services Used
- **Amazon EC2 Launch Template** – Defines baseline configurations for scalable EC2 deployments  
- **Auto Scaling Groups (ASG)** – Ensures compute elasticity across multiple Availability Zones  
- **Elastic Load Balancer (ALB)** – Distributes inbound traffic evenly and conducts health checks  
- **Amazon RDS (Multi-AZ)** – Maintains database availability and durability across zones  
- **Amazon Route 53** – Manages DNS and enables failover routing policies  
- **Amazon EFS** – Provides shared, persistent storage accessible from multiple instances  
- **Amazon Cognito** – Handles user authentication and authorization securely  
- **Amazon CloudWatch** – Monitors instance performance, logs, and alerts for proactive issue resolution  
- **AWS Identity and Access Management (IAM)** – Enforces least-privilege access and service-level permissions  

---

## Architecture Highlights
- EC2 instances launched from a **predefined template** to maintain consistency and security standards  
- **Auto Scaling Groups** ensure the application dynamically adjusts to changing workloads  
- **Application Load Balancer (ALB)** maintains high availability and optimizes performance across zones  
- **Multi-AZ RDS** ensures database redundancy and seamless failover in case of outage  
- **Route 53 with health checks** provides DNS-level failover and reliable traffic routing  
- **Amazon EFS** supports shared file access between application servers  
- **Cognito integration** secures patient and staff logins  
- **CloudWatch dashboards and alarms** provide operational visibility and health monitoring  

---

## Learning Outcomes
Through this project I practiced:  
- Designing and deploying a **multi-tier, high-availability AWS architecture** for critical workloads  
- Implementing **Multi-AZ strategies** for fault tolerance and automatic failover  
- Using **Elastic Load Balancing** and **Auto Scaling** to maintain performance under varying loads  
- Integrating **Route 53 failover routing** and **RDS redundancy** for uninterrupted healthcare service  
- Applying **IAM and Cognito** to enhance user authentication and access control  
- Monitoring and optimizing infrastructure health using **Amazon CloudWatch**  

---

<p align="center"><em>High-availability AWS architecture for healthcare workloads</em></p>

