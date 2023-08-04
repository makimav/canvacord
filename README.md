# Examples
## Rank Card

```js
const canvacord = require("canvacord");
const img = "https://cdn.discordapp.com/embed/avatars/0.png";

const userData = getDataSomehow();

const rank = new canvacord.Rank()
    .setAvatar(img)
    .setCurrentXP(userData.xp)
    .setRequiredXP(userData.requiredXP)
    .setStatus("dnd")
    .setProgressBar("#FFFFFF", "COLOR")
    .setUsername("Snowflake")
    .setDiscriminator("0007");

rank.build()
    .then(data => {
        const attachment = new Discord.MessageAttachment(data, "RankCard.png");
        message.channel.send(attachment);
    });
```

### Preview
![RankCard](https://raw.githubusercontent.com/neplextech/canvacord/main/test/images/RankCard.png)

## Rank Card Variants

![RankCard](https://raw.githubusercontent.com/neplextech/canvacord/main/test/Gamer.png)

![RankCard](https://raw.githubusercontent.com/neplextech/canvacord/main/test/Nerd.png)

![RankCard](https://raw.githubusercontent.com/neplextech/canvacord/main/test/Player.png)

## Other Examples

```js
const Discord = require("discord.js");
const client = new Discord.Client();
const canvacord = require("canvacord");

client.on("ready", () => {
    console.log("I'm online!");
});

client.on("message", async (message) => {
    if (message.author.bot) return;
    if (message.content === "!triggered") {
        let avatar = message.author.displayAvatarURL({ dynamic: false, format: 'png' });
        let image = await canvacord.Canvas.trigger(avatar);
        let attachment = new Discord.MessageAttachment(image, "triggered.gif");
        return message.channel.send(attachment);
    }
});

client.login("Your_Bot_Token_here");
```
