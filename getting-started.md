# **Mongodb with mongoose**

## Achnahowa mongoose 🌐
mongoose howa lpackage lighadi tkhdm bih bach tconnecta m3a mongodb, takhod data, tsayft data...

[Docs](https://mongoosejs.com/docs)

## Usage⚡

### Installation
- flbdya ghadi tinstalli `mongoose`

```js
npm i mongoose
```

- mn ba3d ghadi trequiri `mongoose` flfile dyalk

```js
const mongoose = require("mongoose");
```
- db ghadi ntconnectaw ldatabase bmongoose

```js
mongoose.connect("mongodb://localhost:port/database_name", { // andiro localhost ka example
// flcodedya;l ghadi tbdl "localhost:port/database_name" blink dyal database lighadi tkhdm biha
    useNewUrlParser: true,
    useUnifiedTopology: true,
    useFindAndModify: true
});
```

db nta installiti mongoose, otconnectiti ldatabase!

[Next Page](schemas.md)