# Databases Lab: Build and Access an RDS Server

## Objective
This lab is designed to reinforce the concept of leveraging an AWS-managed database instance for solving relational database needs by creating an RDS instance and using the Amazon RDS Query Editor to query data.

## Steps Taken
1. Logged into the AWS Management Console
2. Launch an Amazon RDS DB instance

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
