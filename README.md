# Canvacard
Potente herramienta de manipulación de imágenes para manipular imágenes fácilmente.

# Installation

```sh
$ npm i canvacard
```

[![NPM](https://nodei.co/npm/canvacard.png)](https://nodei.co/npm/canvacard/)

# Features
- Súper simple y fácil de usar 😎
- Más rápido que canvacard v4 🚀
- ¿Más de **50 métodos** ...? ¡Hurra! 🎉
- Construido sobre un lienzo de nodos y sin tonterías involucradas 🔥
- Orientado a objetos 💻
- Apto para principiantes 🤓
- Soporta emojis 😀

# Examples
## Rank Card

```js
const canvacard = require("canvacard");
const img = "https://cdn.discordapp.com/embed/avatars/0.png";

const userData = getDataSomehow();

const rank = new canvacard.Rank()
    .setAvatar(img)
    .setCurrentXP(userData.xp)
    .setRequiredXP(userData.requiredXP)
    .setStatus("dnd")
    .setProgressBar("#FFFFFF", "COLOR")
    .setUsername("SrGobi")
    .setDiscriminator("5100");

rank.build()
    .then(data => {
        const attachment = new Discord.MessageAttachment(data, "RankCard.png");
        message.channel.send(attachment);
    });
```

### Preview
![RankCard](https://i.imgur.com/j7m8T5x.png)

## Welcomer Card

```js
const canvacard = require("canvacard");
const img = "https://cdn.discordapp.com/embed/avatars/0.png";
const background = "https://i.imgur.com/ulr1KDT.png";

const welcomer = new canvacard.Welcomer()
    .setAvatar(img)
    .setBackground('IMAGE', background)
    .setTitulo("WELCOME")
    .setSubtitulo("Subtitulo personalizable!")
    .setTitulo("Titulo personalizable!")
    .setSubtitulo("Subtitulo personalizable!")
    .setColorTitulo("#FFFFFF");
    .setColorSubtitulo("#5865f2");
    .setColorCircle("#FFFFFF");
    .setColorBorder("#000000");
    .setOpacityBorder("0.4");

welcomer.build()
    .then(data => {
        const attachment = new Discord.MessageAttachment(data, "WelcomerCard.png");
        message.channel.send(attachment);
    });
```

### Preview
![WelcomerCard](https://i.imgur.com/ulr1KDT.png)

## Other Examples

```js
const Discord = require("discord.js");
const client = new Discord.Client();
const canvacard = require("canvacard");

client.on("ready", () => {
    console.log("¡Estoy en línea!");
});

client.on("message", async (message) => {
    if (message.author.bot) return;
    if (message.content === "!triggered") {
        let avatar = message.author.displayAvatarURL({ dynamic: false, format: 'png' });
        let image = await canvacard.Canvas.trigger(avatar);
        let attachment = new Discord.MessageAttachment(image, "triggered.gif");
        return message.channel.send(attachment);
    }
});

client.login("Tu_Bot_Token_aqui");
```

# Note
> ⚠ | Para usar `Canvacard#Welcomer`/`Canvacard#Leaver`/`Canvacard#CaptchaGen`, es posible que deba instalar paquetes como **[discord-canvascard](https://npmjs.com/package/discord-canvascard)** & **[captcha-canvas](https://npmjs.com/package/captcha-canvas)**.