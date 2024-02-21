# Presentation

Kordify is a modular Discord bot empowered by plugins.

## Installation

To install Kordify, you have to 
1. Download the latest release on [GitHub](https://github.com/Kordify/Kordify/releases/latest)
2. Launch it with `java -jar FILE_NAME.jar`. It will create the `config.yml` file.
3. Edit the `config.yml` and add the token of your bot.
4. Relaunch Kordify with the same command and enjoy!

You can install plugins in the generated directory `plugins`.

## Configuration

The default `config.yml` is:

```yaml
token: ""
intents:
  - GUILD_MEMBERS
  - MESSAGE_CONTENTS
  - GUILD_PRESENCES
```

The `token` entry is the token of your bot. It is required to launch your bot.

The `intents` entry is a list of special intents used by your bot. The special intents are:
- `GUILD_MEMBERS`
- `MESSAGE_CONTENTS`
- `GUILD_PRESENCES`
- `GUILD_WEBHOOK`
- `GUILD_MESSAGE_TYPING`
- `DIRECT_MESSAGE_TYPING`

One of these intents can be required by some plugins.

## Plugins

Plugins are a little program which extend the power of your bot. Without any plugins, your bot has nothing. You have to 
install some plugins if you want to add new features to your bot.

Plugins are developed with our API.

To install a plugin, you just have to put the plugin inside your `plugins` directory. Kordify will load it automatically.
