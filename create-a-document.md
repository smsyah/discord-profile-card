# **Mongodb with mongoose**

**db installina `mongoose`, otconnectina ldatabase and sawbna schema lservers**
**ghadi nsawbo config lserver jdid db, lta7t ghadi ikono examples dyal discord bot**

## Creating a new document
**NOTE: guild data katsma document, database kaykono fiha documents**

**scenario lighadi ndiro hna, howa chi user dkhal lbot lserver jdid o7na ghadin nzido hadak server fdatabase**

**ghadi nstkhdmo levent dyal `guildCreate`**

```js
const { Client } = require("discord.js");
const client = new Client();
const GuildsConfig = require("./schemas/GuildsConfig.js");

client.on("guildCreate", async (guild) => {
    console.log(`Yeey! Joined to a new server, ${guild.name} (${guild.id})`);

    console.info(`Creating a new document for ${guild.id}`);
    try {
        await GuildsConfig.create({
            guildId: guild.id,
            welcomeStatus: false,
        });

        console.info(`Successfully created a new document for ${guild.id}`);
    } catch (error) {
        console.error(`There was an error while trying to create a new document for ${guild.id}`, error);
    }
});
```
> **lidrna db howa tsantna levent dyal `guildCreate`, bach ila dkhl lbot lchi server jdid nzidoh fdatabase**
> **fach kaydkhol lbot lchi server jdid kan3ayto lmethod `create`, okandiro fiha object fih data dyal server, fhad l7ala drna guildId howa lid dyal server olwelcomeStatus drnaha false**
> **drna try/catch bach ila kan chi error nlogiwh**

[Go Back](schemas.md) | [Next Page](get-a-document.md)