# Databases Lab: Database Table Operations

## Objective
Use CREATE statement to create databases and tables. Use SHOW statement to view available databases and tables. Use ALTER statement to alter the structure of a table. Use DROP statement to delete databases and tables.
<img width="718" height="584" alt="image" src="https://github.com/user-attachments/assets/7aa21a23-401b-49d3-bef0-1ef7a87e1d2d" />


## Steps Taken
1. Logged into the AWS Management Console

## Sample Query
```sql
SHOW DATABASES;
```
```sql
CREATE DATABASE world;
```
```sql
SHOW DATABASES;
```
```sql
CREATE TABLE world.country (
  `Code` CHAR(3) NOT NULL DEFAULT '',
  `Name` CHAR(52) NOT NULL DEFAULT '',
  `Conitinent` enum('Asia','Europe','North America','Africa','Oceania','Antarctica','South  America') NOT NULL DEFAULT 'Asia',
  `Region` CHAR(26) NOT NULL DEFAULT '',
  `SurfaceArea` FLOAT(10,2) NOT NULL DEFAULT '0.00',
  `IndepYear` SMALLINT(6) DEFAULT NULL,
  `Population` INT(11) NOT NULL DEFAULT '0',
  `LifeExpectancy` FLOAT(3,1) DEFAULT NULL,
  `GNP` FLOAT(10,2) DEFAULT NULL,
  `GNPOld` FLOAT(10,2) DEFAULT NULL,
  `LocalName` CHAR(45) NOT NULL DEFAULT '',
  `GovernmentForm` CHAR(45) NOT NULL DEFAULT '',
  `HeadOfState` CHAR(60) DEFAULT NULL,
  `Capital` INT(11) DEFAULT NULL,
  `Code2` CHAR(2) NOT NULL DEFAULT '',
  PRIMARY KEY (`Code`)
);
```
```sql
USE world;
SHOW TABLES;
```
```sql
SHOW COLUMNS FROM world.country;
```
```sql
ALTER TABLE world.country RENAME COLUMN Conitinent TO Continent;
```
```sql
SHOW COLUMNS FROM world.country;
```
```sql
DROP TABLE world.city;
```
```sql
SHOW TABLES;
```
```sql
DROP DATABASE world;
```
```sql
SHOW DATABASES;
```

## Screenshot
_(Optional – paste image if available)_

## Challenges
- 


## Takeaways


