# GenServer

GenServers are a concept directly taken from Elixir.

> A GenServer is a process like any other Elixir process and it can be used to keep state, execute code asynchronously and so on. The advantage of using a generic server process \(GenServer\) implemented using this module is that it will have a standard set of interface functions and include functionality for tracing and error reporting. It will also fit into a supervision tree.
>
> From the Elixir hexdocs

```swift
with GenServer from std:sync
with console from std:io

class Counter < GenServer
  func! init(state)
    put {:ok, state}
  end
  
  //If you want to use function matching, you have to explicetly state this
  func! call(msg, from, state);
  
  //We don't need ! since we already stated it above
  func call(msg := :get, _, state)
    put {:reply, state, state}
  end
  
  func! cast(msg, state);
  
  func cast(msg := {:increment, number}, state)
    put {:noreply, state + number}
  end
end

try
  var {:ok, ctrPid} = GenServer.start(Counter, 0)
  
  send(ctrPid, {:increment, 10})
  var nr = GenServer.call(ctrPid, :get)
  console.out(nr) //Output: 10
catch(e)
  //ignored
end
```

