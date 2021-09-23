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

## Basic Commands

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

####
```sql
;
```
