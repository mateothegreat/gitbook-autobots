# Setup Discord

We need to acquire a bot token. To do this you'll have to go to [https://discordapp.com/developers/applications/](https://discordapp.com/developers/applications/) and create a new application. From there you'll need to grab the client ID and use the url below to invite the bot to your server.

{% embed url="https://discordapp.com/developers/applications/" caption="Manage Discord Applications" %}

### Authorization

We need to assign our new bot to a server. You can register the new bot with your server by opening a browser and going to:  
  
https://discordapp.com/oauth2/authorize?client\_id=CLIENT\_ID\_GOES\_HERE&scope=bot

{% hint style="info" %}
Replace CLIENT\_ID\_GOES\_HERE with your Client Id from the step above!
{% endhint %}

### Bot Token

After authorizing your bot you'll receive a bot token. Save this for the next step where you'll need to add it to your `.env` file.

