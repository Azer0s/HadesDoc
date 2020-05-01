# Basic Syntax

## Hello world

```javascript
with console from std:io
console.out("Hello world")
```

## Pipelines

```javascript
with list fixed from std:collections
with console from std:io

var fruits = list.of({"Apple", "Banana", "Mango", "Kiwi", "Avocado"})

fruits
|> map(??, {x => x.toLower()})
|> filter({x => x.startsWith("a")})
//if ?? is not in the parameters, the method is inserted as the first parameter
|> forEach(??, {x => console.out(x)})
```

## Function guards

```swift
with console fixed from std:io

func myFunction(a int) requires a < 10
    console.out("a is smaller than 10")
end

func myFunction(a int) requires a > 10
    console.out("a is greater than 10")
end

myFunction(5) // a is smaller than 10
myFunction(17) // a is greater than 10
```

## Actors

```swift
with msg from std:io
with sleep from std:time

func ping()
    receive(m)
        {:ping, data} => {_ =>
            sleep.seconds(1)
            send(data, :pong)
        }
    end
    ping()
end

func pong()
    receive(m)
        {:pong, data} => {_ =>
            sleep.seconds(1)
            send(data, :ping)
        }
    end
    pong()
end

var pingPid = spawn({_ => ping()}
var pongPid = spawn({_ => pong()}

send(pingPid, {:ping, pongPid})
```

## Fibonacci sequence

```javascript
with console from std:io

func fib(n)
    if((n is 0) or (n is 1))
        put n
    end
    
    put fib(n-1) + fib(n-2)
end

fib(10) |> console.out
```

### Lambdas

```javascript
with console from std:io

var hello = { a => console.out("Hello " + a) }
hello("Foo")

var bye = { a string => console.out("Bye " + a) }
bye("Bar")

var cheers lambda::(string)->none = { a => console.out("Cheers " + a) }
```

