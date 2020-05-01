# Declaring lambdas

## Declaring a simple lambda

The **simple lambda** consists of only a single statement. It will automatically return the result of said statement without the need of the `put` keyword.

### Example

```javascript
var add = {x,y => x + y}
add(2,2) //this would return 4
```

## Declaring a complex lambda

A **complex lambda** contains multiple LOC and does require the use of the `put` keyword to return things.

### Example

```javascript
var pow = { x,y => 
    var result = 1
    
    while(y not 0)
        result *= x
        y--
    end
    
    put result //complex lambda needs a put statement
}

pow(4,2) //this would return 16
```

## Declaring a lambda without parameters

If no parameter is needed, an `_` is used as the parameter name, instead.

### Example

```javascript
with console from std:io
var hello = { _ => console.out:"Hello, world!" }
hello()
```

## Assigning a function to a lambda variable

One can assign a function to a lambda. If the function has function guards, they are being rewritten into a `match` block internally. This can be useful when passing a function to a method. 

### Example

```swift
with console from std:io

func myFunction(a int) requires a < 10
    console.out("a is smaller than 10")
end

func myFunction(a int)
    //This default function is called when every condition is false
    console.out("a is " + a)
end

var fn lambda::(int)->none = myFunction

fn(1)  //Output: a is smaller than 10
fn(50) //Output: a is 50
```

```swift
with console from std:io

func onInit()
    console.out("Component initialized!")
end

func onError(e)
    console.outError("There was an error: {}".format(e))
end

...

comp.init(onInit, onError)
```

