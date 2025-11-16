<img width="1200" height="250" alt="image" src="https://github.com/user-attachments/assets/41433a61-8f32-41a2-b7b1-65ddc676d384" />

# My AWS re/Start Journey 2025

Welcome!
This repo contains my personal notes, completed labs and projects demonstrating applied AWS skills from the AWS re/Start program.

It serves as:  
- A **knowledge base** I can refer back to  
- A **portfolio** showcasing my [labs](/awsrestart-main/labs/labs-index.md), [projects](/awsrestart-main/projects/projects.md) and progress  
- Evidence of my commitment to continuous learning in cloud and IT

---

## Progress Tracker

- [x] Week 1 – Introduction to AWS  
- [x] Week 2 – Cloud Basics & AWS Compute Services
- [x] Week 3 – Linux & AWS Storage Services   
- [x] Week 4 – AWS Database, Storage and Analytics services
- [x] Week 5 – AWS Networking and Content Delivery services  
- [x] Week 6 – AWS Security services Part 1
- [x] Week 7 - AWS Security services Part 2
- [x] Week 8 - Management Tools
- [x] Week 9 - AWS Application & Migration Services
- [x] Week 10 - AWS Developer Tools and Machine Learning
- [x] Weeks 11,12 - Final Project & Exam Prep
- [x] AWS Certified Cloud Practitioner – Exam PASSED 🎉  
<p align="center">
  <a href="https://www.credly.com/badges/64964e26-5774-4816-95ca-9fde7fe06ea5/public_url">
    <img src="https://images.credly.com/size/340x340/images/00634f82-b07f-4bbd-a6bb-53de397fc3a6/image.png" 
         alt="AWS Certified Cloud Practitioner Badge" width="240">
  </a>
</p>

<p align="center">
  <b>AWS Certified Cloud Practitioner (CLF-C02)</b><br>
  <i>Issued October 2025 • Verified by Credly</i><br>
  <a href="https://www.credly.com/badges/64964e26-5774-4816-95ca-9fde7fe06ea5/public_url">View Credential →</a>
</p>


---

## Projects Showcase

### ECommerce Platform Architecture
- **Goal:** Design a scalable, secure, highly available AWS architecture for a global e-commerce web application
- **Highlights:**
  - Multi-AZ architecture ensuring fault tolerance and business continuity.
  - Elastic Load Balancer (ALB) distributes web traffic across multiple EC2 instances for performance and high availability.
  - Auto Scaling Group dynamically adjusts compute capacity based on demand.
  - Amazon RDS (Multi-AZ) for reliable and consistent transaction data management.
  - Amazon CloudFront (CDN) accelerates global content delivery and improves user experience.
  - Amazon S3 hosts static content such as product images, scripts, and stylesheets.
  - AWS Cognito provides user authentication and access control for customers and administrators.
  - AWS WAF and Security Groups protect against common web exploits and malicious traffic.
  - Amazon CloudWatch and AWS CloudTrail enable monitoring, logging, and auditing across infrastructure components.
  - IAM roles and policies enforce least-privilege access and operational security best practices.
[<img src="/awsrestart-main/projects/project-1/ecommerceapplication.drawio.png" alt="3D E-Commerce Architecture" width="600"/>](/awsrestart-main/projects/project-1/ecommerceapplication.drawio.svg)
- [View Project](/awsrestart-main/projects/project-1/README.md)

### Interactive AWS Lex Chatbot
- **Goal:** Build an intelligent chatbot using Amazon Lex to simulate real-world customer support scenarios.  
- **Highlights:**
  - Configured intents, slots, and utterances for natural language understanding.  
  - Integrated AWS Lambda for backend logic (order tracking and FAQs).  
  - Connected to Amazon Polly for text-to-speech output.  
  - Deployed on AWS Amplify for user testing
- [View Project](/awsrestart-main/projects/project-2/README.md)

### Event Announcement System
- **Goal:** Develop an event notification system to send automated alerts and reminders to registered users via email and SMS.
- **Highlights:**
  - Static frontend hosted in Amazon S3 with API endpoints exposed via Amazon API Gateway.  
  - Two AWS Lambda functions — one to manage user subscriptions, another to handle event registration and JSON updates.  
  - Events stored in an S3 bucket as JSON files for simplicity and durability.  
  - Email notifications managed via Amazon Simple Notification Service (SNS).  
  - Fully serverless, cost-efficient, and scalable architecture for event-driven communication.   
- [View Project](/awsrestart-main/projects/project-3/README.md)

### Medical Care System
- **Goal:** Implement a cloud-based healthcare management solution for secure patient data handling and appointment tracking.
- **Highlights:**
  - Configured an EC2 launch template with Auto Scaling Groups across multiple Availability Zones for fault tolerance.  
  - Set up an Application Load Balancer (ALB) to distribute incoming traffic and monitor instance health.  
  - Integrated Amazon Cognito for user authentication and role-based access control (doctors, patients, and admins).  
  - Deployed a Multi-AZ Amazon RDS database for continuous availability and failover resilience.  
  - Configured Route 53 with health checks and failover routing for DNS-level reliability.  
  - Added Amazon EFS for scalable, shared file storage across EC2 instances.  
  - Designed to maintain uptime, data integrity, and security compliance in a healthcare environment.  
- [View Project](/awsrestart-main/projects/project-4/README.md)
  
---

## Topics Covered

- [Compute](/awsrestart-main/compute/topic-notes.md)
- [Storage](/awsrestart-main/storage/topic-notes.md)
- [Databases](/awsrestart-main/databases/topic-notes.md)
- [Security](/awsrestart-main/security/topic-notes.md)
- [Networking](/awsrestart-main/networking/topic-notes.md)
- [Management, Monitoring and Automation](/awsrestart-main/management-monitoring-and-automation/topic-notes.md)

---

## <img width="45" height="45" alt="image" src="https://github.com/user-attachments/assets/3016bf4e-af30-45e0-8cda-1f205511fef8" /> AWS Skills Builder Courses 


A growing collection of courses I’ve completed on AWS Skills Builder as part of my AWS learning journey.  
  
Status | Course Name | Key Takeaway
-------|-------------|--------------
✅     | AWS Compute Services Overview | I compared EC2, Lambda, and containers for cost and scalability
✅     | Introduction to AWS Identity and Access Management (IAM) | I learned user, role, and policy management with least privilege
✅     | Introduction to Containers | I grasped Docker basics and AWS container services (ECS/EKS)
✅     | AWS Cloud Quest: Cloud Practitioner | I practiced core AWS services through gamified labs
✅     | AWS SimuLearn: Networking Concepts | I strengthened my understanding of VPCs, subnets, routing, and connectivity in AWS
✅     | AWS SimuLearn: Core Security Concepts| I explored key AWS security principles, shared responsibility, and best practices for protecting workloads

## Certificates

All completed course certificates (PDFs) can be accessed here: 
- AWS Compute Services Overview [View Certificate](/awsrestart-main/certifications-and-courses/certificates/aws-compute-services-overview.pdf)
- Introduction to AWS Identity and Access Management (IAM) [View Certificate](/awsrestart-main/certifications-and-courses/certificates/introduction-to-aws-iam.pdf)
- Introduction to Containers [View Certificate](/awsrestart-main/certifications-and-courses/certificates/introduction-to-containers.pdf)
- AWS Cloud Quest: Cloud Practitioner [View Certificate](/awsrestart-main/certifications-and-courses/certificates/aws-cloud-quest-cloud-practitioner.pdf)
- AWS SimuLearn: Networking Concepts [View Certificate](/awsrestart-main/certifications-and-courses/certificates/aws-simulearn-networking-concepts.pdf)
- AWS SimuLearn: Core Security Concepts [View Certificate](/awsrestart-main/certifications-and-courses/certificates/aws-simulearn-core-security-concepts.pdf)

---

## Reflections

As I near the end of my AWS re/Start journey, I’m struck by how much I’ve grown. I started with lots of curiosity and week by week, the program built up my Linux and networking basic skills to databases, security and automation. The hands-on labs made cloud concepts tangible and boosted my confidence.

Another big milestone was using GitHub for the first time. After working with version control, I see how powerful it is for tracking progress and working in a structured, professional way.

Where I focused on individual services before, now I see the bigger picture of how each AWS service connects to build scalable, reliable systems. Beyond technical skills, I’ve gained perseverance, problem-solving and the confidence to think like a cloud practitioner.

---

## Next Steps

- Continue documenting daily labs and AWS learning  
- Build and showcase more [cloud projects](/awsrestart-main/projects/projects.md) integrating multiple AWS services  
- Deepen cloud expertise by preparing for AWS Certified Solutions Architect – Associate (SAA-C03)
- Prepare for additional AWS certifications 

---

## Learning Resources

- [AWS Training & Certification](https://aws.amazon.com/training/)  
- [AWS Documentation](https://docs.aws.amazon.com/)  
- [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)
- [AWS Skills Builder Training](https://explore.skillbuilder.aws/)
- [More Resources](/awsrestart-main/resources/helpful-links.md)

## Found this repo useful?

Give us a ⭐ by clicking the "Star" button at the top-right of this page to show your support and help others discover these resources.
