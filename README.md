####JS BACKTICKS (&#96;) ARE BETTER THAN QUOTES (&quot;)
# Introduction

I am Jgouken, a young developer with ambitions and dreams, just not the best at design. I finally got around to updating this from my crappy 3 sentence emoji-filled thing. I have quite the bit of dedication and creativity than it seems, so here&#39;s are a couple of details about me!

- Mainly uses **discord.js**. :fa-desktop:
- Learned **JavaScript** and **Swift**. :fa-pencil-square-o:
- Learning **HMTL**, **CSS**, and **C languages**. :fa-book:
- **Collaborated** with many developers on their projects. :fa-group:
- In the process of a huge **discord.js project** never seen before. :fa-spinner:
- **Visual Studio Code** is my editor of choice. :fa-windows:
- **GitHub** is my code-saver of choice. :fa-github:
- **Orange** is my color of choice. :fa-tint:

###Levels
**Javascript** - Intermediate&#42; :fa-meh-o:
**Swift** - Intermediate&#42; :fa-meh-o:
**HTML** - Beginner :fa-frown-o:
**C Languages** - Beginner :fa-frown-o:

&#42; Easily 1-upped, but I know plenty.
# Works

Work/Repo  | Description
------------- | -------------
Discord.js Basic Bot Handler  | A template repository attempted to be made for discord.js developers!
Junk | A folder of files from previous forgotten works saved onto my computer for future reference. Feel free to copy some code!
Train Central  | An upcoming grand discord.js project...stay tuned...
Others are self-projects or private repositories.
####My index.js :fa-keyboard-o:

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

# Comments

"Your dedication is impressive." - Manager of WoC [discord.gg/program](http://discord.gg/program "discord.gg/program")

**You&#39;ve reached the end of the page.** :fa-check:
