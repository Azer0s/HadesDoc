# Built-in functions

Every variable or constant \(simple or complex\) has built-in functions. They can be accessed like any other function even on a literal. Every built-in function can be [overriden](../functions-and-lambdas/declaring-functions.md#overriding-built-in-functions).

## nameof

`nameof` returns the name of a variable as a string. It can be used both with and without a parameter.

### With parameter

#### Example

```javascript
var a = 42
nameof(a) //returns 'a'; the nameof function of the `this` scope is called
```

### Without parameter

#### Example

```javascript
with console from std:io
console.nameof() //returns 'console'
```

## type

`type` returns the type of an object as a string.

### Example

```javascript
var a = 42
var b = "Hello world"
var c = true

a.type() //returns 'int'
b.type() //returns 'string'
c.type() //returns 'bool'
:ok.type() //returns 'atom'
```

## equals

`equals` compares two values and returns true if they're equal and false if they're not.

### Example

```javascript
with list from std:collections

1.equals(2) //returns false
"Hello".equals("Hello") //returns true

var foo = list.of({1,2,3,4,5})
foo.equals(list.of({1,2,3,4,5})) //returns true
```

## hash

For complex types \(except protos\), `hash` serializes the variable into a JSON, MD5-hashes the JSON string and returns it. For simple types, the MD5-hash of the string representation of the value is returned.

### Example

```javascript
var jd = User("John", "Doe")

jd.hash() //returns the MD5 of the JSONified User object

"Hello".hash() //returns the MD5 hash of "Hello"

9000.hash() //returns the MD5 hash of "9000"
```

## toString

`toString` returns the string representation of any variable or literal. Objects or structs are serialized into JSON while simple types are just being converted to strings.

### Example

```javascript
with list from std:collections

list.of({1,2,3,4,5}).toString()
/*
returns:
[1,2,3,4,5]
*/

class Car
    @public
        var name
        var models
    end
end

class Person
    let string name
    var int age
    var object[] cars
end

Person("John",30,
{
    Car("Ford",{"Fiesta", "Focus", "Mustang"}),
    Car("Fiat",{"500", "Panda"})
}).toString()

/*
returns:
{
    "name":"John",
    "age":30,
    "cars": [
        { "name":"Ford", "models":[ "Fiesta", "Focus", "Mustang" ] },
        { "name":"Fiat", "models":[ "500", "Panda" ] }
    ]
 }
*/
```

## send & self

`send` sends an object to the specified PID.

`self` returns the pid of the calling process.

### Example

```swift
with msg from std:io

class Counter
    private var int counter
    
    func loop()
        receive(m)
            msg{state: :increment} => counter++
            msg{state: :get, data := sender} => send(sender, counter)       
        end
    end
    
    func Counter()
        counter = 0
    end
end

var ctr = spawn({_ => Counter().loop()})
send(ctr, msg(:increment))
send(ctr, msg(:increment))
send(ctr, msg(:increment))

send(ctr, msg(:get, self()))

receive(m)
    _ => console.out(m) //prints 3
end
```

