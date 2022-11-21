# **Mongodb with mongoose**

**ila bghina njibo chi document mn database, kandkhmo blmethod `findOne`**

**scenario lighadi ndiro fhad lexample, howa chi member jdid dkhl lchi server, olbot ghadi nsayfto welcome message**

```js
client.on("guildMemberAdd", (member) => {
    const guildData = GuildsConfig.findOne({ guildId: member.guild.id });
    if (!guildData) return;
    if (!guildData.welcomeStatus) return;
    const welcomeChannel = member.guild.channels.cache.get(guildData.welcomeChannel);
    if (!welcomeChannel) return;
    let newWelcomeMessage = guildData.welcomeMessage.replace(/\$<server-name>/g, member.guild.name).replace(/\$<member-tag>/g, member.user.tag);

    welcomeChannel.send(newWelcomeMessage);
});
```

> **lidrna howa anana tsntna levent `guildMemberAdd`, omli kaydkhol chi member jdid lchi server kanjibo data dyal hadak server**
> **kanchofo ila kan server 3ando data, ila makanch 3ando kanreturniw**
> **kanchofo status dyal welcome fserver wach true *`enabled`* ola false *`disabled`***
> **kanjibo lwelcome channel mn server, ila kant kansyfto fiha lmessage dyal lwelcome**

[Go Back](create-a-document.md) | [Next Page](update-a-document.md)