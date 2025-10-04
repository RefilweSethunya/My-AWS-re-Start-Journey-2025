# Databases Lab: Selecting Data from a Database

## Objective
Use the SELECT statement to query a database<br>
Apply the COUNT() function to return the number of rows in a result set<br>
Use the following operators to filter and organize query results:<br>
- <
-
- =
- WHERE
- ORDER BY
- AND
<img width="1582" height="884" alt="image" src="https://github.com/user-attachments/assets/71f6c134-b935-4fb8-80ab-b7a34faf3e3b" />

## Steps Taken
1. Logged into the AWS Management Console

## Sample Query
```sql
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id
WHERE orders.amount > 100;
```
```sql
SELECT users.name, orders.amount
FROM users
JOIN orders ON users.id = orders.user_id
WHERE orders.amount > 100;
```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways
