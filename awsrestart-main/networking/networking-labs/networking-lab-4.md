# Networking Lab: Networking resources for a VPC

## Objective
Create a VPC, Internet Gateway, Route Table, Security Group, Network Access List and EC2 instance to create a routable network within the VPC. See the customer VPC architecture below.

<img width="741" height="401" alt="image" src="https://github.com/user-attachments/assets/731fb016-735f-4cae-889e-57dbae7a0229" />


## Steps Taken
1. Logged into AWS Management Console
2. Created VPC.
   - Name : Test VPC
   - IPv4 CIDR block: 192.168.0.0/18
4. Created subnet in VPC
5. Created route table
6. Created Internet Gateway (IGW)
7. Added route to route table and associated subnet to route table
8. Created network ACL
    - Name: Public Subnet NACL
    - VPC: Chose Test VPC from dropdown
9. Edited NACL inbound rules, Added new rule
   - Rule number: 100
   - Type: Chose All traffic from dropdown
10. Edited NACL outbound rules, Added new rule
    - Rule number: 100
    - Type: Chose All traffic from dropdown
11. Created security group
12. Launched EC2 instance
    - Quick Start: Amazon Linux
    - Amazon Machine Image (AMI): Amazon Linux 2023 AMI
    - Instance type: t3.micro
    - Key pair (login): vockey
    - VPC: Test VPC (In Network section)
    - Subnet: Public Subnet
    - Auto-assign public IP: Enable
    - Firewall (security groups): Select existing security group i.e public security group.
13. Use SSH to connect to an Amazon Linux EC2 instance and use ping test to test connectivity.

## Challenges
- Forgot to attach IGW to VPC so when adding route to route table, the IGW was missing as target source in the dropdown.

## Screenshot
VPC Configuration
<img width="1366" height="414" alt="image" src="https://github.com/user-attachments/assets/8fd26e21-5899-4959-97aa-41e61776dc61" />
Subnet Configuration
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/f1d5611b-7de1-47cd-9292-33382479be15" />
<img width="1366" height="634" alt="image" src="https://github.com/user-attachments/assets/fbef5e8e-a2c2-44d9-95eb-37c6b3498937" />
Route Table Configuration
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/dba244f7-2c87-43fb-b7c1-81914f7f1ee0" />
<img width="1366" height="637" alt="image" src="https://github.com/user-attachments/assets/75cba2ce-9a11-4d9f-9457-96a2d3a263fe" />
Internet Gateway (IGW) Configuration
<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/a72b162c-6f38-413a-994d-e02cf27653c2" />
<img width="1366" height="634" alt="image" src="https://github.com/user-attachments/assets/e6975afb-19cd-4d28-a89c-659c1aeb4c70" />
<img width="1366" height="468" alt="image" src="https://github.com/user-attachments/assets/2820e73e-885f-43e7-adf5-9fb24bbf9ddb" />
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/8ae137f9-a6d3-4a6d-94e3-6a8bd93a0602" />
Network ACL Configuration
Inbound
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/08c1c8db-2003-499f-ac07-3e170ec66876" />
Outbound
<img width="1366" height="640" alt="image" src="https://github.com/user-attachments/assets/b5f13151-c625-403c-95ad-4fca8a614d0f" />
Security Group Configuration
<img width="1366" height="429" alt="image" src="https://github.com/user-attachments/assets/1582abf7-32d7-457e-a030-09de0812c223" />
For Inbound rules I have allowed SSH, HTTP, and HTTPS traffic, each of which has its own protocols and port range. The source from which this traffic reaches your instance can be originating from anywhere.
For Outbound rules, I have allowed all traffic from outside my instance.
<img width="1366" height="639" alt="image" src="https://github.com/user-attachments/assets/284eefc7-85a6-40a5-915e-cc4d8456fcf3" />
EC2 Configuration
<img width="1366" height="641" alt="image" src="https://github.com/user-attachments/assets/385ad3bf-d55b-4d8f-89be-b5e6e6035691" />
Successful ping test result. 0% packet loss.
<img width="944" height="489" alt="image" src="https://github.com/user-attachments/assets/ddafa724-bd63-481e-b00d-a70913a2f472" />




## Takeaways
Creating a VPC architecture can be done in any order. However adding structure to it will ensure you dont skip any steps.
