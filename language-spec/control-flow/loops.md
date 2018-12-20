# Loops

## `for` loop

In Hades, there is no C-style count-controlled loop, but only a foreach loop which iterates over an array.

### Example

```javascript
with math fixed from std:math
with console from std:io

for(var int i in range(0,10) /*'range' returns an array with the number 0 to 10*/)
    console->out:i
end

let string[] fruits = {"Apple", "Banana", "Mango", "Kiwi"}

for(var fruit in fruits)
    console->out("{} is very healthy"->format(fruit))
end
```

If you don't need a variable, you can use an underscore instead of naming a variable or variable declaration.

```javascript
for(_ in range(0,10))
    console->out:""
end
```

## `while` loop

The `while` loop pretty much works like you'd expect. It loops as long as a given condition evaluates to `true`.

### Example

```javascript
with console from std:io
var c = 0

while(c not 10)
    console->out("c is {}"->format(c))
end
```

## `stop` and `skip` statements

The `stop` statement stops a loop.

### Example

```javascript
with console from std:io
var c = 0

while(true)
    if(c == 10)
        stop
    end
    
    console->out("c is {}"->format(c))
    c++
end
```

The `skip` statement skips over the current state of a loop. In `while` loops, this just skips execution of the code after the `skip` statement. In a `for` loop, this statement also skips to the next value of an array.

### Example

```javascript
with console from std:io

var c = 0

while(c not 10)
    if(c not 5)
        c++
        skip
    end
    
    console->out:"c is 5"
    c++
end

// Output: c is 5 

var fruits = {"Apple", "Banana", "Mango", "Kiwi"}

for(var fruit in fruits)
    if(fruit == "Banana")
        skip
    end
    
    console->out:fruit
end

/*
Output:
Apple
Mango
Kiwi
*/
```



