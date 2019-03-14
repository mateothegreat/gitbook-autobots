# Common Classes

### CommandBase Class

This class will be the "base" class that all commands inherit from mapping a few things like command configuration and a run method that we will later override in our own command classes.

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandBase.ts" %}
```typescript
import { CommandConfig } from './CommandConfig';
import { CommandParser } from './CommandParser';

export class CommandBase {

    public config: any;


    public constructor(config: CommandConfig) {

        this.config = config;

    }

    public run(command: CommandParser): void { }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### CommandConfig Class

This class will be used to map configuration details. For now, we'll only specify a name property which will be used to map a parsed command string to a specific `Command` class.

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandConfig.ts" %}
```typescript
export class CommandConfig {

    public name: string;

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### CommandDecorator Class

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandDecorator.ts" %}
```typescript
import { BOT } from './Bot';


// @Command Class Annotation
export function Command(target: any): any {

    // Register the class annotated with @Command
    BOT.register(new target());

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandParser.ts" %}
```typescript
import { Message } from 'discord.js';

export class CommandParser {

    public command: string;
    public arguments: string;
    public message: Message;

    public constructor(message: Message) {

        const matches = message.content.match(/>\s?(\w+)\s+(.*)/);

        if (!!matches && matches.length === 3) {

            this.command = matches[ 1 ];
            this.arguments = matches[ 2 ];
            this.message = message;
            
        }


    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

