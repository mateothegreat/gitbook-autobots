---
description: Declare our database objects by defining them with classes.
---

# Declare Objects

## Setup

{% code-tabs %}
{% code-tabs-item title=".env" %}
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
{% code-tabs-item title="User.ts" %}
```typescript
import { Column, CreateDateColumn, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class User {

    @PrimaryGeneratedColumn()
    id: number;

    @CreateDateColumn()
    createdDate: Date;

    @Column()
    discordUserId: string;

    @Column()
    discordUsername: string;

    @Column()
    discrodDiscriminator: string;

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### ChatMessage Object

Each time a message is received we will log it to the database so we can later perform queries like tracking the number of messages a user has sent for experience points.

{% code-tabs %}
{% code-tabs-item title="ChatMessage.ts" %}
```typescript
import { Column, CreateDateColumn, Entity, PrimaryGeneratedColumn } from 'typeorm';
import { User }                                                     from './User';

@Entity()
export class ChatMessage {

    @PrimaryGeneratedColumn()
    id: number;

    @Column()
    user: User;

    @Column({ type: "blob" })
    content: string;

    @Column()
    channel: string;

}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

