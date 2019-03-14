---
description: Declare our database objects by defining them with classes.
---

# Declare Database Entities

## Setup

### Installation

We will use the node.js module [TypeORM](https://typeorm.io) which will provide us with schema and query management.

```text
npm install typeorm
```

### Environment Variables

We will store our database configuration properties in a `.env` file which will later allow us to access these values using node's `process.env` object

Create a file named `.env` with the following \(updating the values from our previous step\):

{% code-tabs %}
{% code-tabs-item title="/.env" %}
```typescript
TOKEN=<your discord bot token>
OWNER_ID=<your discord user id>
MYSQL_HOST=<mysql hostname>
MYSQL_USER=<mysql username>
MYSQL_PASSWORD=<mysql password>
MYSQL_DATABASE=<mysql database>

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Declaring Objects

### User Object

We need the ability to store users in our database which we can then reference when things happen like recording chat messages, points, etc..

{% code-tabs %}
{% code-tabs-item title="/src/DB/entities/User.ts" %}
```typescript
import { Column, CreateDateColumn, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class User {

    @PrimaryGeneratedColumn()
    public id: number;

    @CreateDateColumn()
    public createdDate: Date;

    @Column()
    public discordUserId: string;

    @Column()
    public discordUsername: string;

    @Column()
    public discrodDiscriminator: string;

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### ChatMessage Object

Each time a message is received we will log it to the database so we can later perform queries like tracking the number of messages a user has sent for experience points.

{% code-tabs %}
{% code-tabs-item title="/src/DB/entities/ChatMessage.ts" %}
```typescript
import { Column, CreateDateColumn, Entity, PrimaryGeneratedColumn } from 'typeorm';
import { User }                                                     from './User';

@Entity()
export class ChatMessage {

    @PrimaryGeneratedColumn()
    public id: number;

    @Column()
    public user: User;

    @Column({ type: "blob" })
    public content: string;

    @Column()
    public channel: string;

}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

