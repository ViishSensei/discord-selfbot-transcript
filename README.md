# Discord.js-selfbot-v13 Selfbot Transcripts

[![Discord](https://img.shields.io/discord/555474311637499955?label=discord)](https://discord.gg/viish)

Discord Selfbot Transcripts is a node.js module to generate nice looking HTML transcripts. Processes discord markdown like **bold**, _italics_, ~~strikethroughs~~, and more. Nicely formats attachments and embeds. Built in XSS protection, preventing users from inserting html tags.

**This module is designed to work with [discord.js-selfbot-v13](https://https://discordjs-self-v13.netlify.app/#/) v3.4.2.**

HTML Template stolen from [DiscordChatExporter](https://github.com/Tyrrrz/DiscordChatExporter).

## Example Output

![output](./src/assets/styles.png)

## Usage

### Example usage using the built in message fetcher.

```js
const discordTranscripts = require("discord-selfbot-transcripts");

const channel = message.channel; // or however you get your TextChannel

// Must be awaited
const attachment = await discordTranscripts.createTranscript(channel);

channel.send({
  files: [attachment],
});
```

### Or if you prefer, you can pass in your own messages.

```js
const discordTranscripts = require("discord-selfbot-transcripts");

const messages = someWayToGetMessages(); // Must be Collection<string, Message> or Message[]
const channel = someWayToGetChannel(); // Used for ticket name, guild icon, and guild name

// You do not need to await this
const attachment = discordTranscripts.generateFromMessages(messages, channel);

channel.send({
  files: [attachment],
});
```

## Configuration

Both methods of generating a transcript allow for an option object as the last parameter.

### Built in Message Fetcher

```js
const attachment = await createTranscript(channel, {
  limit: -1, // Max amount of messages to fetch.
  returnBuffer: false, // Return a buffer instead of a MessageAttachment
  fileName: "transcript.html", // Only valid with returnBuffer false. Name of attachment.
});
```

### Providing your own messages

```js
const attachment = await generateFromMessages(messages, channel, {
  returnBuffer: false, // Return a buffer instead of a MessageAttachment
  fileName: "transcript.html", // Only valid with returnBuffer false. Name of attachment.
});
```
