# Databases Lab: Working with Functions

## Objective
Use aggregate functions SUM(), MIN(), MAX() and AVG() to summarize data <br>
Use the SUBSTRING_INDEX() function to split strings<br>
Use the LENGTH() and TRIM() functions to determine the length of a string<br>
Use the DISTINCT() function to filter duplicate records<br>
Use functions in the SELECT statement and WHERE clause<br>
<img width="1578" height="948" alt="image" src="https://github.com/user-attachments/assets/131aa146-0e4d-43ba-8fc4-24a8638a8cab" />

## Steps Taken
1. Logged into the AWS Management Console
2. Connected to the instance containing the database client (Command Host)
3. Ran the following query to show the existing databases:
      ```sql
      SHOW DATABASES;
      ```
4. Reviewed the table schema, data, and number of rows in the country table:
      ``` sql
      SELECT * FROM world.country;
      ```
5. Aggregated data from all records in the country table```sql
      ``` sql
      SELECT sum(Population), avg(Population), max(Population), min(Population), count(Population) FROM world.country;
      ```
6. 
## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways
