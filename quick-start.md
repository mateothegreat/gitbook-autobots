---
description: 'The quick start, TLDR.'
---

# Quick Start

This book comes with a complimentary repository. Clone it and run if you want the TLDR!

### Clone & npm install

```bash
git clone https://github.com/autobots-rocks/demo-bot
cd demo-bot
npm install
```

### Configure .env

Copy the `.env.sample` file to .env and replace the defaults with your own. Though this repo comes with `.env`added to `.gitignore` be careful and **do not commit this file to git**!

### Starting the bot

```bash
npm run build
npm start
```

Example output:

```bash
[Nest] 19364   - 06/01/2019, 5:51 AM   [NestFactory] Starting Nest application...
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Logging into discord
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] PassportModule dependencies initialized +100ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] TypeOrmModule dependencies initialized +1ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] JwtModule dependencies initialized +0ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] MonitoringModule dependencies initialized +1ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] AppModule dependencies initialized +1ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] ChannelsModule dependencies initialized +0ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] AuthModule dependencies initialized +0ms
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Bootstrapping /Users/yomateod/workspace/work/autobots/bot-test/node_modules/@autobot/module-8ball
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: 8ball (Returns a random value like an 8ball would.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: colour (Returns an embed with the color passed to it.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?answer (Answer a HelpDesk question.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?ask (Submits a question to the HelpDesk)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?close (Close a HelpDesk question.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?comment (Adds a comment to a question.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?delete (Delete a HelpDesk questions.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?search (Search the HelpDesk questions.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?tagadd (Creates a new HelpDesk Tag.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ?tagdelete (Deletes a HelpDesk Tag.)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ++add (Create or replace a new macro. Usage: ++add name=docker,message=Check out https://docker.io!)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ++delete (Deletes a macro. Usage: ++delete name=docker)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: * (Display a saved macro. Usage: +docker)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Command Registered: ++list (Display all saved macros. Usage: ++list)
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Bootstrapping /Users/yomateod/workspace/work/autobots/bot-test/node_modules/@autobot/module-flipper
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Bootstrapping /Users/yomateod/workspace/work/autobots/bot-test/node_modules/@autobot/module-helpbot
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Bootstrapping /Users/yomateod/workspace/work/autobots/bot-test/node_modules/@autobot/module-macro-system
Sat Jun 01 2019 05:51:45 GMT-0500 (Central Daylight Time): Bot Started
[Nest] 19364   - 06/01/2019, 5:51 AM   [InstanceLoader] TypeOrmCoreModule dependencies initialized +578ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RoutesResolver] AppController {/}: +5ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RouterExplorer] Mapped {/, GET} route +3ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RoutesResolver] AuthController {/auth}: +0ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RouterExplorer] Mapped {/login, GET} route +1ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RoutesResolver] ChannelsController {/channels}: +0ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RouterExplorer] Mapped {/send, GET} route +1ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RoutesResolver] MonitoringController {/monitoring}: +0ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [RouterExplorer] Mapped {/is_alive, GET} route +0ms
[Nest] 19364   - 06/01/2019, 5:51 AM   [NestApplication] Nest application successfully started +2ms
Sat Jun 01 2019 05:51:46 GMT-0500 (Central Daylight Time): Connected to database 127.0.0.1:3306
Sat Jun 01 2019 05:51:46 GMT-0500 (Central Daylight Time): Connected to discord

```

Now the bot is up and running check your discord server and type `>ping` in any channel and you should get a response!

