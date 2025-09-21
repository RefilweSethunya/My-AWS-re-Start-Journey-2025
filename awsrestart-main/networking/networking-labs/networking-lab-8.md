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
     
4. Created a public subnet
   - VPC ID: Lab VPC
   - Subnet name: Public Subnet
   - Availability Zone: (First on the list)
   - IPv4 CIDR block: 10.0.0.0/24
   - Actions > Edit subnet settings > Auto-assign IP settings > Enable auto-assign public IPv4 address.
5. Created a private subnet
   - VPC ID: Lab VPC
   - Subnet name: Private Subnet
   - Availability Zone: (First on the list)
   - IPv4 CIDR block: 10.0.2.0/23
6. Created an IGW
   - Name tag: Lab IGW
   - Attach to VPC
7. Configured route tables
   -
8. ds

## Challenges
- Forgot to open port 22 in the security group
- Solved by editing the inbound rules

## Screenshot
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
<img width="1366" height="588" alt="image" src="https://github.com/user-attachments/assets/c2f7cf6d-b666-4f38-b9b7-491315af4439" />


## Takeaways
Security groups wo
