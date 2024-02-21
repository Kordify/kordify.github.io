# Creating commands

Kordify provide a very simple API to create slash commands.

## `Command` class

You can create command by creating a new object inheriting `world.anhgelus.kordify.api.commands.Command`.
```Kotlin
package my.package

import world.anhgelus.kordify.api.commands.Command
import net.dv8tion.jda.api.events.interaction.command.SlashCommandInteractionEvent

object MyCommand : Command() {
    override val name = "my-command"
    override val description = "My own command"
    
    override fun handle(event: SlashCommandInteractionEvent) {
        //
    }
}
```

There are 3 overrides in this object.

`name` variable is the name of the command. (Here we will be able to call this command with `/my-name`.)

`description` variable is the description of the command.

`handle` is the method called when the command is used by a user.
You can get every important information in `event`.

## Adding options

You can add options to your command using the method `addOption(OptionData)` from 
`world.anhgelus.kordify.api.commands.Command`.
`net.dv8tion.jda.api.interactions.commands.build.OptionData` represents an option for slash commands. 
It comes from JDA and you can check the documentation about `OptionData` 
[here](https://jda.wiki/using-jda/interactions/#slash-commands).
```Kotlin
fun start() {
    MyCommand.addOption(
        OptionData(OptionType.STRING, "say", "What to say")
    )
}
```

## Registering the command

Now we can register the command.
We just have to call `register()` from somewhere, so let's do this from our method `start()`!
```Kotlin
fun start() {
    MyCommand.register()
}
```

> Remember, after registering a command, you cannot edit it easily!
{style="warning"}
