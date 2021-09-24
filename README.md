# SQL-Tutorials

This tutorial works for all the platforms, except for the installation part in which you need to take care of the _package manager_ you use (eg: apt for Debian, Ubuntu and Mint ... and so on).  
I will be using **Linux Mint** for the following tutorial:

## Installation

**Step 1:** 
Open Terminal and type
```Shell
sudo apt install mysql-server
```

**Step 2:**
To check that you have successfully installed mysql-server
```Shell
systemctl status mysql
```

**Step 3:**
Securely establish connection using
```Shell
sudo mysql_secure_installation
```

## Run MySQL

```Shell
sudo mysql
```

Use '\q' or '\exit' to quit MySql.

## Creating Databases and Tables

#### Show Databases
```sql
SHOW DATABASES;
```

#### To create a database
```sql
CREATE DATABASE database_name;
```

#### To drop a database
```sql
DROP DATABASE database_name;
```

#### To use a database
```sql
USE database_name;
```

#### To check which database is being used
```sql
SELECT database();
```

#### To create a table
Conventionally, _table_name_ must be pluralised
```sql
CREATE TABLE table_name
  (
    column_name data_type,
    column_name data_type
  );
```
data_type: VARCHAR(size), INT ...and many more.

#### To check if table is created
```sql
SHOW TABLES;
```
or
```sql
SHOW COLUMNS FROM table_name;
```
or
```sql
DESC table_name;
```

#### To drop a table
```sql
DROP table_name;
```

## Inserting Data

#### Inserting data into your tables
```sql
INSERT INTO table_name(column_name) VALUES (data);
```

#### To view all of the data from a table
```sql
SELECT * FROM table_name;
```

#### Inserting multiple data entries
```sql
INSERT INTO table_name 
            (column_name, column_name) 
VALUES      (value, value), 
            (value, value), 
            (value, value);
```

How to insert a string (VARCHAR) value that contains quotations ?  
You can do it a couple of ways:  
- Escape the quotes with a backslash: "This text has \\"quotes\\" in it" or 'This text has \\'quotes\\' in it'
- Alternate single and double quotes: "This text has 'quotes' in it" or 'This text has "quotes" in it'  

#### To view warnings
```sql
SHOW WARNINGS;
```

If you happen to encounter an error instead of a warning then, the solution is to run the following command in your mysql shell:
```sql
set sql_mode='';
```

#### To restrict user from entering empty data (NULL)
```sql
CREATE TABLE table_name
  (
    column_name data_type NOT NULL,
    column_name data_type NOT NULL
  );
```

#### To set default values
```sql
CREATE TABLE table_name
  (
    column_name data_type DEFAULT default_value,
    column_name data_type DEFAULT default_value
  );
```

#### To set default values and to restrict user from entering empty data (NULL)
```sql
CREATE TABLE table_name
  (
    column_name data_type NOT NULL DEFAULT default_value,
    column_name data_type NOT NULL DEFAULT default_value
  );
```

#### To segregate duplicate entries (_use PRIMARY KEY_)
```sql
CREATE TABLE table_name
  (
    id INT NOT NULL AUTO_INCREMENT,
    column_name data_type,
    column_name data_type,
    PRIMARY KEY (id)
  );
```
or
```sql
CREATE TABLE table_name
  (
    id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    column_name data_type,
    column_name data_type
  );
```

## CRUD Commands

**_C_reate**  
**_R_ead**  
**_U_pdate**  
**_D_elete**  
  
### Create

#### Preparing Our Data

We will be using following _cats table_ throughout this CRUD commands section

```sql
CREATE TABLE cats 
  ( 
     cat_id INT NOT NULL AUTO_INCREMENT, 
     name   VARCHAR(100), 
     breed  VARCHAR(100), 
     age    INT, 
     PRIMARY KEY (cat_id) 
  ); 
```

Insert some new cats:

```sql
INSERT INTO cats(name, breed, age) 
VALUES ('Ringo', 'Tabby', 4),
       ('Cindy', 'Maine Coon', 10),
       ('Dumbledore', 'Maine Coon', 11),
       ('Egg', 'Persian', 4),
       ('Misty', 'Tabby', 13),
       ('George Michael', 'Ragdoll', 9),
       ('Jackson', 'Sphynx', 7);
```

### Read

#### Select all columns
```sql
SELECT * FROM table_name;
```

#### Select a specific column
```sql
SELECT column_name FROM table_name;
```

#### Select multiple columns
```sql
SELECT column_name1, column_name2 FROM table_name;
```

#### The WHERE clause
```sql
SELECT * FROM table_name WHERE condition;
```
'=' operator after WHERE acts as a conditional operator for equality.  
The following _conditions_ are same:  
name='Egg'  
name='EGG'  
name='eGg'  
We observe that SQL is _case-insensitive_.  

#### Aliases (Easier to read results)
```sql
SELECT column_name AS easier_to_read_name FROM table_name;
```

### Update

#### UPDATE and SET
```sql
UPDATE table_name SET column_name=some_value WHERE condition;
```

'=' operator after SET acts as an assignment operator.  
Try SELECTing before you UPDATE.  

### Delete

#### DELETE
```sql
DELETE FROM table_name WHERE condition;
```

#### Difference between DELETE and DROP
This deletes all the entries in the table, but the shell remains intact  
i.e. you can still use the table
```sql
DELETE FROM table_name;
```
This deletes all the entries in the table and also deletes the shell  
i.e. the table does not exist after using DROP
```sql
DROP table_name;
```

## The World Of String Functions

#### 
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```

####
```sql

```
