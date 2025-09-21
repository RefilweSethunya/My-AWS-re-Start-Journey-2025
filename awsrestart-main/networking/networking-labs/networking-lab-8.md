# Networking Lab: Configuring an Amazon VPC

## Objective
Create a VPC with a private and public subnet, an internet gateway and a NAT gateway. Configure route tables associated with subnets to local and internet-bound traffic by using an internet gateway and a NAT gateway. Launch a bastion server in a public subnet. Use a bastion server to log in to an instance in a private subnet.

## Steps Taken
1. Logged into AWS Management Console
2. Created a new VPC
   - Name tag: Lab VPC
   - IPv4 CIDR: 10.0.0.0/16
   - Tenancy: Default
   - Actions > Edit VPC settings > DNS settings section > Enable DNS hostnames
   - (EC2 instances launched into the VPC now automatically receive a public IPv4 Domain Name System (DNS) hostname)    
3. Created a public subnet
   - VPC ID: Lab VPC
   - Subnet name: Public Subnet
   - Availability Zone: (First on the list)
   - IPv4 CIDR block: 10.0.0.0/24
   - Actions > Edit subnet settings > Auto-assign IP settings > Enable auto-assign public IPv4 address.
4. Created a private subnet
   - VPC ID: Lab VPC
   - Subnet name: Private Subnet
   - Availability Zone: (First on the list)
   - IPv4 CIDR block: 10.0.2.0/23
5. Created an IGW
   - Name tag: Lab IGW
   - Attach to VPC
6. Configured route tables
   - Create a public route table for internet-bound traffic
   - Add a route to the route table to direct internet-bound traffic to the internet gateway
   - Associate the public subnet with the new route table
7. Launched bastion server in the public subnet
   - Name: Bastion Server
   - Quick Start: Choose Amazon Linux
   - Amazon Machine Image (AMI): Amazon Linux 2023 AMI
   - Instance type section: t3.micro
   - Key pair: Proceed without a key pair
   - VPC: Lab VPC
   - Subnet: Public Subnet
   - Auto-assign public IP: Enable
   - Firewall (security groups): Create security group
     - Security group name: Bastion Security Group
     - Description: Enter Allow SSH
     - Inbound security groups rules:
       - Type: SSH
       - Source: Anywhere
8. Created a NAT Gateway
   - Name: Lab NAT gateway
   - Subnet: Public Subnet
   - Allocate Elastic IP
9. Configured the private subnet to send internet-bound traffic to the NAT gateway
    - Route tables > Private Route Table > Routes > Edit routes
    - Add route
      - Destination: 0.0.0.0/0
      - Target: NAT Gateway (dropdown list)
Testing the private subnet
10.  Launched an instance in the private subnet
     - Name: Private Instance
     - Quick Start: Choose Amazon Linux
     - Amazon Machine Image (AMI): Amazon Linux 2023 AMI
     - Instance type section: t3.micro
     - Key pair (login): Proceed without a key pair (Not recommended)
     - VPC: Lab VPC
     - Subnet: Private Subnet (not the public subnet)
     - Firewall (security groups): Create security group
     - Security group name: Private Instance SG
     - Description: Allow SSH from Bastion
     - Inbound security groups rules:
       - Type: SSH
       - Source type: Custom | 10.0.0.0/16
       - User data
 ``` bash
         #!/bin/bash
# Turn on password authentication for lab challenge
echo 'lab-password' | passwd ec2-user --stdin
sed -i 's|[#]*PasswordAuthentication no|PasswordAuthentication yes|g' /etc/ssh/sshd_config
systemctl restart sshd.service
```
11. Logged into the bastion server
12. Logged into the private instance
    


## Challenges
- ...

## Screenshot
VPC Configuration
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/2528038c-2d18-4c33-a988-8e37b800300a" />

<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/8e1beea0-a672-4891-a5c6-cf6d88b2c256" />

Public Subnet Configuration
<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/1ccaa8c5-1271-455f-a57d-012a416da492" />

<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/ac8b8840-76ee-4492-8966-ba15cbc20b4a" />
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/7936845b-4462-4f87-8ae3-d35c585063da" />

Private Subnet Configuration
<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/80b67c2f-c462-4f70-a94f-abae20ef9b8d" />

<img width="1366" height="636" alt="image" src="https://github.com/user-attachments/assets/d165799d-df11-4317-9ad1-27a8060c4441" />

IGW Configuration
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/deb4d048-ab4b-4503-901b-d420db36583f" />
Attach IGW-VPC Configuration
<img width="1366" height="588" alt="image" src="https://github.com/user-attachments/assets/c2f7cf6d-b666-4f38-b9b7-491315af4439" />

Private Route Table Configuration
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/1e60e553-613f-4d30-9786-69aa6e4207dd" />
<img width="1366" height="630" alt="image" src="https://github.com/user-attachments/assets/756f95ee-1178-4687-baeb-9ded4194945b" />

Public Route Table Configuration
<img width="1366" height="636" alt="image" src="https://github.com/user-attachments/assets/267726ed-82ff-405c-a860-1a3c61fb065e" />

<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/84b705ba-c208-40d9-9cfd-293fb046a4c5" />

Bastion Server Configuration
<img width="1366" height="638" alt="image" src="https://github.com/user-attachments/assets/f41fe9e0-b6da-4c79-b58f-79f76e1da130" />
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/6c78b241-bf9e-4344-936a-8174c38771b2" />

NAT Gateway Configuration
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/0ab8e076-2803-4493-955e-7d51b266f512" />
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/30a22087-397c-493e-86cd-9cff9d768af8" />
Resources in the private subnet that wish to communicate with the internet now have their network traffic directed to the NAT gateway, which forwards the request to the internet. Responses flow through the NAT gateway back to the private subnet.

Bastion Server Configuration
<img width="1366" height="431" alt="image" src="https://github.com/user-attachments/assets/0e62c179-ecd8-40d7-9457-49eb8bbd4400" />

Bastion Server Login
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/0a263f3f-ef45-4e85-a8bd-a529e31534a1" />

Private Server Login
<img width="1366" height="643" alt="image" src="https://github.com/user-attachments/assets/3d84a269-6466-4b66-88f5-b29553b55394" />



## Takeaways
A bastion server (also known as a jump box) is an EC2 instance in a public subnet that is securely configured to provide access to resources in a private subnet.
