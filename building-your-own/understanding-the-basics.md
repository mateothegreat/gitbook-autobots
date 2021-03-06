# Understanding the Basics

![](../.gitbook/assets/image%20%282%29.png)

### The Bootstrap

The autobots is a framework built on dynamically loading "modules". On startup the bot class checks for modules in the `node_modules/@autobot` directory that starts with `module-*`.

{% code-tabs %}
{% code-tabs-item title="https://github.com/autobots-rocks/autobot-common/blob/master/src/Common/Bot.ts\#L110" %}
```typescript
...
await glob(`${ currentPath }/node_modules/@autobot/module-*`, (err: any, commands: any) => {

    commands.map((command: any) => {

        Logger.log(`Bootstrapping ${ command }`);

        commands.map((command: CommandBase) => require(command.toString()));

    });
    ...
});
...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### The Module

A module consists of an `index.ts`that exports your command class\(es\) and extends [CommandBase](https://github.com/autobots-rocks/autobot-common/blob/master/src/Common/CommandBase.ts). Each module is required to have a `public run(command: CommandParser)`method which is invoked by the underlying [Bot.ts](https://github.com/autobots-rocks/autobot-common/blob/master/src/Common/Bot.ts) when a command matches your `name` parameter. 

Here is an example of a simple test command which is invoked with you type `>test` in your discord servers channel:

{% code-tabs %}
{% code-tabs-item title="https://github.com/autobots-rocks/autbot-module-test/blob/master/src/index.ts" %}
```typescript
import { Command, CommandBase, CommandParser, Event } from '@autobot/common';
import { RichEmbed }                                  from 'discord.js';

/**
 * Demonstrates a simple command that replies to a test.
 *
 * Example message: `>test`
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
            group: 'testing',
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

        command.obj.reply(new RichEmbed().setTitle('Test received!'));

    }

}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### What's Next

Now that we understand how modules are loaded and what a basic one looks like let's create a more complex module...

