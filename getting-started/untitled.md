---
description: We'll use MySQL as our database engine and configure it.
---

# Database Setup

## Installation

Download and install MySQL from [https://mysql.com/downloads/installer/](https://mysql.com/downloads/installer/).

Download and install MySQL Workbench from [https://dev.mysql.com/downloads/workbench/](https://dev.mysql.com/downloads/workbench/).

## Configuration

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

