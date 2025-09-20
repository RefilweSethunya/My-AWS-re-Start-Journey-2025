## Project 1
# 3D E-Commerce Platform Architecture on AWS

## Project Overview
The goal of this project was to design a cloud architecture for a **next-generation 3D e-commerce platform**.  
A platform that allows users to interact with 3D product models (e.g., furniture, gadgets, fashion) before purchasing.  
A key requirement was that it must support **millions of global users** with speed, reliability, and cost efficiency.  

---

## Business & Technical Requirements
- **High Availability:** 24/7 uptime with fault tolerance and failover across multiple Availability Zones.  
- **Scalability:** Auto-scaling to handle unpredictable global traffic spikes.  
- **Performance:** Low latency for 3D rendering, fast content delivery via CDN.  
- **Security:** IAM, governance controls, network firewalls, and AWS best practices.  
- **Cost Optimization:** Elastic scaling, managed services, monitoring, and avoiding over-provisioning.  

---

## Architecture Diagram

*Click to view the zoomable SVG version.*  
[<img src="ecommerceapplication.drawio.png" alt="AWS 3D E-Commerce Architecture" width="800"/>](ecommerceapplication.drawio.svg)  

---

## Key AWS Services Used
- **Amazon Route 53** – Global DNS with health checks and failover  
- **Amazon CloudFront** – Low-latency content delivery with edge caching  
- **Elastic Load Balancer (ELB)** – Distributes traffic across EC2 instances  
- **Amazon EC2 Auto Scaling** – Dynamic scalability for compute resources  
- **Amazon RDS (Multi-AZ)** – Highly available relational database backend  
- **Amazon S3** – Static asset and 3D model storage  
- **VPC + Security Groups** – Network isolation and traffic filtering  
- **IAM** – Secure access control with least privilege  
- **AWS Organizations** – Centralized account management for enterprise governance  
- **AWS Control Tower** – Multi-account setup and compliance guardrails  
- **AWS Firewall Manager** – Centralized firewall/security policy enforcement across accounts  

---

## Architecture Highlights
- Multi-AZ deployment ensures **fault tolerance** and **resilience**  
- CloudFront + Route 53 deliver **low-latency, global access**  
- Auto Scaling + ELB provide **elasticity during peak traffic**  
- RDS Multi-AZ and S3 ensure **data durability and availability**  
- Enterprise governance achieved via **AWS Organizations + Control Tower**  
- Security posture strengthened with **Firewall Manager, IAM roles, VPC isolation, and security groups**  

---

## Learning Outcomes
Through this project I practiced:  
- Designing an **end-to-end AWS solution** based on business requirements  
- Applying **Well-Architected Framework** principles (reliability, performance, security, cost optimization, governance)  
- Incorporating **governance and security services** (Organizations, Control Tower, Firewall Manager) for enterprise readiness  
- Creating **professional cloud architecture diagrams** with AWS icons   
 
