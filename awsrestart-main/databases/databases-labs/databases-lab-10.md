# Databases Lab: Migrate to Amazon RDS

## Objective
In this lab I create an Amazon RDS MariaDB instance using the AWS CLI, migrate data from a MariaDB database running on an EC2 instance to an Amazon RDS instance, and monitor the RDS instance by using Amazon CloudWatch metrics.

<img width="1516" height="878" alt="image" src="https://github.com/user-attachments/assets/68e7c1d3-fb78-4e03-bd36-612f5239d504" />

## Steps Taken
1. Logged into the AWS Management Console
2. Created an Amazon RDS instance by using the AWS CLI
   - Configured AWS CLI
      ``` bash
      aws configure
      ```
   - Configured Security groups, subnets as per the final architecture
    
4. Migrated application data to the Amazon RDS instance
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
5. Configured the website to use the Amazon RDS instance
   - AWS Management Console > Systems Manager > Parameter Store > /cafe/dbUrl > Edit
   - In the Parameter details page, I replaced the text in the Value box with the RDS Instance Database Endpoint Address
   - Save Changes
6. Monitored the performance of a database instance
   - AWS Management Console > RDS > Databases > cafedbinstance > Monitoring tab
   - Observed the displayed metrics

## Screenshot
_(Optional – paste image if available)_

## Challenges
- ...

## Takeaways
By migrating from a self-managed EC2 database to RDS I have reinforced the value of using Amazon RDS as a managed service to simplify my database operations. For example, Amazon RDS automatically sends metrics to CloudWatch every minute for each active database.
