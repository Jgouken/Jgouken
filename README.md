I am Jgouken, a young developer with plans. I know how to take time out of my life to make plans for my future. Fueling off of dedication and creativity, I&#39;m growing my reputation as a Software Developer.

- Mainly uses **discord.js**.
- Learned **JavaScript**, **Swift**, and **C languages**.
- Learning **HMTL**, and **CSS**.
- **Visual Studio Code** is my editor of choice.
- **GitHub** is my code-saver of choice.
- **Orange** is my color of choice.

#### Levels
**Javascript** - Advanced&#42;\
**Swift** - Intermediate&#42;\
**C Languages** - Intermediate&#42;\
**HTML** - Beginner

# Works/Volunteers

Work  | Description
------------- | -------------
[Matrix Development](https://github.com/MatrixDevelopment-GH) | Developer
[Wyvern](https://discordbotlist.com/bots/wyvern) | Previous Lead Developer

Others are self-projects or private repositories.
#### My index.js

```javascript
const config = require('./config/config')
const {db, bot, Discord} = require('./config/config')
const fs = require('fs')

bot.commands = new Discord.Collection();
const commandFiles = fs.readdirSync('./commands').filter(file => file.endsWith('.js'))
for (const file of commandFiles) {
  const command = require(`./commands/${file}`)
  bot.commands.set(command.name, command)
}

bot.on('ready', async () => {
  console.log('yipee!')
})

bot.on('message', async (message) => {
  if (message.author.bot) return;
  if (message.channel.type == 'dm') return;
  if (!message.content.toLocaleLowerCase().startsWith(config.prefix)) return;
  if (!(message.guild.me).hasPermission("SEND_MESSAGES")) return;
  const input = message.content.slice(config.prefix.length).trim()
  if (!input.length) return;
  var [, command, commandArgs] = input.match(/(\w+)\s*([\s\S]*)/);
  commandArgs = commandArgs.toLocaleLowerCase().trim().split(" ")
  const called = bot.commands.get(command)
  if (called) called.execute(message, commandArgs, config, bot)
})

bot.login(config.TOKEN)
```
Feel free to copy the code! It&#39;s nothing but a combination of codes I found on the internet.

# Compliments

"Your dedication is impressive." - Manager of [WoC](http://discord.gg/program)
