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

***C*****reate**  
***R*****ead**  
***U*****pdate**  
***D*****elete**  
  
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
The '=' operator after WHERE acts as a conditional operator for equality.  
  
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

The '=' operator after SET acts as an assignment operator.  
  
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

#### Running SQL files
```sql
SOURCE file_name.sql
```

#### Combine data for cleaner input
```sql
SELECT column_name1 AS easy_to_read_column_name1, 
       column_name2 AS easy_to_read_column_name2, 
       CONCAT(column_name1, seperator, column_name2) AS concatenated_column_name
FROM table_name;
```

_seperator_: ' ', ' - ', ' , ' ...and many more.  

#### Concat many columns with seperator
```sql
SELECT column_name1 AS easy_to_read_column_name1, 
       column_name2 AS easy_to_read_column_name2, 
       CONCAT_WS(seperator, column_name1, column_name2) AS concatenated_column_name
FROM table_name;
```

#### Working with parts of strings
```sql
SELECT SUBSTRING(string, start_index, end_index);
```

1 based indexing  
if end_index is not mentioned then it goes upto the last character of the string  
  
SUBSTR() also works  

#### Replace parts of strings
```sql
SELECT REPLACE(string, substring_we_want_to_remove, substring_we_want_to_replace_with);
```

_substring_we_want_to_remove_ is case sensitive  
  
Use cmd + /  (mac)  
or  
ctrl + /  (pc)  
to comment out SQL  
  
The REPLACE() function, as well as the other string functions, only change the query output, they don't affect the actual data in the database.  


#### Reverse 
```sql
SELECT REVERSE(string);
```

#### Count characters in a string
```sql
SELECT CHAR_LENGTH(string);
```

[SQL Formatter](https://sql-format.com/)  

#### Change a string's case
```sql
SELECT UPPER(string);
SELECT LOWER(string);
```

### Refining Our Selections

#### Distinct
```sql
SELECT DISTINCT column_name FROM table_name;
```

#### Distinct for multiple columns 
```sql
SELECT DISTINCT column_name1, column_name2 FROM table_name;
```

#### Sorting our results (ascending by default)
```sql
SELECT column_name FROM table_name ORDER BY sorted_column_name;
```

#### Sorting our results (descending)
```sql
SELECT column_name FROM table_name ORDER BY sorted_column_name DESC;
```

#### Shortening sorted_column_name
```sql
SELECT column_name1, column_name2, column_name3 FROM table_name ORDER BY 1;
```

Here _1_ can be used instead of writing column_name1, _2_ for column_name2, _3_ for column_name3 ...and so on.  

#### Sort multiple columns
```sql
SELECT column_name1, column_name2, column_name3 FROM table_name ORDER BY column_name1, column_name2;
```

#### Limit
```sql
SELECT column_name FROM table_name LIMIT num;
```

#### Using Limit with Order By
```sql
SELECT column_name FROM table_name ORDER BY sorted_column_name DESC LIMIT start_num, end_num;
```

Here, _start_num_ is optional to use, its default value being 0 (0 based indexing)  
[ start_num, end_num )

#### Selecting rows from a starting point to the end of the table 
```sql
SELECT * FROM table_name LIMIT starting_number, some_gigantic_number;
```
some_gigantic_number: 18446744073709551615 ...and many more.  

#### Better searching
```sql
WHERE column_name LIKE regex;
```

'%': Wildcard (pattern matching for any number of characters)  
regex: '%da%', '%harry%' ...and many more.  

#### More Wildcards
```sql
WHERE column_name LIKE '____'
```

'_': Wildcard (pattern matching for eaxactly one character)  
'\\_': Underscore  
'\\%': Percentage  

## Aggregate Functions

#### Count 
```sql
SELECT COUNT(*) FROM table_name;
```
or
```sql
SELECT COUNT(column_name) FROM table_name;
```
or
```sql
SELECT COUNT(DISTINCT column_name) FROM table_name;
```

#### Group By
```sql
SELECT column_name, COUNT(*) FROM table_name
GROUP BY column_name;
```

GROUP BY summarizes or aggregates identical data into single rows.  
It is to be generally used with other aggregate funtions such as: COUNT.  

#### Min and Max
```sql
SELECT MIN(column_name) FROM table_name;
SELECT MAX(column_name) FROM table_name;
```

#### Subqueries
```sql
SELECT * FROM table_name
WHERE column_name = (SELECT MIN(column_name) FROM table_name);
```
or 
```sql
SELECT * FROM table_name 
ORDER BY column_name ASC LIMIT 1;
```

#### Using Min/Max with Group By
```sql
SELECT column_name, MAX(quantity_column_name)
FROM table_name
GROUP BY column_name;
```

#### Sum
```sql
SELECT SUM(column_name) FROM table_name;
```

#### Using Sum with Group By
```sql
SELECT column_name, SUM(quantity_column_name)
FROM table_name
GROUP BY column_name;
```

#### Average
```sql
SELECT AVG(column_name) FROM table_name;
```

AVG returns a floating point number upto 4 decimal places  

#### Using Average with Group By
```sql
SELECT column_name, AVG(quantity_column_name) 
FROM books 
GROUP BY column_name;
```

## Data Types

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

#### 
```sql

```
