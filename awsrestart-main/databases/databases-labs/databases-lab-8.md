# Databases Lab: Introduction to Amazon Aurora

## Objective
This lab gives an introduction to Amazon Aurora, a fully managed, MySQL-compatible, relational database engine that combines the performance and reliability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases. <br> It provides a basic understanding of how to use Aurora. Creating an Aurora instance and then connecting to it.

## Steps Taken
1. Logged into the AWS Management Console
2. Created an Aurora instance
   - RDS > Databases > Create database > Configured the following:
     - Choose a database creation method: Standard create
     - Engine type: Aurora (MySQL Compatible)
     - Engine version: the version specified as the default for major version 8.0.
     - Templates: Dev/Test
   - In settings I configured the following:
     - DB cluster identifier: aurora
     - Master username: admin
     - Master password: admin123
     - Confirm password: admin123
   - DB instance class section, I selected Burstable classes (includes t classes), and selected db.t3.medium
   - In the Availability & durability section for Multi-AZ deployment, I selected Don't create an Aurora Replica
   - In the Connectivity section, configured the following:
     - Virtual private cloud (VPC): LabVPC
     - Subnet group: dbsubnetgroup
     - Public access: No
     - VPC security group: Choose existing
     - Existing VPC security groups: DBSecurityGroup
   - In the Monitoring section, cleared the check box for Enable Enhanced monitoring
   - Expanded Additional configuration section, Configured Initial database name: world
   - In the Encryption section, cleared the check box for Enable encryption
   - In the Maintenance section, cleared the check box for Enable auto minor version upgrade
   - Create database
   - Close
3. Connected to the Amazon EC2 Linux instance (Command Host)
4. Configured the Amazon EC2 Linux instance to connect to Aurora
   - Used the yum package manager to install the MariaDB client
      ``` bash
      sudo yum install mariadb -y
      ```
   - Configured the Amazon EC2 Linux instance to connect to the Aurora database
     - AWS Management Console > RDS > Databases > aurora-instance-1 >aurora > Connectivity & security > Endpoints > copy the Endpoint name for the Writer instance (represented as an Aurora specific URL that contains a host address and a port) 
7. Create a table and insert and query records
   - Connect to the database
      ```bash
      mysql -u admin --password='admin123' -h <endpoint_URL>
      mysql -u admin --password='admin123' -h aurora.cluster-cg3cpbctmsdr.us-west-2.rds.amazonaws.com
      ```

   
    - Listed the available databases:
      ```sql
      SHOW DATABASES;
      ```
    - Switched databases:
      ```sql
      USE world;
      ```
    - Created new table is database world:
      ```sql
      CREATE TABLE `country` (
      `Code` CHAR(3) NOT NULL DEFAULT '',
      `Name` CHAR(52) NOT NULL DEFAULT '',
      `Continent` enum('Asia','Europe','North America','Africa','Oceania','Antarctica','South America') NOT NULL DEFAULT 'Asia',
      `Region` CHAR(26) NOT NULL DEFAULT '',
      `SurfaceArea` FLOAT(10,2) NOT NULL DEFAULT '0.00',
      `IndepYear` SMALLINT(6) DEFAULT NULL,
      `Population` INT(11) NOT NULL DEFAULT '0',
      `LifeExpectancy` FLOAT(3,1) DEFAULT NULL,
      `GNP` FLOAT(10,2) DEFAULT NULL,
      `GNPOld` FLOAT(10,2) DEFAULT NULL,
      `LocalName` CHAR(45) NOT NULL DEFAULT '',
      `GovernmentForm` CHAR(45) NOT NULL DEFAULT '',
      `Capital` INT(11) DEFAULT NULL,
      `Code2` CHAR(2) NOT NULL DEFAULT '',
      PRIMARY KEY (`Code`)
      );
      ```
    - Inserted new record:
      ```sql
      INSERT INTO `country` VALUES ('GAB','Gabon','Africa','Central Africa',267668.00,1960,1226000,50.1,5493.00,5279.00,'Le Gabon','Republic',902,'GA');
      
      INSERT INTO `country` VALUES ('IRL','Ireland','Europe','British Islands',70273.00,1921,3775100,76.8,75921.00,73132.00,'Ireland/Éire','Republic',1447,'IE');
      
      INSERT INTO `country` VALUES ('THA','Thailand','Asia','Southeast Asia',513115.00,1350,61399000,68.6,116416.00,153907.00,'Prathet Thai','Constitutional Monarchy',3320,'TH');
      
      INSERT INTO `country` VALUES ('CRI','Costa Rica','North America','Central America',51100.00,1821,4023000,75.8,10226.00,9757.00,'Costa Rica','Republic',584,'CR');
      
      INSERT INTO `country` VALUES ('AUS','Australia','Oceania','Australia and New Zealand',7741220.00,1901,18886000,79.8,351182.00,392911.00,'Australia','Constitutional Monarchy, Federation',135,'AU');
      ```
    - Queried the table
      ```sql
      SELECT * FROM country WHERE GNP > 35000 and Population > 10000000;
      ```

## Screenshot
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/97b615e1-b7a4-44ef-b3c7-142ec868ce41" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/23a37811-f52e-4b7b-a4d0-8e29c4aec381" />
<img width="1366" height="672" alt="image" src="https://github.com/user-attachments/assets/6f4a1462-8e49-40d1-b480-c00606921bf2" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/60916c72-7bec-4c6c-80bd-da2356dbb694" />
<img width="1366" height="680" alt="image" src="https://github.com/user-attachments/assets/b9317fd9-874f-40be-90aa-edd65d4c1578" />
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/60f19dba-5685-474b-afc3-03b2171047b2" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/99d52e3d-8c9f-48ed-97a0-d78f0f81d256" />
<img width="1366" height="675" alt="image" src="https://github.com/user-attachments/assets/fef1db07-aa06-459d-aa8d-a6a4cd47848e" />
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/ad5835c4-9c4b-48d9-8a0f-c4854eb87d64" />
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/f6966baf-c581-4541-9a7f-0c4a659e4e3e" />

<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/01529f91-9d49-43da-9c7d-5ba80b2836bc" />
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/0e5ffd87-8bdc-4899-a566-181628702a8f" />

## Challenges
- 


## Takeaways
There are two types of endpoints are available from an Aurora DB cluster.<br>
Cluster endpoint: A cluster endpoint for an Aurora DB cluster connects to the current primary DB instance for that DB cluster. This endpoint is the only one that can perform write operations such as DDL statements. Because of this, the cluster endpoint is the one that you connect to when you first set up a cluster or when your cluster contains only a single DB instance.

Each Aurora DB cluster has one cluster endpoint and one primary DB instance.
You use the cluster endpoint for all write operations on the DB cluster, including inserts, updates, deletes, and DDL changes. You can also use the cluster endpoint for read operations, such as queries.The cluster endpoint provides failover support for read/write connections to the DB cluster. If the current primary DB instance of a DB cluster fails, Aurora automatically fails over to a new primary DB instance. During a failover, the DB cluster continues to serve connection requests to the cluster endpoint from the new primary DB instance, with minimal interruption of service.
<br>
The following example illustrates a cluster endpoint for an Aurora MySQL DB cluster.
**mydbcluster.cluster-123456789012.us-west-2.rds.amazonaws.com:3306**
<br>
<br>
Reader endpoint: A reader endpoint for an Aurora DB cluster connects to one of the available Aurora replicas for that DB cluster. Each Aurora DB cluster has one reader endpoint. If there is more than one Aurora replica, the reader endpoint directs each connection request to one of the Aurora replicas. The reader endpoint provides load-balancing support for read-only connections to the DB cluster. Use the reader endpoint for read operations, such as queries. You can't use the reader endpoint for write operations. The DB cluster distributes connection requests to the reader endpoint among the available Aurora replicas. If the DB cluster contains only a primary DB instance, the reader endpoint serves connection requests from the primary DB instance. If one or more Aurora replicas are created for that DB cluster, subsequent connections to the reader endpoint are load balanced among the replicas.
<br>
The following example represents a reader endpoint for an Aurora MySQL DB cluster.
**mydbcluster.cluster-ro-123456789012.us-west-2.rds.amazonaws.com:3306**
