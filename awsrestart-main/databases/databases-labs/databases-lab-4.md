# Databases Lab: Performing a Conditional Search

## Objective
Write search conditions using the WHERE clause <br> Use the BETWEEN operator <br> Apply the LIKE operator with wildcard characters <br> Apply functions in a SELECT statement <br> Use functions within a WHERE clause <br> Use the AS operator to create a column alias
<img width="1580" height="1054" alt="image" src="https://github.com/user-attachments/assets/d75cc6ce-60c5-461d-85c1-4c10ff9d479c" />

## Steps Taken
1. Logged into the AWS Management Console
2. Connected to the instance containing the database client (Command Host)
3. Ran the following query to show the existing databases:
      ```sql
      SHOW DATABASES;
      ```
4. Reviewed the table schema:
      ``` sql
      SELECT * FROM world.country;
      ```
5. Filtered the reults:
      ```sql
      SELECT Name, Capital, Region, SurfaceArea, Population FROM world.country WHERE Population >= 50000000 AND Population <= 100000000;
      ```
6. Filtered the results to return the same results as the previous query using BETWEEN:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea, Population FROM world.country WHERE Population BETWEEN 50000000 AND 100000000;
      ```
7. Returned the population of all European countries by using the LIKE function and SUM function:
      ``` sql
      SELECT sum(Population) from world.country WHERE Region LIKE "%Europe%";
      ```
8. Returned the same results as the previous query with the column alias
      ``` sql
      SELECT sum(population) as "Europe Population Total" from world.country WHERE region LIKE "%Europe%";
      ```
9. Performed a case-sensitive search by using the LOWER function:
      ``` sql
      SELECT Name, Capital, Region, SurfaceArea, Population from world.country WHERE LOWER(Region) LIKE "%central%";
      ```
10. Returned the sum of the surface area and sum of the population of North America:
``` sql
SELECT SUM(SurfaceArea) as "N. America Surface Area", SUM(Population) as "N. America Population" FROM world.country WHERE Region = "North America";
```

## Screenshot
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/f112abc2-8a26-4add-adaf-cb4dafe93c68" />
<img width="1366" height="676" alt="image" src="https://github.com/user-attachments/assets/a85181f4-ac19-4c88-9db7-7201c6362e02" />
<img width="1366" height="678" alt="image" src="https://github.com/user-attachments/assets/a7eac24f-c681-4ce9-9ebf-323bf2e5de90" />
<img width="1366" height="679" alt="image" src="https://github.com/user-attachments/assets/bdf5baca-868a-475f-bfd7-508982d21c7f" />


## Challenges
- ...


## Takeaways
When using the BETWEEN operator, the query is easier to read and the operator is inclusive i.e. the beginning and ending values are included.<br>
SQL is not a case-sensitive language.
