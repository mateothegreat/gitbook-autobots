# KarmaPointCommand

Let's create the file `/src/Commands/KarmaPointCommand.ts` with the following content:

{% hint style="info" %}
Once created, be sure to add it to the `/src/Commands/index.ts` barrel file!
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="/src/Commands/KarmaPointCommand.ts" %}
```typescript
import { RichEmbed, User } from "discord.js";
import { BOT }             from '../Common/Bot';
import { CommandBase }     from '../Common/CommandBase';
import { Command }         from '../Common/CommandDecorator';
import { CommandParser }   from '../Common/CommandParser';
import { Event }           from '../Common/Event';
import { DB }              from '../DB/DB';
import { KarmaPoint }      from '../DB/Entities/KarmaPoint';

/**
 * Searches each message for thank you or thanks.
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
            name: '*',
            group: 'events',
            description: 'Searches each message for thank you or thanks.'

        });

    }

    //
    // Called when a command matches config.name.
    //
    public run(command: CommandParser): void {

        //
        // First we try to detect for thank you and thanks.
        //
        const matches = command.obj.content.match(/(thanks|thank you)/i);

        if (matches && matches.length > 0) {

            //
            // Now we extract the user id(s).
            //
            const userids = command.obj.content.match(/([\d]{18,})/g);

            if (userids) {

                //
                // Since there can be more than one user mentioned we will loop.
                //
                for (let i = 0; i < userids.length; i++) {

                    BOT.client.fetchUser(userids[ i ]).then((member: User) => {

                        //
                        // Prevent users from giving karma to themselves.
                        //
                        if (command.obj.member.id === member.id) {

                            // @ts-ignore
                            BOT.client.guilds.first().channels.get(command.obj.channel.id).send(`Sorry <@${ command.obj.author.id }>, you can't give karma to yourself. :sob:`);

                        } else {

                            let karmaPoint: KarmaPoint = new KarmaPoint();

                            karmaPoint.from_userid = command.obj.author.id;
                            karmaPoint.from_discriminator = command.obj.author.discriminator;
                            karmaPoint.from_username = command.obj.author.username;

                            karmaPoint.to_userid = member.id;
                            karmaPoint.to_discriminator = member.discriminator;
                            karmaPoint.to_username = member.username;

                            DB.connection.manager.save(karmaPoint);

                            const embed = new RichEmbed().setTitle(`Learn more about Karma Points..`)
                                                         .setDescription(`Congratulations <@${ member.id }>, you've received a Karma Point!`)
                                                         .setAuthor(`Karma From ${ command.obj.author.username }`)
                                                         .setColor(0x00AE86)
                                                         .setURL("https://forum.bitmerge.org/t/server-karma-points");

                            // @ts-ignore
                            BOT.client.guilds.first().channels.get(command.obj.channel.id).send({ embed });

                        }

                    });

                }

            }

        }

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

