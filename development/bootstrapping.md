# Bootstrapping

{% code-tabs %}
{% code-tabs-item title="/src/index.ts" %}
```typescript
/**
 * Main bootstrap file that instantiates the database connection and Bot class.
 */
import { BOT } from './Common/Bot';
import { DB }  from './DB/DB';

/**
 * Connect to the database.
 */
DB.connect();

/**
 * Starts the bot.
 */
BOT.start();
```
{% endcode-tabs-item %}
{% endcode-tabs %}



