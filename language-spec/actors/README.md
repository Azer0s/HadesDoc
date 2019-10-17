# Actors

Hades implements the Actor model in a very lightweight way. Every process in Hades has a state and a message queue. In Hades, one can pass messages from process to process. Processes are referenced via PIDs.

More on the actor model [here](https://www.brianstorti.com/the-actor-model/#targetText=The%20actor%20model%20is%20a,this%20model%20is%20probably%20Erlang%20.).

![](../../.gitbook/assets/actors.svg)

One can create a new actor with the built-in `spawn` function.

### Example

```swift
with console from std:io
with WaitGroup from std:sync

var wg = WaitGroup()

spawn({_ =>
    wg.add()
    for(_ in 0|..|11)
        console.out("Hello from the actor!")
    end
    wg.done()
})

wg.wait()
```

