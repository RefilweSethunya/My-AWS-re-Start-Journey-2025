# Databases Lab: Migrate to Amazon RDS

## Objective
In this lab I create an Amazon RDS MariaDB instance using the AWS CLI, migrate data from a MariaDB database running on an EC2 instance to an Amazon RDS instance, and monitor the RDS instance by using Amazon CloudWatch metrics.

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
By migrating from a self-managed EC2 database to RDS I have reinforced the value of using Amazon RDS as a managed service to simplify my database operations.
