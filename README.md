I'm a Software Programmer, a young developer with plans. I know how to take time out of my life to make plans for my future. Fueling off of dedication and creativity, I'm growing my reputation as a Software Programmer. I started working with Discord Bots, wanting to learn website development and game development. I learn quickly and effectively to ensure I produce the best material in a short amount of time.

- Obtaining **JavaScript Certification**.
- Learned **JavaScript**, **Swift**, and **C languages**.
- Learning **Spanish** and **Japanese**.
- Learning **HMTL** and **CSS**.
- **Visual Studio Code** is my editor of choice.
- **GitHub** and **Replit** are my code-savers of choice.
- **Orange** is my color of choice.

#### Programming Knowledge
**Javascript** - Intermediate (*Certif. in progress*)\
**Swift** - Intermediate (*Uncertif.*)\
**C Languages** - Intermediate (*Uncertif.*)\
**HTML** - Beginner (*Uncertif.*)

# Works/Volunteers

Work  | Position | Description
------------- | ------------- | -------------
[Make-A-Mand](https://github.com/Jgouken/MakeAMand) | Self | Self-lead project to create helpful commands not seen in many other bots.
[Discord.js Bot Handler](https://github.com/Jgouken/Discord.js-Basic-Bot-Handler) | Self | For me and the public to use my code not often seen by others for many functionalities.
[Junk](https://github.com/Jgouken/Junk) | Self | A dump of random discarded files lounging on my computer.
[Snake](https://github.com/Jgouken/snake) | Self | My first HTML video game to show myself the ropes.
[Calculator](https://github.com/Jgouken/calculator) | Self | My first very simple HTML/CSS program.
[Matrix Development](https://github.com/MatrixDevelopment-GH) | Retired Developer | Designed new processes and abilities that boosted the bot architecually.
[Wyvern](https://wyvern.host/) ([Discord Bot](https://discordbotlist.com/bots/wyvern)) | Retired Lead Developer | Previously lead new designs, creations, and commands that suited the bots' needs along with user-friendly capabilities.

Sorted from Newest to Oldest.
Not mentioned: Private or Discarded repositories.
#### My Main discord.js index.js File

```javascript
const config = require('./config/config')
const { bot, Discord } = require('./config/config')
const fs = require('fs')
bot.commands = new Discord.Collection();
bot.aliases = new Discord.Collection();
const commandFiles = fs.readdirSync('./commands').filter(file => file.endsWith('.js'));

let cmds = [];
for (const file of commandFiles) {
	const command = require(`./commands/${file}`);
	bot.commands.set(command.name, command);
	cmds.push(command.name)
	command.aliases.forEach(alias => {
		bot.aliases.set(alias, command)
		cmds.push(alias)
	})
}

bot.on('ready', async () => {
	await config.db.delete(`test`)
	console.log(`\n\n${config.name} IS ONLINE!\n\n`);
	let types = ['LISTENING', 'WATCHING', 'PLAYING', 'STREAMING', 'COMPETING'];
	bot.user.setActivity(`m-${cmds[Math.floor(Math.random() * cmds.length)]}`, {
		type: types[Math.floor(Math.random() * types.length)],
	})

	setInterval(async () => {
		bot.user.setActivity(`m-${cmds[Math.floor(Math.random() * cmds.length)]}`, {
			type: types[Math.floor(Math.random() * types.length)],
		})
	}, 10000)

	bot.on('messageCreate', async message => {
		if (message.author.bot) return;
		if (message.channel.type == 'dm') return;
		if (!(message.guild.me).permissions.has("SEND_MESSAGES")) return;
		var prefix = await config.db.get(`prefix_${message.guild.id}`)
		if (!prefix) var commandArgs = message.content.slice(config.prefix.length).trim().split(/ +/);
		else var commandArgs = await message.content.slice(prefix.length).trim().split(/ +/)

		const member = await message.guild.members.fetch(message.author)
		const command = commandArgs.shift().toLowerCase()
		const called = bot.commands.get(command)

		if (message.content == '<@!932394428453232751>' || message.content == '<@932394428453232751>') return bot.commands.get('start').execute(message, member, commandArgs, bot.commands, config, bot)

		if (!prefix) {
			if (!message.content.toLocaleLowerCase().startsWith(config.prefix.toLocaleLowerCase())) return
		} else if (!message.content.toLocaleLowerCase().startsWith(prefix)) return;

		if (called) called.execute(message, member, commandArgs, bot.commands, config, bot)
		else if (bot.aliases.get(command)) bot.aliases.get(command).execute(message, member, commandArgs, bot.commands, config, bot)
	})
})

bot.login(config.TOKEN)
// Code put together by https://github.com/Jgouken. Full program can be found here https://github.com/Jgouken/MakeAMand.
// Getting into Discord Bots? My coding template can be found here https://github.com/Jgouken/Discord.js-Basic-Bot-Handler.
```
Feel free to copy my public code for any non-commercial purposes. Credit is not required but is fully appreciated!

# Personal Achievements
Participated in a Robotics Team and became sponsored by businesses such as Amazon, Tesla, and Gene Haas.

# Compliments

> "It's amazing to see how he wraps his brain around a problem at such a young age."
- [Tesla Nevada](https://www.tesla.com/gigafactory) Official/Recruiter
> "Your work, time, and dedication is exceedingly astounding for this [robotics] team."
- Senior Architect/Teacher
> "Your dedication is impressive."
- Manager of World of Code [Discord Server](http://discord.gg/program)
