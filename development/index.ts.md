# index.ts

We'll setup an `index.ts` file which will handle all of our exported commands that will be used to load things later.

{% code-tabs %}
{% code-tabs-item title="/src/Commands/index.ts" %}
```typescript
export * from './AllMessagesCommand';
export * from './TestCommand';
```
{% endcode-tabs-item %}
{% endcode-tabs %}



