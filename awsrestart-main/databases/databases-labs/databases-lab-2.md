# Databases Lab: Insert, Update, and Delete Data in a Database

## Objective
Use INSERT statement to add rows into a table. Use UPDATE statement to modify rows in a table. Use DELETE statement to remove rows from a table. Use IMPORT statement to load rows from a database backup file.
<img width="882" height="686" alt="image" src="https://github.com/user-attachments/assets/3428b089-4558-45e0-8563-26304daf2e4b" />

## Steps Taken
1. Logged into the AWS Management Console
2. To show the existing databases, run the following query
      ```sql
      SHOW DATABASES;
      ```
3. To verify that the country table exists, run the following command
      ```sql
      SELECT * FROM world.country;
      ```
4. To insert rows into the country table, run the following commands. The values in the VALUES clause need to be in the same order as defined by the table schema.
      ```sql
      INSERT INTO world.country VALUES ('IRL','Ireland','Europe','British Islands',70273.00,1921,3775100,76.8,75921.00,73132.00,'Ireland/Éire','Republic',1447,'IE');
      
      INSERT INTO world.country VALUES ('AUS','Australia','Oceania','Australia and New Zealand',7741220.00,1901,18886000,79.8,351182.00,392911.00,'Australia','Constitutional Monarchy, Federation',135,'AU');
      ```
5. To verify that two rows were successfully inserted into the country table, run the following query.
      ```sql
      SELECT * FROM world.country WHERE Code IN ('IRL', 'AUS');
      ```
6. To set the value in the Population column to 0 for both rows in the country table, run the following UPDATE statement
      ```sql
      UPDATE world.country SET Population = 0;
      ```
7. To verify that the Population column in the country table was updated, run the following command
      ```sql
      SELECT * FROM world.country;
      ```
8. To update the Population and SurfaceArea columns for all rows in the country table, run the following UPDATE statement
      ```sql
      UPDATE world.country SET Population = 100, SurfaceArea = 100;
      ```
9. To verify that the Population and SurfaceArea columns in the country table were updated, run the following command
      ```sql
      SELECT * FROM world.country;
      ```
10. To delete ALL rows from the country table, run the following
      ```sql
      SET FOREIGN_KEY_CHECKS = 0;
      DELETE FROM world.country;
      ```
11. To verify that all rows have been deleted from the country table, run the following query
      ```sql
      SELECT * FROM world.country;
      ```
12. To exit the MySQL terminal
      ```sql
      QUIT;
      ```
13. To verify that the world.sql file has been downloaded
      ``` bash
      ls /home/ec2-user/world.sql
      ```
14. It is possible to create a SQL script file containing a group of SQL statements to quickly load data into a database. To load rows into the country table, we run the following command
      ``` bash
      mysql -u root --password='re:St@rt!9' < /home/ec2-user/world.sql
      ```
15.  Reconnect to the database, run the following command.
      ``` bash
      mysql -u root --password='re:St@rt!9'
      ```
16. To verify that the script ran successfully, run
      ```sql
      USE world;
      SHOW TABLES;
      ```
17. verify that the rows were loaded successfully
      ```sql
      SELECT * FROM country;
      ```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- ...


## Takeaways
Exercise caution when using data manipulation statements such as UPDATE and DELETE because these changes may not be reversible. Because the DELETE statement does not include a WHERE condition, all rows are deleted.

