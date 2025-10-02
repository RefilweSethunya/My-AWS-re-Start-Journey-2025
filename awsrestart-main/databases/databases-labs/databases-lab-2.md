# Databases Lab: Insert, Update, and Delete Data in a Database

## Objective
Use INSERT statement to add rows into a table<br> Use UPDATE statement to modify rows in a table<br> Use DELETE statement to remove rows from a table<br> Use IMPORT statement to load rows from a database backup file
<img width="882" height="686" alt="image" src="https://github.com/user-attachments/assets/3428b089-4558-45e0-8563-26304daf2e4b" />

## Steps Taken
1. Logged into the AWS Management Console
2. Ran the following query to show the existing databases:
      ```sql
      SHOW DATABASES;
      ```
3. Verified that the country table existed by running:
      ```sql
      SELECT * FROM world.country;
      ```
4. Inserted rows into the country table with the following commands (the values in the VALUES clause were entered in the same order as defined by the table schema):
      ```sql
      INSERT INTO world.country VALUES ('IRL','Ireland','Europe','British Islands',70273.00,1921,3775100,76.8,75921.00,73132.00,'Ireland/Éire','Republic',1447,'IE');
      
      INSERT INTO world.country VALUES ('AUS','Australia','Oceania','Australia and New Zealand',7741220.00,1901,18886000,79.8,351182.00,392911.00,'Australia','Constitutional Monarchy, Federation',135,'AU');
      ```
5. Verified that the two rows were successfully inserted into the country table by running:
      ```sql
      SELECT * FROM world.country WHERE Code IN ('IRL', 'AUS');
      ```
6. Updated the Population column to 0 for both rows in the country table:
      ```sql
      UPDATE world.country SET Population = 0;
      ```
7. Verified that the Population column was updated:
      ```sql
      SELECT * FROM world.country;
      ```
8. Updated the Population and SurfaceArea columns for all rows in the country table:
      ```sql
      UPDATE world.country SET Population = 100, SurfaceArea = 100;
      ```
9. Verified that the Population and SurfaceArea columns were updated:
      ```sql
      SELECT * FROM world.country;
      ```
10. Deleted all rows from the country table:
      ```sql
      SET FOREIGN_KEY_CHECKS = 0;
      DELETE FROM world.country;
      ```
11. Verified that all rows were deleted:
      ```sql
      SELECT * FROM world.country;
      ```
12. Exited the MySQL terminal:
      ```sql
      QUIT;
      ```
13. Verified that the world.sql file had been downloaded:
      ``` bash
      ls /home/ec2-user/world.sql
      ```
14. Loaded rows into the country table by running a SQL script file:
      ``` bash
      mysql -u root --password='re:St@rt!9' < /home/ec2-user/world.sql
      ```
15.  Reconnected to the database:
      ``` bash
      mysql -u root --password='re:St@rt!9'
      ```
16. Verified that the script ran successfully:
      ```sql
      USE world;
      SHOW TABLES;
      ```
17. Verified that the rows were loaded successfully:
      ```sql
      SELECT * FROM country;
      ```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- ...


## Takeaways
Exercise caution when using data manipulation statements such as UPDATE and DELETE because these changes may not be reversible. Because when the DELETE statement does not include a WHERE condition, all rows are deleted.

