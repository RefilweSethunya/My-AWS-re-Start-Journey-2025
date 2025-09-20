# Databases Lab: Database Table Operations

## Objective
Use SELECT, WHERE, and JOIN clauses on multiple tables

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
SELECT * FROM customers WHERE country='Botswana';
```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways


