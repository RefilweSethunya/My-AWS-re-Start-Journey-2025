# Databases Lab: Database Table Operations

## Objective
Use CREATE statement to create databases and tables. Use SHOW statement to view available databases and tables. Use ALTER statement to alter the structure of a table. Use DROP statement to delete databases and tables.
<img width="718" height="584" alt="image" src="https://github.com/user-attachments/assets/7aa21a23-401b-49d3-bef0-1ef7a87e1d2d" />


## Steps Taken
1. Logged into the AWS Management Console
2. Connected to the Command Host
3. Created a database(world) and a table(country)
4. To show the existing databases, run the following query
    ```sql
    SHOW DATABASES;
    ```

5. To create a new database named world, run the following query
      ```sql
      CREATE DATABASE world;
      ```
6. To verify that the world database has been created, run the following query
      ```sql
      SHOW DATABASES;
      ```
7. To create a table named country, with a well-defined structure, known as a table schema run the following 
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
8. To verify that the country table was created, use the SHOW TABLES; command to list the tables in the database. To specify which database to run a query against use the USE command
      ```sql
      USE world;
      SHOW TABLES;
      ```
9. To list all columns and their properties in the country table run the following query
      ```sql
      SHOW COLUMNS FROM world.country;
      ```
10. To alter the table's schema i.e. to fix the incorrectly spelled Continent column, run the following command
      ```sql
      ALTER TABLE world.country RENAME COLUMN Conitinent TO Continent;
      ```
11. To verify that the Continent column name in the country table has been corrected, run the following query
      ```sql
      SHOW COLUMNS FROM world.country;
      ```
12. To drop the city table, run the following command 
      ```sql
      DROP TABLE world.city;
      ```
13. To verify that both tables have been dropped, run the following command
      ```sql
      SHOW TABLES;
      ```
14. To drop the world database, run the following command
      ```sql
      DROP DATABASE world;
      ```
15. To verify that the world database has been deleted, run the following query
      ```sql
      SHOW DATABASES;
      ```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways
Once a table has been dropped, it cannot be recovered unless a backup is available. 

