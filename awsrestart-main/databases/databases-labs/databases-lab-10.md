# Databases Lab: Migrate to Amazon RDS

## Objective
In this lab I create an Amazon RDS MariaDB instance using the AWS CLI, migrate data from a MariaDB database running on an EC2 instance to an Amazon RDS instance, and monitor the RDS instance by using Amazon CloudWatch metrics.

<img width="1516" height="878" alt="image" src="https://github.com/user-attachments/assets/68e7c1d3-fb78-4e03-bd36-612f5239d504" />

## Steps Taken
1. Logged into the AWS Management Console
2. Created the Amazon RDS instance by using the AWS CLI
   - Configured AWS CLI
      ``` bash
      aws configure
      ```
   - Configured Security groups, Private Subnets as per the final architecture diagam
     - Created CafeDatabaseSG Security Group
         ``` bash
         aws ec2 create-security-group \
         --group-name CafeDatabaseSG \
         --description "Security group for Cafe database" \
         --vpc-id <CafeInstance VPC ID>
         ```
     - Created Inbound Rule
         ``` bash
         aws ec2 authorize-security-group-ingress \
         --group-id <CafeDatabaseSG Group ID> \
         --protocol tcp --port 3306 \
         --source-group <CafeSecurityGroup Group ID>
         ```
     - Confirmed Inbound Rule
         ``` bash
         aws ec2 describe-security-groups \
         --query "SecurityGroups[*].[GroupName,GroupId,IpPermissions]" \
         --filters "Name=group-name,Values='CafeDatabaseSG'"
         ```
     - Created CafeDB Private Subnet 1
         ``` bash
         aws ec2 create-subnet \
         --vpc-id <CafeInstance VPC ID> \
         --cidr-block 10.200.2.0/23 \
         --availability-zone <CafeInstance Availability Zone>
         ```
     - Created CafeDB Private Subnet 2
         ``` bash
         aws ec2 create-subnet \
         --vpc-id <CafeInstance VPC ID> \
         --cidr-block 10.200.10.0/23 \
         --availability-zone <availability-zone>
         ```
     - Created Subnet Group
         ``` bash
         aws rds create-db-subnet-group \
         --db-subnet-group-name "CafeDB Subnet Group" \
         --db-subnet-group-description "DB subnet group for Cafe" \
         --subnet-ids <Cafe Private Subnet 1 ID> <Cafe Private Subnet 2 ID> \
         --tags "Key=Name,Value= CafeDatabaseSubnetGroup"
         ```    
3. Migrated the application data to the Amazon RDS instance
   - Connected to CafeInstance
   - Created a backup of the local cafe_db database
      ``` sql
      mysqldump --user=root --password='Re:Start!9' \
      --databases cafe_db --add-drop-database > cafedb-backup.sql
      ```
   - Restored the backup to the Amazon RDS database
      ``` sql
      mysql --user=root --password='Re:Start!9' \
      --host=<RDS Instance Database Endpoint Address> \
      < cafedb-backup.sql
      ```
   - Verified cafe_db was successfully created and populated in the Amazon RDS instance
      ``` sql
      mysql --user=root --password='Re:Start!9' \
      --host=<RDS Instance Database Endpoint Address> \
      cafe_db
      ```
      ``` sql
      select * from product;
      ```
      ``` sql
      exit
      ```
4. Configured the website to use the Amazon RDS instance
   - AWS Management Console > Systems Manager > Parameter Store > /cafe/dbUrl > Edit
   - In the Parameter details page, I replaced the text in the Value box with the RDS Instance Database Endpoint Address
   - Save Changes
5. Monitored the performance of a database instance
   - AWS Management Console > RDS > Databases > cafedbinstance > Monitoring tab
   - Observed the displayed metrics

## Screenshot
<img width="1366" height="726" alt="image" src="https://github.com/user-attachments/assets/18566936-69e2-4058-8c83-a24b37314ab6" />
<img width="1366" height="720" alt="image" src="https://github.com/user-attachments/assets/73510ce7-59a9-4f7e-8676-85715b08334b" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/9dfb7f69-71ea-4570-b0ac-86cfbd5719e7" />
<img width="1366" height="651" alt="image" src="https://github.com/user-attachments/assets/39d1a426-4a51-4ad9-b0a7-339a9312db04" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/03c5d392-a752-4a65-a91e-39cbf5b635bb" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/5a47645b-a156-476e-b832-fb6196531d82" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/de647a0d-4336-4f86-b283-eca1114af1ac" />
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/fbade070-d9e6-4f1b-b3c1-ca48bc421679" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/5d060abb-0c52-4fd6-b128-f30200291d3b" />
<img width="1366" height="330" alt="image" src="https://github.com/user-attachments/assets/9602a497-9afb-4924-86b5-ac134043fdf2" />
<img width="1366" height="539" alt="image" src="https://github.com/user-attachments/assets/f2838406-2837-4499-8e64-17396a4a5343" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/40cfe3cc-667e-418c-9ab3-b0520983326a" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/3341d8b0-4369-422e-96e5-293e2e0dc5fc" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/b5f76281-5b86-4c67-af02-25b020d6b02c" />
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/2ee80d9e-fc66-4b46-805c-c2c3c7aff81a" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/4a81b5d2-55f6-4731-8be2-91859eb4a334" />
<img width="1366" height="682" alt="image" src="https://github.com/user-attachments/assets/63c7a267-7f61-448e-af20-64f69e8aea93" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/791157f7-1e47-4a79-a237-c90711bb5846" />
<img width="1366" height="670" alt="image" src="https://github.com/user-attachments/assets/4e202c89-328e-4a09-b2ca-7f290a65ff1f" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/4046352c-bf54-46a8-88c4-9c3ebf96096f" />


## Challenges
- I initially created both subnets in the same Availability Zone, which did not meet the RDS subnet group requirement for multi-AZ coverage. To resolve this, I had to delete the second subnet and recreate it in a different AZ. This also resulted in a new Subnet ID being generated before I could successfully build the subnet group. Here is the error and the solution.
<img width="1366" height="191" alt="image" src="https://github.com/user-attachments/assets/ad1df002-c85b-4975-bdf7-cf68f62be2e7" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/870fb7b2-2997-46c8-816b-1b3cd99f7940" />
<br>
- The MariaDB version I specified in the command (10.5.13) was not supported in Amazon RDS. I had to list the available engine versions and then select 10.5.25, which worked successfully.
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/cc61c589-0b32-40c7-a840-b325d8425258" />
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/e607cd0f-e3f4-4d3f-87ca-082cf7948d4d" />



## Takeaways
By migrating from a self-managed EC2 database to RDS I have reinforced the value of using Amazon RDS as a managed service to simplify my database operations. For example, Amazon RDS automatically sends metrics to CloudWatch every minute for each active database.
