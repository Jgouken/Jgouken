# Jgouken
I'm a `Software Programmer`, celebrating **5 years** of Software Programming 🎉5️⃣🎉!
First things first, I'm fueling off of dedication and creativity and slowly growing my reputation as a Software Programmer. I started working with Discord Bots, wanting to learn website and game development for the betterment and interconnection of interests. I have a lot on my plate, but I learn quickly and effectively to ensure I produce the best material I can with the least amount of second-guessing. One day this name may land in the papers! 📰

- Applying to California Institute of Technology
- Learned **JavaScript**, **Swift**, **Java,** and **C-langs**.[^4]
- Learning **HMTL**, **CSS**, and **Python**.
- **Visual Studio Code** is my editor of choice.
- **GitHub** and **Replit** are my code-savers of choice.
- **Orange** is my color of choice.

# Works/Volunteers
All of the following are works of Discord.js bots going back to May 17th, 2020 with 34,000+[^1] lines of code in counting.
Work  | Rank | Description | Active
------------- | ------------- | ------------- | -------------
[Text-Based Game](https://github.com/jgouken/text-based-game) | Group Project | This is a discord.js variant of my original text-based game done with a few of my friends. This is the biggest solo project I've tackled thus far, but due to hosting issues, it may not continue for a while. | ✅
[The Introvert Advantage](https://github.com/jgouken/the-introvert-advantage) | School Project | This was done as an assignment. This is a [text-based game](https://the-introvert-advantage.jgouken.repl.co/) using HTML, CSS, and JavaScript. This project will be expanded significantly in the future. | ❌
[Bot-ez-a](https://github.com/Jgouken/BOT-ez-a) | Volunteer | Previously assisted aspiring developers create commands for their private server's needs. | ❌
[Make-A-Mand](https://github.com/Jgouken/MakeAMand) | Solo | Self-lead project to create helpful commands not seen in many other bots. Lead to nowhere. | ❌
[Discord.js Bot Handler](https://github.com/Jgouken/Discord.js-Basic-Bot-Handler) | Solo | For me and the public to use my code not often seen by others for many functionalities. | ❌
[TC-Phone](https://github.com/Jgouken/TC-Phone) | Solo | This was my add-on to Train Central; a "phone" for Discord users to use as their interface to this RPG world (such as an economy system). | ❌
[Train Central](https://github.com/Jgouken/Train-Central) | Solo | This was an RPG-like idea using Discord; a train would go around different "regions" and users would have to catch the train to view and go to these regions. | ❌
[Junk](https://github.com/Jgouken/Junk) | - | A dump of discarded files of mine lounging on my computer. | -
[Snake](https://github.com/Jgouken/snake) | Solo | My first HTML video game to show me the ropes. | ❌
[Calculator](https://github.com/Jgouken/calculator) | Solo | My first very simple HTML/CSS program. | ❌
[Matrix Development](https://github.com/MatrixDevelopment-GH) | Volunteer | Designed new processes and abilities that boosted the bot architecturally. | ❌
[Wyvern](https://wyvern.host/) ([Discord Bot](https://discordbotlist.com/bots/wyvern)) | Volunteer | As a lead developer, I've previously led new designs, creations, and commands that suited the bots' needs along with user-friendly capabilities. | ❌
[JgoChat](https://github.com/Jgouken/JgoChat) | Solo | A very old project to essentially create ChatGPT (before it was even created) didn't lead anywhere. | ❌

Active - If I'm currently working on or updating the project.

Not mentioned: Private or Discarded repositories.[^2] May or may not be active.

#### My Main discord.js index.js File (Outdated)

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
	if (command.data) {
		config.bot.sCommands.set(command.data.name, command);
		scmds.push(command.data)
	}
	// If not, it's just a slash command
}

async function start() {
	await rest.put(
		Routes.applicationGuildCommands(config.clientId, '...'),
		{ body: scmds.map(command => command.toJSON()) },
	).then(() => {console.log('Slash Commands Updated')}).catch(console.error);

	await listeners.execute(config.bot, config.db) // Puts "Listeners Executed" in the console

	await config.bot.login(config.TOKEN).then(() => { console.log(`Logged In`) })
}
start()
// Code put together within my Text-Based-Game repository.
// Not much code, right? I've allocated more of my time to reorganization, just so that I know exactly where what happens.
```
Feel free to copy my public code![^3]

# Personal Achievements
Participated in a Robotics Team and became sponsored by businesses such as Amazon, Tesla, and Gene Haas.

# Compliments

> "It's amazing to see how he wraps his brain around a problem at such a young age."
- [Tesla Nevada](https://www.tesla.com/gigafactory) Official/Recruiter
> "Your work, time, and dedication are exceedingly astounding for this [robotics] team."
- Senior Architect/Teacher[^5]
> "Your dedication is impressive."
- Manager of World of Code [Discord Server](http://discord.gg/program)

[^1]: Estimated values. Includes private content.
[^2]: Several private repositories exist and will remain private until further notice or until the end of that work.
[^3]: All repositories are Copyright (c) Jgouken. Follow the "LICENSE" file within the respective repository or, if it does not exist, follow Github's default MIT license.
[^4]: All of these I feel proficient at. Some cannot be found in any GitHub repository. C-langs include C, C+, C++, and C#.
[^5]: Registered Architectural official, Navy Military veteran, and influential person.
