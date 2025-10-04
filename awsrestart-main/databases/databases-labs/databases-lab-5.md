# Databases Lab: Working with Functions

## Objective
<img width="1578" height="948" alt="image" src="https://github.com/user-attachments/assets/131aa146-0e4d-43ba-8fc4-24a8638a8cab" />


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
