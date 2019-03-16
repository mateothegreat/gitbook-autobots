# MacroListCommand

{% code-tabs %}
{% code-tabs-item title="/src/Commands/MacroListCommand.ts" %}
```typescript
import { RichEmbed }     from 'discord.js';
import { CommandBase }   from '../Common/CommandBase';
import { Command }       from '../Common/CommandDecorator';
import { CommandParser } from '../Common/CommandParser';
import { Event }         from '../Common/Event';
import { DB }            from '../DB/DB';
import { Macro }         from '../DB/Entities/Macro';

/**
 * Display all saved macros. Usage: ++list
 */
@Command
export class MacroListCommand extends CommandBase {

    public constructor() {

        //
        // Set this commands configuration.
        //
        super({

            event: Event.MESSAGE,
            name: '++list',
            group: 'macros',
            description: 'Display all saved macros. Usage: ++list',
            roles: [ 'admin' ]

        });

    }

    /**
     * Called when a command matches config.name.
     *
     * @param command Parsed out commamd
     *
     */
    public async run(command: CommandParser) {

        const results = await DB.connection.getRepository(Macro)
                                .createQueryBuilder('Macro')
                                .select([ '*' ])
                                .orderBy('name')
                                .getRawMany();

        const embed = new RichEmbed().setTitle('Available Macros');

        for (let i = 0; i < results.length; i++) {

            embed.addField(results[ i ].name, results[ i ].message);

        }

        command.obj.reply(embed);

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

