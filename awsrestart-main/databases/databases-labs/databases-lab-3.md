# Databases Lab: Selecting Data from a Database

## Objective
Use the SELECT statement to query a database<br>
Apply the COUNT() function to return the number of rows in a result set<br>
Use the following operators to filter and organize query results:<br>
- '<'
- '>'
- '='
- WHERE
- ORDER BY
- AND
<img width="1582" height="886" alt="image" src="https://github.com/user-attachments/assets/3a5606a0-bd8f-4a8a-862a-a8c80729b010" />


## Steps Taken
1. Logged into the AWS Management Console
2. Connected to the instance containing the database client (Command Host)
3. Ran the following query to show the existing databases:
      ```sql
      SHOW DATABASES;
      ```
4. Listed all rows and columns in the country table:
      ``` sql
      SELECT * FROM world.country;```sql
      SELECT users.name, orders.amount
      FROM users
      JOIN orders ON users.id = orders.user_id
      WHERE orders.amount > 100;
      ```
5. Queried the number of rows in the country table:
      ``` sql
      SELECT COUNT(*) FROM world.country;
      ```
6. Listed all columns in the country table:
      ``` sql
      SHOW COLUMNS FROM world.country;
      ```
7. Queried specific columns in the world table:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea, Population FROM world.country;
      ```
8. Added a more descriptive column name to the query output:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population FROM world.country;
      ```
9. Ordered result set by specific column:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population FROM world.country ORDER BY Population;
      ```
10. Ordered the data in descending order:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population FROM world.country ORDER BY Population DESC;
      ```
11. Listed all rows with a population greater than 50,000,000:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population FROM world.country WHERE Population > 50000000 ORDER BY Population DESC;
      ```
12. Listed all rows with a population greater than 50,000,000 and all rows with a population less than 100,000,000:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population FROM world.country WHERE Population > 50000000 AND Population < 100000000 ORDER BY Population DESC;
      ```
13. Listed countries in Southern Europe that have a population greater than 50,000,000:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea AS "Surface Area", Population from world.country WHERE Population > 50000000 AND Region = "Southern Europe";
      ```
     
## Screenshot


## Challenges
- 


## Takeaways
