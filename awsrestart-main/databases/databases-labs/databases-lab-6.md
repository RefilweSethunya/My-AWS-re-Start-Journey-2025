# Databases Lab: Organizing Data

## Objective
<img width="1582" height="884" alt="image" src="https://github.com/user-attachments/assets/151a5c16-dc06-47bf-a62f-59d351ed1156" />


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
5. Returned a list of records where the Region is Australia and New Zealand ordered by descending population:
      ``` sql
      SELECT Region, Name, Population FROM world.country WHERE Region = 'Australia and New Zealand' ORDER By Population desc;
      ```
6. Grouped related records together:
      ``` sql
      SELECT Region, SUM(Population) FROM world.country WHERE Region = 'Australia and New Zealand' GROUP By Region ORDER By SUM(Population) desc;
      ```
7. Generated a running total by grouping and then aggregating the records. The output displays the population of a country along side a running total of the region
      ``` sql
      SELECT Region, Name, Population, SUM(Population) OVER(partition by Region ORDER BY Population) as 'Running Total' FROM world.country WHERE Region = 'Australia and New Zealand';
      ```
8. Grouped the records by Region and ordered by Population and generated a rank number
      ``` sql
      SELECT Region, Name, Population, SUM(Population) OVER(partition by Region ORDER BY Population) as 'Running Total', RANK() over(partition by region ORDER BY population) as 'Ranked' FROM world.country WHERE region = 'Australia and New Zealand';
      ```
9. Listed by rank
      ``` sql
      SELECT Region, Name, Population, RANK() OVER(partition by Region ORDER BY Population desc) as 'Ranked' FROM world.country order by Region, Ranked;
      ```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways
