# Databases Lab: Introduction to Amazon Aurora

## Objective


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
