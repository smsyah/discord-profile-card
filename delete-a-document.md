# **Mongodb with mongoose**

**bach tms7 chi document l9adiya sahla**

**fhad lexample andiro lbot khraj mn chi server, oghadi ims7 data dyalo**

```js
client.on("guildDelete", async (guild) => {
    console.log(`I left a guild :( ${guild.name} (${guild.id})`);

    console.info(`Deleting the document for ${guild.id}`);

    try {
        await GuildsConfig.deleteOne({ guildId: guild.id });

        console.log(`Successfully deleted the document for ${guild.id}`);
    } catch (error) {
        console.error(`There was an error while trying to delete the document for ${guild.id}`, error);
    }
});
```

> **lmethod likhdmna biha hiya `deleteOne`**
> **f7al ga3 lmethods ta9riban katakhod lconditions *`guildId: message.guild.id`***
>
> ***NOTE*: kaynin bzaf dyal lmethods bach tms7 chi document *(deleteOne, findByIdAndDelete, findOneAndDelete, deleteMany, remove)***
> **but makaynch chi far9 kbir binathom so yeah**

[Go Back](update-a-document.md)