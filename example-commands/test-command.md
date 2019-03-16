---
description: Let's create our first test command!
---

# TestCommand

Commands are made of of a class that extends the `CommandBase` class and has the `@Command` annotation.

All command classes have to implement a `run(command: CommandParser)` method which is called by the `Bot` class as messages are received.

### Your First Command

{% code-tabs %}
{% code-tabs-item title="/src/Commands/TestCommand.ts" %}
```typescript
import { RichEmbed }     from 'discord.js';
import { CommandBase }   from '../Common/CommandBase';
import { Command }       from '../Common/CommandDecorator';
import { CommandParser } from '../Common/CommandParser';
import { Event }         from '../Common/Event';

/**
 * Demonstrates a simple command that uses arguments.
 *
 * Example message: `>test chars=abc,num=123,opt=hellow world`
 */
@Command
export class TestCommand extends CommandBase {

    public constructor() {

        //
        // Set this commands configuration.
        //
        super({

            event: Event.MESSAGE,
            name: '>test',
            description: 'Simple test command that sends a reply if validation succeeds.',
            params: [ {

                name: 'chars',
                description: 'An argument containing a word.',
                required: true,
                pattern: '[a-zA-Z]+'

            }, {

                name: 'num',
                description: 'An argument containing numbers.',
                required: true,
                pattern: '\\d+'

            }, {

                name: 'opt',
                description: 'An optional argument.',
                required: false,

            } ]

        });

    }

    /**
     * Called when a command matches config.name.
     *
     * @param command Parsed out commamd
     *
     */
    public run(command: CommandParser): void {

        command.obj.reply(new RichEmbed().setTitle('Test received!')
                                         .setDescription(`argument 1: ${ command.arguments[ 0 ].name }=${ command.arguments[ 0 ].value }\nargument 2: ${ command.arguments[ 1 ].name }=${ command.arguments[ 1 ].value }`));

    }

}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

By setting the "name" property of the configuration object, passed via the constructors `super(..)` call the `Bot` class knows how to map messages starting with it's value and will then execute the `run(..)` method while passing a `CommandParser` object.

