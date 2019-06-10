---
description: .env configuration
---

# Creating your own Bot

## Development Environment

Getting ready to create your own command modules requires a short bit of setup. We need to initialize our node package, install a few packages and create a `src/` directory as follows.

{% code-tabs %}
{% code-tabs-item title="Directory Structure" %}
```typescript
Matthews-MacBook-Pro-178 in ~/workspace/work/autobots/autobot-docsbot
± |master U:1 ✗| → ls -la

-rw-r--r--    1 yomateod  staff       314 Jun  4 22:05 .env
drwxr-xr-x   15 yomateod  staff       480 Jun  9 19:58 .git
-rw-r--r--    1 yomateod  staff        36 Jun  2 16:04 .gitignore
drwxr-xr-x    9 yomateod  staff       288 Jun  2 13:53 dist
drwxr-xr-x  289 yomateod  staff      9248 Jun  8 18:12 node_modules
-rw-r--r--    1 yomateod  staff     99150 Jun  8 18:12 package-lock.json
-rw-r--r--    1 yomateod  staff       681 Jun  8 18:12 package.json
drwxr-xr-x    5 yomateod  staff       160 Jun  2 13:40 src
-rw-r--r--    1 yomateod  staff       343 May 27 08:23 tsconfig.json

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Setting up your node module

First we need to create a new directory and initialize our node package:

```text
npm init
npm install -D typescript
npm install @autobot/common discord.js
```

### Configuration

The autobots framework relies on environment variables for configuration. We use the `dotenv` module to load the `.env` configuration file in the project root at boot time.

The required variables are:

| Variable Name | Description |
| :--- | :--- |
| `TOKEN` | Discord bot token. |
| `NAMESPACE` | The directory which you will publish your node modules under. |
| `MODULE_PATTERN` | The pattern to look for node modules directory names. |

Here is an example of a `.env` file with some custom variables for our testbot that we'll read in later:

{% code-tabs %}
{% code-tabs-item title="/.env" %}
```bash
# *** DO NOT CHECK THE .env FILE INTO GIT! ***

#
# Your discord token. (required)
#
TOKEN=<your discord bot token>

#
# The directory in node_modules to look for modules. (required)
#
NAMESPACE=@autobot

#
# The pattern to use for including modules. (required)
#
MODULE_PATTERN=module-*

#
# Port for the web server to run on. (optional)
#
PORT=8080

#####################################################################
#
# Individual module configurations.
#
#####################################################################

#
# Your own testbot environment variables.
#
TESTBOT_BOTNAME=tester mctest
TESTBOT_TEST_PREFIX=>test
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Create this file in your project root directory and name it `.env`.

### tsconfig.json

We need to tell the typescript command `tsc` how to compile our project. Create the following file in your project root and name it `tsconfig.json`:

```typescript
{
    "compilerOptions": {
        "target": "es6",
        "module": "commonjs",
        "lib": [
            "es5",
            "es6"
        ],
        "sourceMap": true,
        "outDir": "dist",
        "rootDir": "src",
        "noImplicitAny": true,
        "moduleResolution": "node",
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true,
        "declaration": true
    },
    "include": [
        "src/**/*"
    ]
}
```

### Creating our Command Module



