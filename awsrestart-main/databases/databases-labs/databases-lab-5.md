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
6. Spilt the string where a space occurs:
      ``` sql
      SELECT Region, substring_index(Region, " ", 1) FROM world.country;
      ```             
7. Searched the rows using a string fragment to filter the records that include Southern in the first part of the region name:
      ``` sql
      SELECT Name, Region from world.country WHERE substring_index(Region, " ", 1) = "Southern";
      ```           
8. Returned only regions that have fewer than 10 characters in their names:
      ``` sql
      SELECT Region FROM world.country WHERE LENGTH(TRIM(Region)) < 10;
      ```
9. Filtered duplicates:
      ``` sql
      SELECT DISTINCT(Region) FROM world.country WHERE LENGTH(TRIM(Region)) < 10;
      ```
10. Returned rows that have Micronesian/Caribbean as the name in the region column. The output should split the region as Micronesia and Caribbean into two separate columns: one named Region Name 1 and one named Region Name 2.
      ``` sql
      SELECT Name, substring_index(Region, "/", 1) as "Region Name 1",substring_index(region, "/", -1) as "Region Name 2" FROM world.country WHERE Region = "Micronesia/Caribbean";
      ```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways
