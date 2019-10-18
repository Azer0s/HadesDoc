# Message passing

As Hades implements the actor model, it also needs some way for concurrency between these actors.

The way I thought to be most elegant was Erlang/Elixir-style message passing. To do so, Hades provides a built-in method to send \(called `send`\) and a block to receive \(`receive`\) messages.

`send` takes a pid and any value to send something to a process. `receive` works similar to a match block in that it can also match on object/list level, but the supplied argument to `receive` actually tells Hades to put the received data \(no matter what it is\) in a variable with the name of whatever the name of the supplied argument is.

```swift
with console from std:io

var p = spawn({_ =>
    var data
    receive(m)
        _ => data = m
    end
    console.out(data)
})

send(p, "Hello")
```

  


