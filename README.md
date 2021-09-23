# SQL-Tutorials

This tutorial works for all the platforms, except for the installation part in which you need to take care of the _package manager_ you use (eg: apt for Debian, Ubuntu and Mint ... and so on).
I will be using **Linux Mint** for the following tutorial:

## Installation

**Step 1:** 
Open Terminal and type
```Shell
sudo apt install mysql-server
systemctl status mysql
```

## Basic Commands

#### Show Databases
```sql
SHOW DATABASES;
```

#### Create Database
```sql
CREATE DATABASE db_name;
```

