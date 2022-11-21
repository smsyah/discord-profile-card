# **Mongodb with mongoose**

##### db installina mongoose otconnectina ldatabase, ansawbo schema bach nbdaw lkhdma, but achnahiya schema ba3da?

## Schema
>**schema hiya chi haja daroriya fmoongose bach tkhdm m3a data, hiya bach**
>**kat7edad chi collection. ana anwarik wa7ed lexample**
>
>**tkhayl 3andna wa7ed lbot dyal tickets, ohad lbot kaykhdm bjson**
>**bach nb9aw nakhdo data mn hadak ljson file andiro chi haja haka**

```js
const ticketsData = require("./tickets.json"); // tickets.json howa lfile lifih data
const ticketId = "4787823498894098409"; // matalan hadi hiya ticket libaghin nakhdo data dyalha
console.log(ticketsData[ticketId]);
```

>**walakin m3a mongoose andiro khdma akhra**
>**bach tfhm lkhdma dyal mongoose mzyan, fhad tutorials andiro wa7ed lproject, had lproject howa bot dyal welcome oghadi nkhdmo bmongoose bach t3rf tkhdm biha 7san**

>**bach nshlo 3la rasna lkhdma chwiya oikon dakchi mndm, ghadi nsawbo wa7ed lfolder jdid, atkon smito `schemas`, ofhad lfolder andiro file jdid smito `GuildsConfig.js`**
>**wast had lfile aykon had lcode**

```js
const mongoose = require("mongoose");

const GuildsConfigSchema = new mongoose.schema({
    guildId: {
        type: mongoose.SchemaTypes.String,
        required: true,
        unique: true,
    },
    welcomeChannel: {
        type: mongoose.SchemaTypes.String,
        unique: true,
    },
    welcomeStatus: {
        type: mongoose.SchemaTypes.Boolean,
        required: true,
        default: false,
    },
    welcomeMessage: {
        type: mongoose.SchemaTypes.String,
        default: "$<member-tag> welcome to $<server-name>!",
    },
});

module.exports = mongoose.model("GuildConfig", GuildsConfigSchema);
```

> **so db ana anchr7 lik achno kaydir had lcode**
> **flbdya requirina `mongoose` bach n9dro nkhdmo biha**
> **mn ba3d drna schema jdida**
> **fhad schema drna data lighadi tkon fiha**
>
> - **aykon fiha `guildId`, lihowa lid dyal server, type dyalo string, aykon required ounique**
>
> - **oghadi ikon `welcomeChannel`, lihowa lid dyal channel dyal lwelcome type dyalo string oghadi ikon unique**
>
> **ghadi ikon `welcomeStatus`, type dyalo boolean, aykon required odefault howa `false`**
>
> **ghadi ikon `welcomeMessage`, lihowa lmessage dyal lwelcome lighadi nsayfto lroom dyal lwelcome type dyalo string, odefault howa `$<member-tag> welcome to $<server-name>!`**
>
>**and flkhr exportina lmodel bach n9dro nkhdmo bih**

## Schema Options

> **so kima chfti lfo9 schemas i9dro ikono 3andhom options, hna anwarik chi options oachno kaydiro**
>
> - **required**
>   - had loption kat3ni ila kant lprop libaghi tzid daroriya, f7alat kant daroriya omakanch default value, obghiti tzid chi GuildConfig oma3titich lvalue dyalha ghadi ikon error.
> - **default**
>   - hada aykon howa default value dyal chi prop ila mat3tach lvalue dyalha fach kan kaytsawb lGuildConfig
> - **lowercase**
>   - had loption kat3ni ila bghiti dima string likayn fhadik lprop iwaliw l7orof dyalo sghar `(ex: Test => test)`
> - **uppercase**
>   - had loption l3aks dyal lilfo9, kat3ni ila bghiti dima string iwaliw l7orof dyalo kbar `(ex: Test => TEST)`
>
> **kaynin options bzaf t9dr [t9ra 3lihom hna](https://mongoosejs.com/docs/schematypes.html#schematype-options)**

**db 9adina schema, ila bghina nkhdmo biha ghadi nrequiriwha flfile libghina**

```js
const GuildsConfig = require("./schemas/GuildsConfig.js");
```

[Go Back](getting-started.md) | [Next Page](create-a-document.md)