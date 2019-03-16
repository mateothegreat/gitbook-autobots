# Bot Class

This is the meat and potatoes of things, the main Bot Class.

{% code-tabs %}
{% code-tabs-item title="/src/Common/Bot.ts" %}
```typescript
import * as Discord                    from 'discord.js';
import { GuildMember, RichEmbed }      from 'discord.js';
import * as dotenv                     from 'dotenv';
import { CommandBase }                 from './CommandBase';
import { CommandParser, MESSAGE_TYPE } from './CommandParser';
import { Event }                       from './Event';
import { EVENT_OBJECT }                from './EventObjectType';
import { Logger }                      from './Logger';

//
// Load .env into process.env
//
dotenv.config();


class Bot {

    /**
     * Discord.js Client
     */
    public client: any = new Discord.Client();

    /**
     * Array of Command Class References
     */
    public commands: Array<CommandBase> = [];

    /**
     * Called by the @Command decorated classes
     *
     * @param commandRef Command class reference.
     */
    public register(commandRef: CommandBase): void {

        this.commands.push(commandRef);

        Logger.log(`Command Registerd: ${ commandRef.config.name } (${ commandRef.config.description })`);

    }

    /**
     * Start the bot.
     */
    public start(): void {

        //
        // Bind discord.js events
        //
        this.client.on('message', (message: MESSAGE_TYPE) => this.handleMessage(Event.MESSAGE, message));
        this.client.on('guildMemberAdd', (guildMember: GuildMember) => this.handleEvent(Event.GUILD_MEMBER_ADD, guildMember));

        this.client.login(process.env.TOKEN);

        //
        // Load Command Classes
        //
        require('../Commands');

        Logger.log('Bot Started');

    }

    /**
     * Handle an incoming event.
     *
     * @param event Event type.
     * @param eventobject Event Object from discord.js.
     */
    public handleEvent(event: Event, eventobject: EVENT_OBJECT): void {

        this.runEvent(event, eventobject);

    }

    /*
     * Handle an incoming message.
     *
     * @param event Event type.
     * @param Message Discord message obj.
     *
     */
    public handleMessage(event: Event, message: MESSAGE_TYPE): void {

        //
        // Prevent the bot from talking to itself (this would cause an endless loop).
        //
        if (!message.author.bot) {

            const command = new CommandParser(message);

            //
            // Run the preCommand validation checks before executing runCommand.
            //
            if (this.preCommand(event, command)) {

                this.runCommand(event, command);

            }

        }

    }

    /*
     * Perform validation checks.
     *
     * @param CommandParser commandParser The parsed command.
     *
     */
    public preCommand(event: Event, parsedCommand: CommandParser): boolean {

        const command: CommandBase = this.getCommandByName(parsedCommand.command);

        if (command) {

            let errors: string[] = [];

            //
            // Roles Validation
            //
            if (command.config.roles) {

                let roleMatched = false;

                for (let i = 0; i < command.config.roles.length; i++) {

                    if (parsedCommand.obj.member.roles.find(role => role.name === command.config.roles[ i ])) {

                        roleMatched = true;

                        break;

                    }

                }

                if (!roleMatched) {

                    errors.push('You do not have the required role to run this command.');

                }

            }

            //
            // Parameter Validation
            //
            if (command.config.params) {

                for (let i = 0; i < command.config.params.length; i++) {

                    const argument = parsedCommand.getArgumentByName(command.config.params[ i ].name);

                    if (command.config.params[ i ].required && !argument) {

                        errors.push(`The parameter "${ command.config.params[ i ].name }" (${ command.config.params[ i ].description }) is required.`);

                    } else {

                        //
                        // Check to see if the argument passed exists in the commands accetpable parameters.
                        //
                        if (argument) {

                            const regex = new RegExp(command.config.params[ i ].pattern);

                            if (!argument.value.match(regex)) {

                                errors.push(`The parameter "${ command.config.params[ i ].name }" with the value "${ argument.value }" is invalid (Acceptable pattern: ${ command.config.params[ i ].pattern }).`);

                            }

                        }

                    }

                }

            }

            //
            // Send the error messages back to the user.
            //
            if (errors.length > 0) {

                parsedCommand.obj.reply(new RichEmbed().setTitle('The following errors ocurred:')
                                                       .setDescription(errors.join("\n\t")));

                return false;

            } else {

                return true;

            }

        }

        //
        // Return true by default which means the command did not have any validations.
        //
        return true;

    }

    /*
     * Run a command
     *
     * @param string commandName Name of the command to run.
     *
     */
    public runCommand(event: Event, command: CommandParser): void {

        for (let i = 0; i < this.commands.length; i++) {

            if (this.commands[ i ].config.event === event && this.commands[ i ].config.name === command.command || this.commands[ i ].config.name === '*') {

                console.log(`Running Command: ${ this.commands[ i ].config.name }`);

                this.commands[ i ].run(command);

            }

        }

    }

    /**
     * Run a command based on an event.
     *
     * @param event Event type.
     * @param eventobject Event object.
     */
    public runEvent(event: Event, eventobject: EVENT_OBJECT): void {

        const command = this.getCommandByEvent(event);

        if (command) {

            command.run(eventobject);

        }

    }

    /**
     * Retrieves a registered command by it's name.
     *
     * @param name Name of the command.
     */
    public getCommandByName(name: string): CommandBase {

        for (let i = 0; i < this.commands.length; i++) {

            if (this.commands[ i ].config.name === name) {

                return this.commands[ i ];

            }

        }

    }

    /**
     * Retrieves a registered command by it's event type.
     */
    public getCommandByEvent(event: Event): CommandBase {

        for (let i = 0; i < this.commands.length; i++) {

            if (this.commands[ i ].config.event === event) {

                return this.commands[ i ];

            }

        }

    }

}

export const BOT = new Bot();
```
{% endcode-tabs-item %}
{% endcode-tabs %}

