# package.json

{% code-tabs %}
{% code-tabs-item title="/package.json" %}
```yaml
{
    "name": "discord-bot-typescript-annotationdriven",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "build": "tsc --build tsconfig.json",
        "start": "node dist/index.js",
        "docs": "typedoc --mode file --out docs src/"
    },
    "keywords": [],
    "author": "",
    "license": "ISC",
    "dependencies": {
        "discord.js": "^11.4.2",
        "dotenv": "^6.2.0",
        "mysql": "^2.16.0",
        "reflect-metadata": "^0.1.13",
        "typeorm": "^0.2.13",
        "wikijs": "^4.13.0"
    },
    "devDependencies": {
        "@types/dotenv": "^6.1.0",
        "@types/node": "^11.9.5",
        "typedoc": "^0.14.2",
        "typescript": "^3.3.3333"
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Now that we have our package.json file setup we can tell node to install the dependencies:

```bash
npm install
```



