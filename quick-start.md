---
description: 'The quick start, TLDR.'
---

# Quick Start

This book comes with a complimentary repository. Clone it and run if you want the TLDR!

### Clone & npm install

```bash
git clone https://github.com/mateothegreat/discord-bot-typescript-annotationdriven
cd discord-bot-typescript-annotationdriven
npm install
```

### Configure .env

Copy the `.env.sample` file to .env and replace the defaults with your own. Though this repo comes with `.env`added to `.gitignore` be careful and do not commit this file to git!

### Starting the bot

```bash
npm run build
npm start
```

Example output:

```bash
Command Registerd: *
Command Registerd: >test
Command Registerd: !ping
Bot Started
query: START TRANSACTION
query: SELECT DATABASE() AS `db_name`
query: SELECT * FROM `INFORMATION_SCHEMA`.`TABLES` WHERE (`TABLE_SCHEMA` = 'mybot' AND `TABLE_NAME` = 'user') OR (`TABLE_SCHEMA` = 'mybot' AND `TABLE_NAME` = 'chat_message')
query: SELECT * FROM `INFORMATION_SCHEMA`.`COLUMNS` WHERE (`TABLE_SCHEMA` = 'mybot' AND `TABLE_NAME` = 'user') OR (`TABLE_SCHEMA` = 'mybot' AND `TABLE_NAME` = 'chat_message')
query: SELECT * FROM `INFORMATION_SCHEMA`.`KEY_COLUMN_USAGE` WHERE `CONSTRAINT_NAME` = 'PRIMARY' AND ((`TABLE_SCHEMA` = 'mybot' AND `TABLE_NAME` = 'user') OR (`TABLE_SCHEMA` = 'mybot' AND `TABLE_NAME` = 'chat_message'))
query: SELECT `SCHEMA_NAME`, `DEFAULT_CHARACTER_SET_NAME` as `CHARSET`, `DEFAULT_COLLATION_NAME` AS `COLLATION` FROM `INFORMATION_SCHEMA`.`SCHEMATA`
query: SELECT `s`.* FROM `INFORMATION_SCHEMA`.`STATISTICS` `s` LEFT JOIN `INFORMATION_SCHEMA`.`REFERENTIAL_CONSTRAINTS` `rc` ON `s`.`INDEX_NAME` = `rc`.`CONSTRAINT_NAME` WHERE ((`s`.`TABLE_SCHEMA` = 'mybot' AND `s`.`TABLE_NAME` = 'user') OR (`s`.`TABLE_SCHEMA` = 'mybot' AND `s`.`TABLE_NAME` = 'chat_message')) AND `s`.`INDEX_NAME` != 'PRIMARY' AND `rc`.`CONSTRAINT_NAME` IS NULL
query: SELECT `kcu`.`TABLE_SCHEMA`, `kcu`.`TABLE_NAME`, `kcu`.`CONSTRAINT_NAME`, `kcu`.`COLUMN_NAME`, `kcu`.`REFERENCED_TABLE_SCHEMA`, `kcu`.`REFERENCED_TABLE_NAME`, `kcu`.`REFERENCED_COLUMN_NAME`, `rc`.`DELETE_RULE` `ON_DELETE`, `rc`.`UPDATE_RULE` `ON_UPDATE` FROM `INFORMATION_SCHEMA`.`KEY_COLUMN_USAGE` `kcu` INNER JOIN `INFORMATION_SCHEMA`.`REFERENTIAL_CONSTRAINTS` `rc` ON `rc`.`constraint_name` = `kcu`.`constraint_name` WHERE (`kcu`.`TABLE_SCHEMA` = 'mybot' AND `kcu`.`TABLE_NAME` = 'user') OR (`kcu`.`TABLE_SCHEMA` = 'mybot' AND `kcu`.`TABLE_NAME` = 'chat_message')
query: COMMIT
Connected to database
```

