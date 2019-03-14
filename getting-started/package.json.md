# package.json

{% code-tabs %}
{% code-tabs-item title="package.json" %}
```yaml
{
    "name": "@ngxui/discord-bot-typescript-autobot",
    "version": "1.0.0",
    "main": "index.js",
    "scripts": {
        "build": "tsc",
        "start": "node dist/index.js"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "dependencies": {
        "@types/common-tags": "^1.8.0",
        "@types/sequelize": "^4.27.37",
        "columnify": "^1.5.4",
        "common-tags": "^1.8.0",
        "discord.js": "^11.4.2",
        "discord.js-commando": "^0.10.0",
        "dotenv": "^6.2.0",
        "mysql": "^2.16.0",
        "reflect-metadata": "^0.1.13",
        "typeorm": "^0.2.13"
    },
    "devDependencies": {
        "@types/dotenv": "^6.1.0",
        "@types/node": "^11.9.5",
        "typescript": "^3.3.3333"
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now that we have our package.json file setup we can tell node to install the dependencies:

```text
$ npm install
```



