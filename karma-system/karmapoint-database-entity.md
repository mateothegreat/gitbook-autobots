# KarmaPoint Database Entity

Let's create a new file under `/src/DB/Entities` and call it `KarmaPoint.ts`with the following content:

{% code-tabs %}
{% code-tabs-item title="/src/DB/Entities/KarmaPoint.ts" %}
```typescript
import { Column, CreateDateColumn, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity()
export class KarmaPoint {

    @PrimaryGeneratedColumn()
    id: number;

    @Column()
    from_userid: string;

    @Column()
    from_discriminator: string;

    @Column()
    from_username: string;

    @Column()
    to_userid: string;

    @Column()
    to_discriminator: string;

    @Column()
    to_username: string;

    @CreateDateColumn()
    createdDate: Date;

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now that we've created our entity we need to update the `DB` class so that it registers it \(see line 29:

{% code-tabs %}
{% code-tabs-item title="/src/DB/DB.ts" %}
```typescript
import { Connection, createConnection } from 'typeorm';
import { Logger }                       from '../Common/Logger';
import { ChatMessage }                  from './Entities/ChatMessage';
import { KarmaPoint }                   from './Entities/KarmaPoint';
import { User }                         from './Entities/User';

export class DB {

    public static connection: Connection;

    public static async connect() {

        try {

            console.log(__dirname);

            this.connection = await createConnection({

                type: "mysql",
                host: process.env.MYSQL_HOST,
                port: Number(process.env.MYSQL_PORT),
                username: process.env.MYSQL_USER,
                password: process.env.MYSQL_PASSWORD,
                database: process.env.MYSQL_DATABASE,
                entities: [

                    User,
                    ChatMessage,
                    KarmaPoint

                ],
                synchronize: true,
                logging: true

            });

            Logger.log('Connected to database');

        } catch (e) {

            console.log(e);

        }

    }

}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

Once we restart our bot the new database table will be automatically created for us.

