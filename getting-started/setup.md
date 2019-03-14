---
description: Configure the .env file with our database credentials.
---

# Setup .env

  
In the root directory of our project we need to have a plain text file that contains variables for configuring our application.  
  
We'll use the default `.env` filename so that when we call `dotenv.config()` before our app starts it will make these variables available as "environment variables" under the `process.env` object.

{% hint style="danger" %}
Make sure you add "**.env**" to your .gitignore file to prevent your token and other credentials from being exposed in your git repository remote\(s\).
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="/.env" %}
```typescript
TOKEN=<your discord bot token>
OWNER_ID=<your discord user id>
MYSQL_HOST=<mysql hostname>
MYSQL_USER=<mysql username>
MYSQL_PASSWORD=<mysql password>
MYSQL_DATABASE=<mysql database>
```
{% endcode-tabs-item %}
{% endcode-tabs %}



