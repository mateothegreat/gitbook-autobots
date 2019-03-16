---
description: Sends a reply with the message "pong" when a user types "!ping".
---

# PingCommand

{% code-tabs %}
{% code-tabs-item title="/src/Commands/PingCommand.ts" %}
```typescript
import { CommandBase }   from '../Common/CommandBase';
import { Command }       from '../Common/CommandDecorator';
import { CommandParser } from '../Common/CommandParser';
import { Event }         from '../Common/Event';

/**
 * Replies back to the user with "pong!"
 */
@Command
export class PingCommand extends CommandBase {

    public constructor() {

        //
        // Set this commands configuration.
        //
        super({

            event: Event.MESSAGE,
            name: '!ping',
            description: 'Simple test command that sends a reply.',

        });

    }

    /**
     * Called when a command matches config.name.
     *
     * @param command Parsed out commamd
     *
     */
    public run(command: CommandParser): void {

        command.obj.reply('pong!');

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

