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
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/9dfb7f69-71ea-4570-b0ac-86cfbd5719e7" />
<img width="1366" height="651" alt="image" src="https://github.com/user-attachments/assets/39d1a426-4a51-4ad9-b0a7-339a9312db04" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/03c5d392-a752-4a65-a91e-39cbf5b635bb" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/5a47645b-a156-476e-b832-fb6196531d82" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/de647a0d-4336-4f86-b283-eca1114af1ac" />
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/fbade070-d9e6-4f1b-b3c1-ca48bc421679" />


## Challenges
- Accidentally created subnets in the same az, so I had to deletec the second subnet and even the subnetid changed, in order to create subnet group.
- <img width="1366" height="191" alt="image" src="https://github.com/user-attachments/assets/ad1df002-c85b-4975-bdf7-cf68f62be2e7" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/870fb7b2-2997-46c8-816b-1b3cd99f7940" />
<br>
- the maria db version in the command was not supported so I had to find the list of supported ones available, opted for version 10.5.25 which worked
- <img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/cc61c589-0b32-40c7-a840-b325d8425258" />
- <img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/e607cd0f-e3f4-4d3f-87ca-082cf7948d4d" />



## Takeaways
By migrating from a self-managed EC2 database to RDS I have reinforced the value of using Amazon RDS as a managed service to simplify my database operations. For example, Amazon RDS automatically sends metrics to CloudWatch every minute for each active database.
