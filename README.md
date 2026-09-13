<div align="center">

# 💬 Quote Generator

**Generate beautiful WhatsApp-style quote images — locally, without any external API.**


 🔀 **Fork of** [`@neoxr/quote-api`](https://www.npmjs.com/package/@neoxr/quote-api/v/1.1.1-dev), originally based on [**LyoSU — Quote API**](https://github.com/LyoSU/quote-api).

This package generates quote images from WhatsApp-style messages.

 🖼️ **I'm in charge of keeping the emoji images updated to the latest version.**

</div>

---

## 📦 Installation

This fork is intended to be used directly from GitHub.

```bash
npm install github:ds6/quote-api
```

### `package.json`

```json
{
  "dependencies": {
    "@neoxr/quote-api": "github:ds6/quote-api"
  }
}
```

---

## 🚀 Example

```javascript
const quoteApi = require('@neoxr/quote-api')
const fs = require('node:fs')

const text = 'Hello World'
const username = 'Alι_Aryαɴ'
const avatar = 'https://telegra.ph/file/59952c903fdfb10b752b3.jpg'

const json = {
  type: 'quote',
  format: 'png',
  backgroundColor: '#FFFFFF',
  width: 512,
  height: 768,
  scale: 2,
  messages: [
    {
      entities: [],
      avatar: true,
      from: {
        id: 1,
        name: username,
        photo: {
          url: avatar
        }
      },
      text,
      replyMessage: {}
    }
  ]
}

quoteApi(json).then(res => {
  const buffer = Buffer.from(res.image, 'base64')

  fs.writeFile('Quotly.png', buffer, err => {
    if (err) throw err
  })
})
```

---


## 🎨 Bubble style

The generator now uses a softer WhatsApp-style bubble: more circular corners, a subtle lower-left speech tail, and the avatar layered on top of the bubble near its lower-left corner.

---

## 🙏 Credits

> **The credits are not mine.**

- 💚 Thanks to [**@neoxr**](https://github.com/neoxr) for the fork **without starting an HTTP server**.
- 💙 Thanks to [**@LyoSU**](https://github.com/LyoSU) for creating this **quote-api**.

If you prefer, you can also follow the original project at [**LyoSU/quote-api**](https://github.com/LyoSU/quote-api) — just keep in mind that it uses an HTTP-server-based system and requires running a server.