# Publishing your node module

You can publish your module with a simple `npm publish --scope=public`.Before we do this we'll want to make sure that we've built our project with `tsc` which will output to the `dist/` directory and will be picked up by `npm publish`.

## package.json configuration

{% code-tabs %}
{% code-tabs-item title="/package.json" %}
```javascript
{
    "name": "<your username>/testbot-module-test",
    "version": "1.0.180",
    "description": "my first testbot module",
    "main": "dist/index",
    "typings": "dist/index",
    "scripts": {
        "build": "npx tsc",
        "bump": "tsc && npm version patch && npm publish"
    },
    "access": "public",
    "keywords": [],
    "author": "",
    "license": "ISC",
    "dependencies": {
        "@autobot/common": "^1.1.23",
        "discord.js": "^11.4.2"
    },
    "devDependencies": {
        "@types/dotenv": "^6.1.0",
        "@types/node": "^11.11.4"
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

