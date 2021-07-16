## Discord-Moderator-Light
----
#### Features:
- Easy and simple
- Beginner Friendly
- Supports Mass actions like Massban, massmute

----
#### Support Server
**__Invite__**: https://discord.gg/QWKzWpdFZc

----
### Example Code

```js
const {
Client,
Intents
} = require('discord.js-light');

var myIntents = new Intents(Intents.ALL);

const mod = require('discord-moderator-light')
const client = new Client({
intents: myIntents,
allowedMentions: {
parse: ['users'],
repliedUser: true
},
messageCacheMaxSize: 1,
messageCacheLifetime: 10000,
messageSweepInterval: 360000,
cacheGuilds: true,
cacheChannels: true,
cacheOverwrites: true,
cacheMembers: false,
cacheRoles: true,
cacheEmojis: false,
cachePresences: false
});

client.on('ready', async () => {
console.log('ok')
})

client.on('message', async message => {
if (message.content.startsWith(`!ban`)) {
userIDs = ['00070300'] // Ability to massban. All you need is get multiple IDs by message collector or something.
reason = 'scam' // Ban reason
days = 7 // Number of days to purge.
interval = 2000 //To avoid API Abuse, we will ban 1 ID in every 2 seconds.
try {
await mod.Ban(message, userIDs, reason, days, interval)
console.log('banned')
} catch (err) {
if (err.message.startsWith('Invalid ID')) console.log('Invalid ID was provided')
else if (err.message.startsWith(`No Input.`)) console.log(`No Input was given.`)
console.log(err)
//Handle error like this to respond to user input.
};
} else if (message.content.startsWith(`!unban`)) {
userIDs = ['038100', 'id2'] // Ability to massunban. All you need is get multiple IDs by message collector or something.
interval = 2000 //To avoid API Abuse, we will unban 1 ID in every 2 seconds.
try {
await mod.Unban(message, userIDs, interval)
} catch (err) {
if (err.message.startsWith('Invalid ID')) console.log('Invalid ID was provided')
else if (err.message.startsWith(`No Input.`)) console.log(`No Input was given.`)
console.log(err)
//Handle error like this to respond to user input.
}
} else if (message.content.startsWith(`!kick`)) {
userIDs = ['00', 'id2', 'id3'] // Ability to massunkick. All you need is get multiple IDs by message collector or something.
reason = 'spam' // The reason
interval = 2000 //To avoid API Abuse, we will kick 1 ID in every 2 seconds.
try {
await mod.Kick(message, userIDs, reason, interval)
} catch (err) {
if (err.message.startsWith('Invalid ID')) console.log('Invalid ID was provided')
else if (err.message.startsWith(`No Input.`)) console.log(`No Input was given.`)
console.log(err)
//Handle error like this to respond to user input.
}
} else if (message.content.startsWith(`!mute`)) {
userIDs = ['id1', 'id2', 'id3'] // Ability to massunmute. All you need is get multiple IDs by message collector or something.
roleID = 'id' // The mute role ID. Package will take care if its valid or not.
interval = 2000 //To avoid API Abuse, we will mute 1 ID in every 2 seconds.
try {
await mod.Mute(message, userIDs, roleID, interval)
} catch (err) {
if (err.message.startsWith('Invalid ID')) console.log('Invalid ID was provided')
else if (err.message.startsWith(`No Input.`)) console.log(`No Input was given.`)
console.log(err)
//Handle error like this to respond to user input.
}
} else if (message.content.startsWith(`!unmute`)) {
userIDs = ['id1', 'id2', 'id3'] // Ability to massununmute. All you need is get multiple IDs by message collector or something.
roleID = 'id' // The mute role ID. Package will take care if its valid or not.
interval = 2000 //To avoid API Abuse, we will mute 1 ID in every 2 seconds.
try {
await mod.Unmute(message, userIDs, roleID, interval)
} catch (err) {
if (err.message.startsWith('Invalid ID')) console.log('Invalid ID was provided')
else if (err.message.startsWith(`No Input.`)) console.log(`No Input was given.`)
console.log(err)
//Handle error like this to respond to user input.
}
}
})
client.login('¯\_(ツ)_/¯');
```

----
