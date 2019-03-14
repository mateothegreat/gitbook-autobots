# TypeORM Configuration

{% code-tabs %}
{% code-tabs-item title="/src/DB/DB.ts" %}
```typescript
import { Connection, createConnection } from 'typeorm';

export class DB {

    public connection: Connection;

    public async connect() {

        try {

            this.connection = await createConnection({

                type: "mysql",
                host: process.env.MYSQL_HOST,
                port: 3306,
                username: process.env.MYSQL_USER,
                password: process.env.MYSQL_PASSWORD,
                database: process.env.MYSQL_DATABASE,
                entities: [ './entities' ],
                synchronize: true,
                logging: true

            });

        } catch (e) {

            console.log(e);

        }

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

