---
description: The Barrel File
---

# index.ts

We'll setup an `index.ts` file which will handle all of our exported commands that will be used to load things later.

{% hint style="info" %}
For new commands you will want to add them to `index.ts`!
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="/src/Commands/index.ts" %}
```typescript
/**
 * Barrel file for commands.
 */
export * from './ChannelSetTopicCommand';
export * from './FlipCommand';
export * from './GuildMemberAddMessageCommand';
export * from './HelpCommand';
export * from './LogMessagesCommand';
export * from './PingCommand';
export * from './TestCommand';
export * from './UserBanCommand';
export * from './UserUnBanCommand';
export * from './WikipediaSearchCommand';
```
{% endcode-tabs-item %}
{% endcode-tabs %}



