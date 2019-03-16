---
description: 'Bans a user from the server. Usage: >ban name=someusername'
---

# UserBanCommand

{% code-tabs %}
{% code-tabs-item title="/src/Commands/UserBanCommand.ts" %}
```typescript
import { RichEmbed, User } from 'discord.js';
import { BOT }             from '../Common/Bot';
import { CommandBase }     from '../Common/CommandBase';
import { Command }         from '../Common/CommandDecorator';
import { CommandParser }   from '../Common/CommandParser';
import { Event }           from '../Common/Event';

/**
 * Bans a user from the server. Usage: >ban name=someusername
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
            name: '>ban',
            description: 'Bans a user from the server. Usage: >ban name=someusername',
            roles: [ 'admin' ],
            params: [ {

                name: 'name',
                description: 'Users name.',
                required: true,

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

        const user = BOT.client.users.find((user: User) => user.username === command.arguments[ 0 ].value);

        if (user) {

            BOT.client.guilds.first().ban(user);

            command.obj.reply(new RichEmbed().setTitle(`Server Ban`)
                                             .setDescription(`The user with username "${ command.arguments[ 0 ].value }" has been banned.`));

        } else {

            command.obj.reply(new RichEmbed().setTitle(`Server Ban`)
                                             .setDescription(`Could not find a user with the username "${ command.arguments[ 0 ].value }"`));

        }

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

