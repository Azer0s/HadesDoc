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
var hello = { _ => console->out:"Hello, world!" }
hello()
```

