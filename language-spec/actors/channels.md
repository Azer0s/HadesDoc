# Channels

Hades also offers Go like channels via `std:sync`. This is useful for operations where one needs to sync two actors. Different from Go, in Hades channels can be used to connect multiple actors together. Every actor can send and every actor can receive \(except if specified otherwise\). One can send everything over a channel. Internally, the channel itself is an independent actor that manages member PIDs and messages. 

### Example - Send, async receive

This is the default setting. Here, everyone receives every message async.

```swift
with Channel from std:sync
with console from std:io

var chan = Channel()

func worker(worker, channel)
    while(true)
        //channel.get() is blocking
        //channel.get() is also a fixed function that has state in the receiving process
        var text = channel.get()
        console.out(text)
    end
end

var worker1 = spawn({_ => worker(1, chan)})
var worker2 = spawn({_ => worker(2, chan)})

//disable sending for other actors
chan.onlyReceive()
//...except for us
chan.allowSend(self())

//since the channel is just a wrapper around the send function,
//one need to manually register the pid to the channel
chan.register(worker1) 
chan.register(worker2)

//Channel just overrides the shift operator
//One could also just do chan.send("Hello")
chan << "Hello"
chan << "World"

console.in() //block

/*
Output:
Hello
Hello
World
World
*/
```

### Example - First come, first serve \(FCFS\) channel

```swift
with Channel from std:sync
with console from std:io

var chan = Channel(mode=:fcfs)

func worker(worker, channel)
    while(true)
        var text = channel.get() //channel.get is blocking
        console.out("Worker " + worker + ":" + text)
    end
end

var worker1 = spawn({_ => worker(1, chan)})
var worker2 = spawn({_ => worker(2, chan)})

chan.register(worker1) 
chan.register(worker2)

chan << "Hello"
chan << "World"
chan << "Foo"
chan << "Bar"

console.in()
```

### Example - Send to all, wait

Here, the channel waits until everyone received the message to exit the blocking `channel.get` call. 

```swift
with Channel from std:sync
with console from std:io

var chan = Channel(mode=:all_wait)

func worker(worker, channel)
    channel.get()
    console.out("Worker " + worker + " received the message")    
end

var worker1 = spawn({_ => worker(1, chan)})
var worker2 = spawn({_ => worker(2, chan)})
var worker3 = spawn({_ => worker(3, chan)})

chan.register([worker1, worker2, worker3])

chan << :hello
//Workers would print to stdout at the same time

console.in()
```

### Example - Send to all, balance

This will load balance between multiple actors.

```swift
with Channel from std:sync
with console from std:io

var chan = Channel(mode=:all_balance)

func worker(worker, channel)
    while(true)
        console.out("Worker " + worker + " " + channel.get())    
    end
end

var worker1 = spawn({_ => worker(1, chan)})
var worker2 = spawn({_ => worker(2, chan)})
var worker3 = spawn({_ => worker(3, chan)})

chan.register([worker1, worker2, worker3])

chan << :hello //Output: Worker 1 :hello
chan << :hello //Output: Worker 2 :hello
chan << :hello //Output: Worker 3 :hello
chan << :hello //Output: Worker 1 :hello

console.in()
```



