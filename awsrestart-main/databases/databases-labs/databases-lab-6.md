# Databases Lab: Organizing Data

## Objective
Use the GROUP BY clause with the aggregate function SUM()<br>
Use the OVER clause with the RANK() window function<br>
Use the OVER clause with the aggregate function SUM() and the RANK() window function
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
<img width="1366" height="673" alt="image" src="https://github.com/user-attachments/assets/9bc0b5ac-c4aa-4998-b01e-1b91d2ccf875" />
<img width="1366" height="677" alt="image" src="https://github.com/user-attachments/assets/719483f6-536a-48bc-b632-7b8e87097584" />
<img width="1366" height="680" alt="image" src="https://github.com/user-attachments/assets/0e3df646-6796-4a07-ab2e-b202f64d8630" />
<img width="1366" height="674" alt="image" src="https://github.com/user-attachments/assets/f2e87d65-80b8-43b9-beeb-6b67e74f7d1a" />

<img width="1366" height="679" alt="image" src="https://github.com/user-attachments/assets/e7e9d009-b2e9-4659-a5f1-700f4c230059" />

## Challenges
- 


## Takeaways
