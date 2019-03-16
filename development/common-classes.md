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

### CommandParam Class

This class configures each parameter that a command expects.

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandParam.ts" %}
```typescript
/*
 * Parameter type class that commands configure themselves with.
 */
export class CommandParam {

    /**
     * Name of the command, i.e.: !ping or >hellow
     */
    public name: string;

    /**
     * Command description -- used with the help command and during validation error(s) (optional).
     */
    public description?: string;

    /**
     * Determine if this parameter is required (optional).
     */
    public required?: boolean;

    /**
     * Regular expression pattern for validating this parameter (optional).
     */
    public pattern?: string;

    /**
     * Initial default value (optional).
     */
    public value?: string;

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### CommandConfig Class

This class will be used to map configuration details. For now, we'll only specify a name property which will be used to map a parsed command string to a specific `Command` class.

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandConfig.ts" %}
```typescript
import { CommandParam } from './CommandParam';
import { Event }        from './Event';

export class CommandConfig {

    public event: Event;
    public name?: string;
    public description?: string;
    public params?: CommandParam[];
    public roles?: string[];

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### CommandDecorator Class

This class will allow us to "decorate" or "annotate" our Command classes with `@Command`. Classes decorated with this annotation will automatically be loaded and it's configuration analyzed in preparation of receiving messages.

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

### CommandParser Class

This class will automatically parse out the command name and argument\(s\) providing a ready means to each. This class will get passed to all Command `run(..)` method calls.

{% code-tabs %}
{% code-tabs-item title="/src/Common/CommandParser.ts" %}
```typescript
import { GuildMember, Message } from 'discord.js';
import { CommandArgument }      from './CommandArgument';

export type MESSAGE_TYPE = Message & GuildMember;

/**
 * Takes in a obj and parses it out into a Command Class Instance.
 */
export class CommandParser {

    /**
     * Name of the command parsed out.
     */
    public command: string;

    /**
     * Arguments parsed out between commas.
     */
    public arguments: CommandArgument[] = [];

    /**
     * Discord.js Message Object.
     */
    public obj: MESSAGE_TYPE;

    /**
     * @description Class Constructor requiring a Discord.js Message Object.
     *
     * @param obj Discord.js object.
     *
     */
    public constructor(obj: MESSAGE_TYPE) {

        //
        // Match between spaces or to the end if no spaces found.
        // i.e.: `!ping` or `>test chars=abc,num=123
        //
        const matches = obj.content.match(/^(.*?)(?:\s+|$)(.*)/);

        if (!!matches && matches.length === 3) {

            this.command = matches[ 1 ];

            const split = matches[ 2 ].split(',');

            for (let i = 0; i < split.length; i++) {

                const splitRow = split[ i ].split('=');

                this.arguments.push({

                    name: splitRow[ 0 ],
                    value: splitRow[ 1 ]

                });

            }

        }

        this.obj = obj;

    }

    /**
     * @description Retrives a parsed argument by it's name.
     *
     * @param commandName Name of the argument (name=somecommand).
     *
     * @returns CommandArgument CommandArgument or null if not found.
     *
     */
    public getArgumentByName(commandName: string): CommandArgument {

        for (let i = 0; i < this.arguments.length; i++) {

            if (this.arguments[ i ].name === commandName) {

                return this.arguments[ i ];

            }

        }

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

