JS BACKTICKS (&#96;) ARE BETTER THAN QUOTES (&quot;)
# Introduction

I am Jgouken, a young developer with ambitions and dreams, just not the best at design. I finally got around to updating this from my crappy 3 sentence emoji-filled thing. I have quite the bit of dedication and creativity than it seems, so here&#39;s are a couple of details about me!

- Mainly uses **discord.js**.
- Learned **JavaScript** and **Swift**.
- Learning **HMTL**, **CSS**, and **C languages**.
- **Collaborated** with many developers on their projects.
- In the process of a huge **discord.js project** never seen before.
- **Visual Studio Code** is my editor of choice.
- **GitHub** is my code-saver of choice.
- **Orange** is my color of choice.

#### Levels
**Javascript** - Intermediate&#42;\
**Swift** - Intermediate&#42;\
**HTML** - Beginner\
**C Languages** - Beginner

&#42; Easily 1-upped, but I know plenty.
# Works

Work/Repo  | Description
------------- | -------------
Discord.js Basic Bot Handler  | A template repository attempted to be made for discord.js developers!
Junk | A folder of files from previous forgotten works saved onto my computer for future reference. Feel free to copy some code!
Train Central  | An upcoming grand discord.js project...stay tuned...

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

# Comments

"Your dedication is impressive." - Manager of WoC [discord.gg/program](http://discord.gg/program "discord.gg/program")

**You&#39;ve reached the end of the page.**
