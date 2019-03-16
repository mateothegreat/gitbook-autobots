---
description: >-
  Replies back to the user with a random selection between "|". Usage: >flip
  heads|tails|whoknows
---

# FlipCommand

{% code-tabs %}
{% code-tabs-item title="/src/Commands/FlipCommand.ts" %}
```typescript
import { CommandBase }   from '../Common/CommandBase';
import { Command }       from '../Common/CommandDecorator';
import { CommandParser } from '../Common/CommandParser';
import { Event }         from '../Common/Event';

/**
 * Replies back to the user with a random selection between "|". Usage: >flip heads|tails|whoknows
 */
@Command
export class 
 extends CommandBase {

    public constructor() {

        //
        // Set this commands configuration.
        //
        super({

            event: Event.MESSAGE,
            name: '!flip',
            description: 'Replies back to the user with a random selection between "|". Usage: >flip heads|tails|whoknows',

        });

    }

    /**
     * Called when a command matches config.name.
     *
     * @param command Parsed out commamd
     *
     */
    public run(command: CommandParser): void {

        const split = command.arguments[ 0 ].name.split('|');

        command.obj.reply(split[ Math.floor(Math.random() * split.length) ]);

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

