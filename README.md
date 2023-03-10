# Jgouken
I'm a `Software Programmer`, celebrating **4 years** of Software Programming 🎉🎉🎉!
First thing's first, I'm fueling off of dedication and creativity and slowly growing my reputation as a Software Programmer. I started working with Discord Bots, wanting to learn website and game development for the betterment and interconnection of interests. I have a lot on my plate, but I learn quickly and effectively to ensure I produce the best material I can with the least amount of second guessing. One day this name may land in the papers! 📰

- Learned **JavaScript**, **Swift**, and **C languages**.
- Learning **HMTL** and **CSS**.
- **Visual Studio Code** is my editor of choice.
- **GitHub** and **Replit** are my code-savers of choice.
- **Orange** is my color of choice.

#### Programming Knowledge
**Javascript** - Intermediate to Advanced\
**Swift** - Intermediate\
**C Languages** - Intermediate\
**HTML/CSS** - Beginner

# Works/Volunteers
All of the following are works of Discord.js bots going back to May 17th, 2020 with 27,000+ [^1] lines of code in counting.
Work  | Position | Description
------------- | ------------- | -------------
[The Introvert Advantage](https://github.com/jgouken/the-introvert-advantage) | School Project & Solo | This was done as an assignment. This is a [text-based game](https://the-introvert-advantage.jgouken.repl.co/) using HTML, CSS, and JavaScript. This project will be expanded significantly in the future.
[Bot-ez-a](https://github.com/Jgouken/BOT-ez-a) | Volunteer Developer (scrapped) | Previously assisted aspiring developers create commands their privated server's needs.
[Make-A-Mand](https://github.com/Jgouken/MakeAMand) | Solo | Self-lead project to create helpful commands not seen in many other bots. Lead to nowhere.
[Discord.js Bot Handler](https://github.com/Jgouken/Discord.js-Basic-Bot-Handler) | Solo | For me and the public to use my code not often seen by others for many functionalities.
[TC-Phone](https://github.com/Jgouken/TC-Phone) | Solo (scrapped) | This was my add-on to Train Central; a "phone" for Discord users to use as their interface to this RPG world (such as an economy system).
[Train Central](https://github.com/Jgouken/Train-Central) | Solo (scrapped) | This was an RPG-like idea using Discord; a train would go around different "regions" and users would have to catch the train to view and go to these regions.
[Junk](https://github.com/Jgouken/Junk) | - | A dump of discarded files of mine lounging on my computer.
[Snake](https://github.com/Jgouken/snake) | Solo | My first HTML video game to show myself the ropes.
[Calculator](https://github.com/Jgouken/calculator) | Solo | My first very simple HTML/CSS program.
[Matrix Development](https://github.com/MatrixDevelopment-GH) | Volunteer Developer (Retired) | Designed new processes and abilities that boosted the bot architecually.
[Wyvern](https://wyvern.host/) ([Discord Bot](https://discordbotlist.com/bots/wyvern)) | Lead Volunteer Developer (Retired) | Previously lead new designs, creations, and commands that suited the bots' needs along with user-friendly capabilities.
[JgoChat](https://github.com/Jgouken/JgoChat) | Solo (scrapped) | A very old project to essentially create ChatGPT (before it was even created) didn't lead to anywhere.

Not mentioned: Private or Discarded repositories. [^2]
#### My Main discord.js index.js File

```javascript
const { Collection, Routes } = require('discord.js');
const config = require('./config/config.js')
const listeners = require('./config/listeners.js');
const { REST } = require('@discordjs/rest');
const rest = new REST({ version: '10' }).setToken(config.TOKEN);

const fs = require('fs');
const path = require('path');
const sCommandsPath = path.join(__dirname, 'slash_commands');
const sCommandFiles = fs.readdirSync(sCommandsPath).filter(file => file.endsWith('.js'));

config.bot.sCommands = new Collection();
let scmds = []

for (const file of sCommandFiles) {
	const command = require(`./slash_commands/${file}`);
	config.bot.sCommands.set(command.data.name, command);
	scmds.push(command.data)
}

rest.put(Routes.applicationGuildCommands(config.clientId, '929575731497951312'), { body: scmds.map(command => command.toJSON()) }).then(() => {
	console.log(`Slash Commands Updated`)
}).catch(console.error);
listeners.execute(config.bot, config.db)

config.bot.login(config.TOKEN)
// Code put together within a private repository.
// Not much code, right? I've allocated more of my time to reorganization, just so that I know exactly where what happens.
```
Feel free to copy my public code! [^3]

# Personal Achievements
Participated in a Robotics Team and became sponsored by businesses such as Amazon, Tesla, and Gene Haas.

# Compliments

> "It's amazing to see how he wraps his brain around a problem at such a young age."
- [Tesla Nevada](https://www.tesla.com/gigafactory) Official/Recruiter
> "Your work, time, and dedication is exceedingly astounding for this [robotics] team."
- Senior Architect/Teacher
> "Your dedication is impressive."
- Manager of World of Code [Discord Server](http://discord.gg/program)

[^1]: Approximate value rounding from 27,741, as well as including privated content. "Lines of code" exclude comments.
[^2]: Several privated repositories exist and will remain privated until further notice or until the end of that work.
[^3]: All repositories are Copyright (c) 2022 Jgouken. Follow "LICENSE" file within the respective repository.
