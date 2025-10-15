## Project 3
# Event Announcement System on AWS

## Project Overview
The goal of this project was to build a **serverless event notification system** that automatically sends email announcements to registered subscribers.  
The system enables administrators to create new events and notify all subscribers instantly — without managing any backend servers — ensuring a **fully managed, scalable, and cost-efficient architecture**.

---

## Business & Technical Requirements
- **Automation:** Trigger email notifications automatically when new events are created.  
- **Scalability:** Handle an increasing number of events and subscribers without manual intervention.  
- **Simplicity:** Use minimal moving parts by adopting a serverless approach.  
- **Reliability:** Ensure messages are delivered to all subscribed users.  
- **Cost Efficiency:** Pay only for what is used, ideal for low-to-medium event traffic.  

---

## Architecture Diagram

*Click to view the zoomable version.*  
[<img src="event-notification-architecture.png" alt="Event Notification System Architecture" width="800"/>](event-notification-architecture.png)  

---

## Key AWS Services Used
- **Amazon S3** – Hosts static frontend and stores event data in JSON format.  
- **Amazon API Gateway** – Exposes secure REST endpoints for user subscriptions and event creation.  
- **AWS Lambda** – Two functions: one for subscription management and another for event creation and publishing.  
- **Amazon Simple Notification Service (SNS)** – Handles the email distribution of event announcements to subscribers.  
- **Amazon CloudWatch** – Monitors Lambda executions and API activity.  
- **AWS IAM** – Manages permissions and roles for Lambda and API Gateway.  

---

## Architecture Highlights
- Fully **serverless design** reduces maintenance and simplifies scalability.  
- **Two Lambda functions** independently manage subscriptions and event triggers for modular efficiency.  
- **S3 stores event data** as JSON, ensuring durability and cost-effective persistence.  
- **API Gateway** provides secure, low-latency interaction between users and backend logic.  
- **SNS** automates the delivery of email notifications to all subscribers.  
- **IAM roles** enforce least-privilege access across components.  

---

## Learning Outcomes
Through this project I practiced:  
- Designing a **serverless, event-driven architecture** on AWS.  
- Implementing **publish-subscribe (pub/sub)** messaging patterns using SNS.  
- Building **API-based automation** for dynamic data and event handling.  
- Using **CloudWatch for operational visibility** and Lambda monitoring.  
- Applying **cost optimization** strategies through on-demand, usage-based compute.  


