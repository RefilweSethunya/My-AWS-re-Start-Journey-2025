# Databases Lab: Build Your Database Server and Interact with Your DB Using an App

## Objective
The objective of this lab is to gain hands-on experience with Amazon RDS by launching a highly available DB instance, configuring secure connectivity and integrating it with a web application. The focus is on understanding how managed database services simplify administration while providing scalability and reliability.

Final Architecture
<img width="1064" height="507" alt="image" src="https://github.com/user-attachments/assets/100608b6-baf8-40a4-82bc-bbc025962635" />

## Steps Taken
1. Logged into the AWS Management Console
2. Created a Security Group for the RDS DB Instance
   - Networking & Content Delivery > VPC > Security Groups > Create security group > Configured the following:
     - Security group name: DB Security Group
     - Description: Permit access from Web Security Group
     - VPC: Lab VPC
   - In the Inbound rules section > Add rule > Configured the following:
     - Type: MySQL/Aurora (3306)
     - Source: Web Security Group
   - Create security group
4. Created a DB Subnet Group
   - Database > RDS > Subnet groups > Create DB Subnet Group > Configured the following:
     - Name: DB Subnet Group
     - Description: DB Subnet Group
     - VPC ID: Lab VPC
     - In the Add subnets section for Availability zones selected the first and second AZs
     - Added Private Subnet 1 (10.0.1.0/24) and Private Subnet 2 (10.0.3.0/24)
   - Create
5. Created an Amazon RDS DB Instance
   -  Databases > Create database > Standard create
   -  Engine type: MySQL
   -  Engine version: latest version
   -  Templates: Dev/Test
   -  Availability and durability: Multi-AZ DB Instance
   -  DB instance identifier: lab-db
   -  Master username: main
   -  Master password: lab-password
   -  Confirm password: lab-password
   -  Under Instance configuration, configured the following for DB instance class
     - Burstable classes (includes t classes), selected db.t3.medium
   - Under Storage, configured:
     - Storage type: General Purpose (SSD)
   - Under Connectivity, configured:
     - Virtual Private Cloud (VPC): Lab VPC
     - Existing VPC security groups: DB Security Group
   - Under Monitoring, Enhanced Monitoring, unchecked Enable Enhanced monitoring
   - Initial database name: lab
   - Under Backup, unchecked Enable automated backups
   - Create database
6. Interacted with Database
   - Clicked the RDS link at the top of the web application page,
   - Configured the application to connect to my database:
     - Endpoint: Endpoint
     - Database: lab
     - Username: main
     - Password: lab-password
   - Submit

## Screenshot
<img width="1366" height="671" alt="image" src="https://github.com/user-attachments/assets/6c2c6096-8792-4071-ab41-c5dda99486f2" />
<img width="1366" height="656" alt="image" src="https://github.com/user-attachments/assets/ec24529a-0ba7-4a7a-be73-0081f46d954a" />
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/b18ca591-78a7-4a91-a60a-ac9ffb23f9e1" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/761b8bdf-93cd-4797-a364-24d4ec8026b6" />
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/33e41f47-87f8-42bb-94d5-684c503cfdc3" />
<img width="1366" height="358" alt="image" src="https://github.com/user-attachments/assets/7f535119-e7f2-402c-a98c-0c2ad4768670" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/e843ab30-b4bb-40ac-b9e7-edd8a4c3c398" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/b29b40ee-7321-42fb-a6e6-746dc8cf02b7" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/f4bee373-407e-4002-91d0-45684812931a" />
<img width="1366" height="669" alt="image" src="https://github.com/user-attachments/assets/c12656e3-3896-4c12-94cb-6e49fb5a67aa" />



## Challenges
- 


## Takeaways
