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
_(Optional – paste image if available)_

## Challenges
- ...

## Takeaways
By migrating from a self-managed EC2 database to RDS I have reinforced the value of using Amazon RDS as a managed service to simplify my database operations. For example, Amazon RDS automatically sends metrics to CloudWatch every minute for each active database.
