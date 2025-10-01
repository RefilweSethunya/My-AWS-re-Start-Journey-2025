# Compute Lab: Scale and Load Balance your Architecture
## Objective
The objective of this lab is to implement Elastic Load Balancing (ELB) and Amazon EC2 Auto Scaling to build a fault-tolerant and scalable infrastructure. I created an Amazon Machine Image (AMI) from an EC2 instance, configured a load balancer, and set up a launch template with an Auto Scaling group. I then configured the Auto Scaling group to scale new instances within private subnets and used Amazon CloudWatch alarms to monitor the performance and health of the infrastructure.


Starting Architecture
<img width="1202" height="688" alt="image" src="https://github.com/user-attachments/assets/9e6b2aaf-d8bd-439d-a1e9-97a482ab8bee" />
Final Architecture
<img width="2534" height="1550" alt="image" src="https://github.com/user-attachments/assets/1dda1d99-2408-4f1f-a3f5-50cc6b58d00d" />


## Steps Taken
1. Logged into the AWS Management Console
2. Created an AMI for auto scaling
   - AWS Management Console > EC2 > Instances > Select Web Server 1 > Actions > Image and templates > Create image > Configure the following:
     - Image name: Web Server AMI
     - Image description: Lab AMI for Web Server
     - Create image
3. Created a load balancer
   - Load balancers > ALB > Create > Configure the following:
     - Load Balancer Name : LabELB
     - VPC: Lab VPC
     - Mappings: AZ Public Subnet 1
     - Mappings: AZ Public Subnet 2
     - Security Groups: Web Security Group
   - Listeners and routing > Create Target Group > Configure the following:
     - Target type: Instances
     - Target group name: lab-target-group
   - Next
   - Create target group
   - Load balancers > Listeners and routing > Forward to lab-target-group
   - Create load balancer
   - View load balancer 
4. Created a launch template
   - EC2 > Instances > Launch Templates > Create Launch Template
   - Configure the following:
     - Launch template name: lab-app-launch-template
     - Template version description: A web server for the load test app
     - Auto Scaling guidance:  Provide guidance to help me set up a template that I can use with EC2 Auto Scaling
     - Instance type: t3.micro
     - Key pair (login): Don't include in launch template
     - Security Group: Web Security Group
     - Create launch template
     - View launch templates
5. Created an Auto-Scaling Group
   - Selected lab-app-launch-template > Actions > Create Auto Scaling Group
   - Configured the following:
     - Name: Lab Auto Scaling Group
     - VPC: Lab VPC
     - Availability Zones and subnets: Private Subnet 1 (10.0.1.0/24) and Private Subnet 2 (10.0.3.0/24)
     - Load balancing – optional section: Attach to an existing load balancer
     - Attach to an existing load balancer: Chose from load balancer target groups
     - Existing load balancer target groups: lab-target-group | HTTP
     - Health checks type: ELB
     - Group size – optional configured the following:
       - Desired capacity:2
       - Minimum capacity: 2
       - Maximum capacity: 4
     - Scaling Policies – optional configured the following:
       - Target tracking scaling policy
       - Metric Type: Avg CPU Utilization
       - Target Value: 50
     - Add tag. Key: Name. Value: Lab Instance
     - Next
     - Create Auto Scaling Froup
6. Verified Load balancing works
   - Load Balancing > Target Groups > Selected lab-target-group
7. Tested auto-scaling
   - CloudWatch > Alarms > All Alarms
   - Verified Number of instances running
8. Terminated the Web Server 1 instance
   - Selected Web Server 1 > Instance State > Terminate instance > Terminate

## Challenges
- 

## Screenshot
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/514d0599-3be7-4d27-bc38-a94714a4caa7" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/d68c759d-b2aa-4e34-ba3f-3ecffb587e48" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/32b6dc7c-59e0-4a6f-b89e-2dc4564f64e8" />
<img width="1366" height="667" alt="image" src="https://github.com/user-attachments/assets/582e7a74-c626-48a6-a0fd-2e3c92429afc" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/bbe912c4-c9a7-4935-92c1-fb44c4775f93" />
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/3a2f495f-c93d-4f38-9215-53c546b8496b" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/4b3127d2-a770-4b7c-b0b4-d4d6b231127e" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/7e10ca3b-d06d-4a01-b4fd-5006671a741d" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/6a7465fe-6950-455a-8f16-da6f1efe07aa" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/7584444c-b222-4847-84ae-4624b6e19b59" />
<img width="1366" height="668" alt="image" src="https://github.com/user-attachments/assets/9cb7cd55-b774-44cd-bf70-b8d106df9e48" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/57b5c223-cd5e-44f1-aa69-3840b32f049b" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/c31919e5-651e-43a7-9592-04fe4cfe51ac" />
<img width="1366" height="488" alt="image" src="https://github.com/user-attachments/assets/7e2f2ded-6077-44d6-8146-e96d63d39bd8" />
<img width="1366" height="665" alt="image" src="https://github.com/user-attachments/assets/50b33249-5850-4754-b412-700d5bbb4426" />
<img width="1366" height="433" alt="image" src="https://github.com/user-attachments/assets/c0993871-45f5-4a45-9566-20e9f0197a2d" />
<img width="1366" height="339" alt="image" src="https://github.com/user-attachments/assets/77a340b5-ae8a-41aa-9718-4a0f61b98e38" />
<img width="1366" height="374" alt="image" src="https://github.com/user-attachments/assets/0739133a-b524-4cc5-9fe2-1b949073606d" />


## Takeaways
This lab showed me how ELB and Auto Scaling work together to improve reliability, scalability, and cost efficiency. By creating an AMI, configuring a load balancer, and setting up an Auto Scaling group with CloudWatch alarms, I reinforced the importance of automation in maintaining performance while minimizing manual intervention.
