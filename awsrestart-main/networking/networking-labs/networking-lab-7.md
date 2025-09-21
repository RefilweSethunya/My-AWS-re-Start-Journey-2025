# Networking Lab: Build your VPC and Launch a Web Server

## Objective
Create network resources and routing components to make the VPC network functional.
<img width="1106" height="510" alt="image" src="https://github.com/user-attachments/assets/e36fd9c1-216c-4a17-b85c-932d2745673a" />
Deliver customer's exact request: a fully functional VPC with its resources (network and security) AND A WEB SERVER.
<img width="1114" height="511" alt="image" src="https://github.com/user-attachments/assets/c4728464-9c9c-475f-bbbc-e00c10aa1882" />

## Steps Taken
1. Logged into AWS Management Console
2. Created VPC.
   - Name : Test VPC
   - IPv4 CIDR: 10.0.0.0/16
   - IPv6 CIDR block: None
   - Tenancy: Default
   - Number of Availability Zones (AZs): 1
   - Number of public subnets: 1 | Public subnet CIDR block in us-west-2a: 10.0.0.0/24 | name tag: Public Subnet 1 | Public Route Table
   - Number of private subnets: 1 | Private subnet CIDR block in us-west-2a: 10.0.1.0/24 | name tag: Private Subnet 1 | Private Route Table
   - NAT gateways: In 1 AZ
   - VPC endpoints: None
   - VPC: Lab VPC
4. Created additional public subnet in VPC
   - Subnet name: Public Subnet 2
   - Availability Zone: No preference
   - IPv4 CIDR block: 10.0.2.0/24
5. Created additional private subnet in VPC
   - Subnet name: Private Subnet 2
   - Availability Zone: No preference
   - IPv4 CIDR block: 10.0.3.0/24
7. Associated the subnets and added routes
8. Created a VPC security group
   - Security group name: Web Security Group
   - Description: Enable HTTP access
   - VPC: Lab VPC.
   - Add Inbound rule
     - Type: HTTP
     - Source: Anywhere IPv4
     - Description: Permit web requests
    
9. Launched a web server instance
    - Name:  Web Server 1
    - Quick Start: Amazon Linux
    - Amazon Machine Image (AMI): Amazon Linux 2 AMI (HVM)
    - Instance type: t3.micro
    - Key pair: vockey
    - VPC: Lab VPC
    - Subnet: Public Subnet 2
    - Auto-assign public IP: Enable
    - Firewall (security groups): Web Security Group
    - User Data:
  
```bash
#!/bin/bash
#Install Apache Web Server and PHP
yum install -y httpd mysql php
#Download Lab files
wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-100-RESTRT-1/267-lab-NF-build-vpc-web-server/s3/lab-app.zip
unzip lab-app.zip -d /var/www/html/
#Turn on web server
chkconfig httpd on
service httpd start
```

## Challenges
- ...

## Screenshot
VPC Configuration
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/8254f135-514f-45be-a3ef-48f7a12d6f42" />



## Takeaways
I am able to create a VPC and its resources and make it successfully connect to a web server. According to my design specification, or a customer's design specifications.
I can appreciate the scalability of AWS, that even after using a Create VPC wizard we can later create additional resources not specified in the beginning. Similar to thegroeing demands of a customer using AWS. 
