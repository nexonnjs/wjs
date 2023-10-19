## Simplicity WhatsApp Bot (Baileys)

> This is a WhatsApp bot module based on Baileys which can be used in a very easy way.

### Example

For example of use you can open the [example](https://github.com/nexonnjs/js/tree/master/example) folder or here for [example base](https://github.com/neoxr/wbot)

<p align="center"><img align="center" width="100%" src="https://telegra.ph/file/7ad1c9fb5cfe4862d8f87.jpg" /></p>

### Handling Events

There are several events that can be used are as follows :

```Javascript
client.on('connect', () => console.log)
client.on('error', error => console.log(error))
client.on('ready', () => console.log)
client.on('message', ctx => console.log(ctx))
client.on('message.delete', ctx => console.log(ctx))
client.on('group.add', ctx => console.log(ctx))
client.on('group.remove', ctx => console.log(ctx))
client.on('group.promote', ctx => console.log(ctx))
client.on('group.demote', ctx => console.log(ctx))
client.on('caller', ctx => console.log(ctx))
client.on('presence.update', ctx => console.log(ctx))
```

### Event Message (message)

```Javascript
{
   m: {
      key: {
         remoteJid: '6285887776722@s.whatsapp.net',
         fromMe: false,
         id: 'A4A5E1FB9C33178CD11673178C46CA1E',
         participant: undefined
      },
      messageTimestamp: 1689557472,
      pushName: 'Kens Ransyah',
      broadcast: false,
      message: Message {
         extendedTextMessage: [ExtendedTextMessage],
         messageContextInfo: [MessageContextInfo]
      },
      id: 'A4A5E1FB9C33178CD11673178C46CA1E',
      isBot: false,
      chat: '6285726319205@s.whatsapp.net',
      fromMe: false,
      isGroup: false,
      sender: '6285726319205@s.whatsapp.net',
      mtype: 'extendedTextMessage',
      msg: ExtendedTextMessage {
         text: '.menu',
         previewType: 0,
         contextInfo: [ContextInfo],
         inviteLinkGroupTypeV2: 0
      },
      quoted: null,
      mentionedJid: [],
      reply: [Function(anonymous)],
      text: '.menu'
   },
   body: '.menu',
   prefix: '.',
   plugins: [],
   commands: [],
   args: [],
   command: 'menu',
   text: '',
   prefixes: ['.', '#', '!', '/']
}
```
### Messaging Function

```Javascript
// declaration variable sock
const sock = client.sock

// send a text message (auto tagged)
sock.reply(m.chat, `Test!`, m)

// send a react message
sock.sendReact(m.chat, `💀`, m.key)

// send a text message with progress bar
sock.sendProgress(m.chat, `Test!`, m)

// send a ptv message from path, url, or buffer (video duration 10s)
sock.sendPtv(m.chat, `./media/video/yemete.mp4`)

// send a text message with custom thumbnail
sock.sendMessageModify(m.chat, `Test!`, m, {
   title: '© nexon-bot',
   largeThumb: true,
   ads: false,
   /* can buffer or url */
   thumbnail: 'https://telegra.ph/file/1f54f0c9a0245e01cd662.jpg',
   link: 'https://chat.whatsapp.com/DREGAHAKAnC1VSa4P5V45k'
})

// send a file from path, url, or buffer (auto extension)
sock.sendFile(m.chat, 'https://telegra.ph/file/1f54f0c9a0245e01cd662.jpg', 'image.jpg', 'Test!', m)

// send a document from path, url, or buffer (auto extension)
sock.sendFile(m.chat, 'https://telegra.ph/file/1f54f0c9a0245e01cd662.jpg', 'image.jpg', 'Test!', m, {
   document: true
})

// send a voicenote from path, url, or buffer
sock.sendFile(m.chat, './media/audio/ah.mp3', '', '', m, {
   ptt: true
})

// send a audio from path, url, or buffer with thumbnail in audio tag
sock.sendFile(m.chat, './media/audio/ah.mp3', '', '', m, {
   APIC: < Buffer >
})

// send a sticker message from url or buffer
sock.sendSticker(m.chat, 'https://iili.io/HP3ODj2.jpg', m, {
   packname: 'Copyright by',
   author: '© nexon.js'
})

// forward message
sock.copyNForward(m.chat, m)
```
