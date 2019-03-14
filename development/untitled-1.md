---
description: Let's create our first test command!
---

# Test Command

Commands are made of of a class that extends the `CommandBase` class and has the `@Command` annotation.

All command classes have to implement a `run(command: CommandParser)` method which is called by the `Bot` class as messages are received.

### Your First Command

{% code-tabs %}
{% code-tabs-item title="/src/Commands/TestCommand.ts" %}
```typescript
import { CommandBase }   from '../Common/CommandBase';
import { Command }       from '../Common/CommandDecorator';
import { CommandParser } from '../Common/CommandParser';

@Command
export class TestCommand extends CommandBase {

    public constructor() {

        // Set this commands configuration.
        super({ name: 'test' });
        
    }

    // Called when a command matches config.name.
    public run(command: CommandParser): void {

        command.message.reply('Test received!');

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

By setting the "name" property of the configuration object, passed via the constructors `super(..)` call the `Bot` class knows how to map messages starting with it's value and will then execute the `run(..)` method while passing a `CommandParser` object.

