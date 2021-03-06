# The CommandParser Object

The CommandParser Object is passed to every command via it's `public run(command: CommandParser)` method call from the main Bot class's command handler method.

You will use this object to interact with the parsed out command and the underlying `discord.js` `Message` object.

Argument parsing support is built in and is parsed out dynamically not requiring any static configuration. To pass in arguments you can send a message such as  `>mycommand name=mateo,description=taco tuesdays` and your arguments will be available via `command.namedarguments.name` or`command.namedarguments.description`.

### command.command

The `command.command` property is a literal representation of the command issued by the discord message and received by your module.

  `console.log(command);` output snippet:

{% code-tabs %}
{% code-tabs-item title="console.log\(command\);" %}
```bash
CommandParser {
  ...
  command: '>test',
  ...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### command.arguments

The `command.arguments` property is an `array` of [CommandArgument](https://github.com/autobots-rocks/autobot-common/blob/master/src/Common/CommandArgument.ts) Objects that has the `name` and `value` properties available.

  `console.log(command);` output snippet:

{% code-tabs %}
{% code-tabs-item title="console.log\(command\);" %}
```bash
CommandParser {
  arguments: [
    { name: 'name', value: 'mateo' },
    { name: 'description', value: 'taco tuesday' }
  ],
  ...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### command.namedarguments

The `command.namedarguments` is an [CommandArgument](https://github.com/autobots-rocks/autobot-common/blob/master/src/Common/CommandArgument.ts) Objects that has the `name` and `value` properties available., rather than an array \(see above\) of objects. This makes things _easier_ to access. 

  `console.log(command);` output snippet:

{% code-tabs %}
{% code-tabs-item title="console.log\(command\);" %}
```bash
CommandParser {
  ...
  namedarguments: { name: 'mateo', description: 'taco tuesday' },
  ...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### command.obj

The `command.obj` property is the literal `Message` object passed by `discord.js`. You can interact with the message directly with this property such as:

```typescript
command.obj.reply(new RichEmbed().setTitle('Test received!'));
```

  `console.log(command);` output snippet:

{% code-tabs %}
{% code-tabs-item title="console.log\(command\);" %}
```bash
CommandParser {
  ...
  obj: Message {
    channel: TextChannel {
      type: 'text',
      deleted: false,
      id: '581968863663751180',
      name: 'general',
      position: 0,
      parentID: '581968863663751179',
      permissionOverwrites: Collection [Map] {},
      topic: null,
      nsfw: false,
      lastMessageID: '587433698841067531',
      lastPinTimestamp: null,
      rateLimitPerUser: 0,
      guild: [Guild],
      messages: [Collection [Map]],
      _typing: Map {}
    },
    deleted: false,
    id: '587433698841067531',
    type: 'DEFAULT',
    content: '>test name=mateo,description=taco tuesday',
    author: User {
      id: '505520869246763009',
      username: 'mateothegreat',
      discriminator: '0001',
      avatar: 'e4d574d22fcc131bd6a31576b27403b8',
      bot: false,
      lastMessageID: '587433698841067531',
      lastMessage: [Circular]
    },
    member: GuildMember {
      guild: [Guild],
      user: [User],
      joinedTimestamp: 1558822589627,
      _roles: [Array],
      serverDeaf: false,
      serverMute: false,
      selfMute: undefined,
      selfDeaf: undefined,
      voiceSessionID: undefined,
      voiceChannelID: undefined,
      speaking: false,
      nickname: null,
      lastMessageID: '587433698841067531',
      lastMessage: [Circular],
      deleted: false
    },
    pinned: false,
    tts: false,
    nonce: '587433698513649664',
    system: false,
    embeds: [],
    attachments: Collection [Map] {},
    createdTimestamp: 1560125507794,
    editedTimestamp: null,
    reactions: Collection [Map] {},
    mentions: MessageMentions {
      everyone: false,
      users: Collection [Map] {},
      roles: Collection [Map] {},
      _content: '>test name=mateo,description=taco tuesday',
      _client: [Client],
      _guild: [Guild],
      _members: null,
      _channels: null
    },
    webhookID: null,
    hit: null,
    _edits: []
  }
}b
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### getArgumentByName\(commandName: string\): CommandArgument

This is a helper function that retrieves an argument by it's name directly and is rarely used.

