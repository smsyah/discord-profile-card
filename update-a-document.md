# **Mongodb with mongoose**

**kayn joj dyal toro9** *likan3rf* **bach nupdatiw chi document**

## Method 1

> **kankhdmo blmethod `findOneAndUpdate`**
> **fhad lexample andiro command dyal setup *config***

```js
client.on("message", async (message) => {
    if (message.author.bot) return;
    if (message.content.toLowerCase().startsWith(prefix + "setup")) {
        if (!message.guild) return;
        if (!message.member.hasPermission("MANAGE_GUILD")) return message.channel.send("You don't have the `MANAGE_GUILD` permission!");
        const [param, ...args] = message.content.split(" ").slice(1);
        if (param === "welcome-status") {
            if (!args[0] || !["enabled", "disabled"].includes(args[0])) return message.channel.send("Please provide a valid status *(enabled/disabled)*");

            try {
                await GuildsConfig.findOneAndUpdate(
                    { guildId: message.guild.id },
                    { $set: { welcomeStatus: args[0] === "enabled" ? true : false } }
                );

                message.channel.send(`Successfully changed the status to "${args[0]}"`);
            } catch (error) {
                console.error(error);
                message.channel.send("There was an error while trying to change the welcome status!");
            }
            
        } else if (param === "welcome-channel") {
            if (!message.mentions.channels.first()) return message.channel.send("Please mention the channel you want to set");

            try {
                await GuildsConfig.findOneAndUpdate(
                    { guildId: message.guild.id },
                    { $set: { welcomeChannel: message.mentions.channels.first().id } }
                );

                messsage.channel.send(`Successfully set the new welcome channel to <#${message.mentions.channels.first().id}>`);
            } catch (error) {
                console.error(error);
                message.channel.send("There was an error while trying to change the welcome channel!");
            }
        } else if (param === "welcome-message") {
            const newMessage = args.join(" ");
            if (!newMessage.length) return message.channel.send("Please provide a valid message");

            try {
                await GuildsConfig.findOneAndUpdate(
                    { guildId: message.guild.id },
                    { $set: { welcomeMessage: newMessage } }
                );

                message.channel.send(`Successfully set the welcome message to "${newMessage}"`);
            } catch (error) {
                console.error(error);
                message.channel.send("There was an error while trying to change the welcome message!");
            }
        }
    }
});
```
> **hna stakhdmna `findOneAndUpdate`**
> **had lmethod katakhod lcondition olupdate lighadi dir**
> - **lcondition hiya lighadi njibo biha server, fhad l7ala drna `guildId: message.guild.id`**
> - **lupdate howa likaykon fih lupdate lighadi ndiro ldata, ila chfti 7na drna `$set: {}` 3ada drna update ldata, n9adro n7aydoha walakin mn l2afdal ila khlinaha bach maytrach chi mochkilotbdl data kamla**
>
> ***NOTE*: ila knti baghi takhod data jdida lidrti liha save, atzid had loption `new: true`**
> ```js
> let newData = await GuildsConfig.findOneAndUpdate(
>    { guildId: message.guild.id }, // conditions
>    { welcomeStatus: false }, // update
>    { new: true } // options
> );
>
> console.log(newData); // atlogi data jdida
>```

## Method 2

> **fhad tari9a kankhdmo blmethod `save`**

```js
client.on("message", async (message) => {
    if (message.author.bot) return;
    if (message.content.toLowerCase().startsWith(prefix + "set-welcome-message")) {
        const args = message.content.split(" ").slice(1);
        const guildData = GuildsConfig.findOne({ guildId: message.guild.id });

        try {
            guildData.welcomeMessage = args.join(" ");
            guildData.save();

            message.channel.send(`Successfully set the new welcome message to **${args.join(" ")}**`);
        } catch (error) {
            console.error(error);
            message.channel.send("There was an error while trying to change the welcome message!");
        }
    }
});
```

> **f7al hoka kan9ado data libghayna direct, okandiro save liha**
> **n9dro n9ado ktar mn haja 3ada ndiro save**
> ```js
> guildData.welcomeMessage = "Hello there, welcome";
> guildData.welcomeStatus = true;
> guildData.save();
> ```

[Go Back](get-a-document.md) | [Next Page](delete-a-document.md)