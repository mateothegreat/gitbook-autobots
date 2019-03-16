---
description: Send a message to a channel when a member is added to the guild.
---

# GuildMemberAddMessageCommand

{% code-tabs %}
{% code-tabs-item title="/src/Commands/GuildMemberAddMessageCommand.ts" %}
```typescript

import { Channel, GuildMember, RichEmbed } from 'discord.js';
import { CommandBase }                     from '../Common/CommandBase';
import { Command }                         from '../Common/CommandDecorator';
import { Event }                           from '../Common/Event';

/**
 * Sends a message to the channel when a user joins the guild.
 */
@Command
export class GuildMemberAddMessageCommand extends CommandBase {

    public constructor() {

        //
        // Set this commands configuration.
        //
        super({

            event: Event.GUILD_MEMBER_ADD,
            description: 'Sends a obj when a new user is added to the guild.',

        });

    }

    /**
     * Called when a command matches config.name.
     *
     * @param event Event object.
     *
     */
    public run(event: GuildMember): void {

        const channel: Channel = event.guild.channels.find(channel => channel.name === "general");

        if (channel) {

            // @ts-ignore
            channel.send(new RichEmbed().setTitle('Welcome New User!')
                                        .setDescription(`Glad you could join us <@${ event.user.id }>!`));

        }

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

