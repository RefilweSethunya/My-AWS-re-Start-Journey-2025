# Databases Lab: Database Table Operations

## Objective
Use CREATE statement to create databases and tables<br> Use SHOW statement to view available databases and tables<br> Use ALTER statement to alter the structure of a table<br> Use DROP statement to delete databases and tables
<img width="718" height="584" alt="image" src="https://github.com/user-attachments/assets/7aa21a23-401b-49d3-bef0-1ef7a87e1d2d" />


## Steps Taken
1. Logged into the AWS Management Console
2. Connected to the Command Host
3. Created a database(world) and a table(country)
4. Showed the existing databases by running:
    ```sql
    SHOW DATABASES;
    ```

5. Created a new database named world by running:
      ```sql
      CREATE DATABASE world;
      ```
6. Verified that the world database was created by running:
      ```sql
      SHOW DATABASES;
      ```
7. Created a table named country with the following schema: 
      ```sql
      CREATE TABLE world.country (
        `Code` CHAR(3) NOT NULL DEFAULT '',
        `Name` CHAR(52) NOT NULL DEFAULT '',
        `Conitinent` enum('Asia','Europe','North America','Africa','Oceania','Antarctica','South  America') NOT NULL DEFAULT 'Asia',
        `Region` CHAR(26) NOT NULL DEFAULT '',
        `SurfaceArea` FLOAT(10,2) NOT NULL DEFAULT '0.00',
        `IndepYear` SMALLINT(6) DEFAULT NULL,
        `Population` INT(11) NOT NULL DEFAULT '0',
        `LifeExpectancy` FLOAT(3,1) DEFAULT NULL,
        `GNP` FLOAT(10,2) DEFAULT NULL,
        `GNPOld` FLOAT(10,2) DEFAULT NULL,
        `LocalName` CHAR(45) NOT NULL DEFAULT '',
        `GovernmentForm` CHAR(45) NOT NULL DEFAULT '',
        `HeadOfState` CHAR(60) DEFAULT NULL,
        `Capital` INT(11) DEFAULT NULL,
        `Code2` CHAR(2) NOT NULL DEFAULT '',
        PRIMARY KEY (`Code`)
      );
      ```
8. Verified that the country table was created by running:
      ```sql
      USE world;
      SHOW TABLES;
      ```
9. Listed all columns and their properties in the country table by running:
      ```sql
      SHOW COLUMNS FROM world.country;
      ```
10. Corrected the misspelled Conitinent column by running:
      ```sql
      ALTER TABLE world.country RENAME COLUMN Conitinent TO Continent;
      ```
11. Verified that the column name was corrected by running:
      ```sql
      SHOW COLUMNS FROM world.country;
      ```
12. Dropped the city table by running:
      ```sql
      DROP TABLE world.city;
      ```
13. Verified that the table was dropped by running:
      ```sql
      SHOW TABLES;
      ```
14. Dropped the world database by running:
      ```sql
      DROP DATABASE world;
      ```
15. Verified that the world database was deleted by running:
      ```sql
      SHOW DATABASES;
      ```

## Screenshot
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/b7fc99cd-10ae-4aa2-b917-176330b67564" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/85f5992a-1a73-4625-aeb7-031e5f9cd791" />
<img width="1366" height="682" alt="image" src="https://github.com/user-attachments/assets/0c91899b-6225-43a8-9fbf-1d2147d32304" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/966daaa8-d8d0-445b-af23-311be0a5614c" />


## Challenges
- ...


## Takeaways
Once a table has been dropped, it cannot be recovered unless a backup is available. 

