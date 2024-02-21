# Installation

Currently, we do not provide an official maven repository.
To add Kordify to your dependencies, you can 
1. Get the official sources, compile them and publish the jar to your local maven repository ;
2. Download the official jar and it to your dependency like this:
```Groovy
dependencies {
    implementation(files("path/to/the/file.jar"))
}
```

## `plugin.yml`

Next you have to create a new resource called `plugin.yml`.
In this file, you will add every important information about your plugin.

A complete `plugin.yml` should look like this:
```yaml
main: world.anhgelus.kordify.Main
author: Anhgelus Morhtuuzh
version: 1.0
description: Plugin for Kordify
intents:
  - GUILD_MEMBERS
```

The `main` field is the path to your main file (we will speak about it later).

The `author` field tells us who is the author.

The `version` field tells us what is the version of this plugin.

The `description` field is a basic description of your plugin.

The `intents` list is a list of intents required by your plugin. This list is not required.

> If a required part is missing, Kordify will throw an `InvalidPluginException` with the reason `INVALID_PLUGIN_YML`.
{style=note}

## Main class

The main class is the class called by Kordify when it starts your plugin.
It has to be at the position indicated by the `main` field in your `plugin.yml`.

Your main class must inherit from `world.anhgelus.kordify.api.Plugin`.

It should look like this:
```Kotlin
package my.package

import world.anhgelus.kordify.api.Plugin
import world.anhgelus.kordify.common.utils.Logger

class MyPlugin : Plugin() {
    override val logger = object : Logger() {
        override val name = pluginName
    }
    
    override fun start() {
        //
    }
    
    override fun stop() {
        //
    }
}
```

So, in this class you have 3 overrides.

`logger` is a... logger. 
It's an object which inherit from `world.anhgelus.kordify.common.utils.Logger`.
The override variable is the name used by the logger.
Usually it's the plugin name (the plugin name is stored in `pluginName`).

The method `start()` is called when your plugin starts.
Your plugin starts when the event `ReadyEvent` is emitted by the websocket.

The method `stop()` is called when your plugin stops.
Your plugin stops after the shutdown of the bot.

We will look more deeply in method provided by `Plugin` later.
