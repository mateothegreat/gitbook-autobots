---
description: Using MySQL as our database engine.
---

# Database Setup

## Installation

Download and install MySQL from [https://mysql.com/downloads/installer/](https://mysql.com/downloads/installer/).

If you need a GUI you can download and install MySQL Workbench from [https://dev.mysql.com/downloads/workbench/](https://dev.mysql.com/downloads/workbench/).

## Configuration

### Login to MySQL

We'll open a command prompt and issue the following command:

```typescript
mysql -u root -p -h 127.0.0.1
```

### Create the database

```typescript
mysql> CREATE DATABASE mybot;
Query OK, 1 row affected (0.07 sec)
```

### Create the user

```typescript
mysql> GRANT ALL PRIVILEGES ON mybot.* TO 'mybotuser'@'localhost' IDENTIFIED BY 'mybotpassword';
Query OK, 0 rows affected, 2 warnings (0.07 sec)
```

After starting our bot for the first time the table schemas will be created automatically for us so there are no tables to create at this time.

