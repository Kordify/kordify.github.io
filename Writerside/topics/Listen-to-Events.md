# Listen to Events

One of the most important part of the creation of a Discord bot is to listen to events.

## Listener

You have to create a new object which inherit from `net.dv8tion.jda.api.hooks.ListenerAdapter`.
You can override predefined methods to listen for an event.

For example, this object will receive the event emitted when a user send a message.
```Kotlin
package my.package

import net.dv8tion.jda.api.hooks.ListenerAdapter

object MyListener : ListenerAdapter() {
    override fun onMessageReceived(event: MessageReceivedEvent) {
        //
    }
}
```

But we have to register him.
To do this, we have to use the method `registerListener(ListenerAdapter)` on our instance of `Plugin`.
So let's register this object directly from the `start()` method:
```Kotlin
fun start() {
    registerListener(MyListener)
}
```

## Get registered listeners

All registered listeners are stored in the variable `listeners` on our instance of `Plugin`.

> Do not register directly your listener by adding it to `listeners`!
> It will not work!
{style="warning"}
