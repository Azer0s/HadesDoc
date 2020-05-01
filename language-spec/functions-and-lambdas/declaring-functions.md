# Declaring functions

## Declaring a function

In Hades, function declarations don't contain the return type of the functions. Neither do the datatypes of the input values have to be defined.

### S**tatically typed** parameters

A function which is defined with static types, can only be called with those lines. If a function definition for a function with the types specified in the function call does not exist, execution will fail. The return type of a function is declared with `->`. **Only if a function is fully typed, it can be JITed.**

#### Example

```swift
with console from std:io

func add(a int, b int) //can also be written as `func add(a b int)
    console.out("Adds two ints")
    put a + b
end

func add(a string, b string) -> string
    console.out("Concatenates two strings")
    put "{} {}".format(a,b)
end

add(2,2) //Output: Adds two ints
add("Hello","world") //Output: Concatenates two strings
add(1.5,1.5) //Execution fails
```

### Dynamically-**typed** parameters

This function can be used with every datatype.

#### Example

```swift
with console from std:io

func add(a,b)
    var result = a + b
    console.out(result)
    put result
end

add(2,2) //Output: 4
add("Hello ","world") //Output: Hello world
add(1.5,1.5) //Output: 3.0
```

### Varargs

Varargs allow for method invocation with multiple parameters which are treated as a single parameter array by the function. A function can only have one vararg parameter.

#### Example

```swift
with console from std:io

func sum(...a int)
    var result = 0

    for(var i in a)
        result += i
    end

    put result
end

func print(...a)
    for(var arg in a)
        console.out(arg)
    end
end

func print(...a, times int)
    for(var i in range(1,times))
        for(var arg in a)
            console.out(arg)
        end
    end
end

console.out(sum(1, 2, 3, 4, 5, 6, 7, 8, 9))
print("Hello", ",", "world")
print("Hello", "," ,"world", 5/*this is the 'times' parameter*/)
```

### Function guards

With function guards, an initial condition has to be fulfilled for the function to be called. If the condition is not fulfilled, another function \(ordered by declaration\) with the same name and different, or no, function guard is called.

#### Example

```swift
with console from std:io

func myFunction(a int) requires a < 10
    console.out("a is smaller than 10")
end

func myFunction(a int) requires a is 11
    console.out("a is 11")
end

func myFunction(a int) requires a > 11 and a < 21
    console.out("a is greater than 11 and smaller than 21")
end

func myFunction(a int)
    //This default function is called when every condition is false
    console.out("a is " + a)
end

myFunction(1)  //Output: a is smaller than 10
myFunction(11) //Output: a is 11
myFunction(15) //Output: a is greater than 11 and smaller than 21
myFunction(50) //Output: a is 50
```

### Function guards by match

In addition to the normal function guards, Hades also offers function guards by object/list match. To use this feature, one must first define the function.

```swift
with console from std:io

func doSomething(person);

func doSomething(person := Employee{department: "IT"})
    console.out("{} works in IT".format(person.firstname))
end

func doSomething(Employee{department: "Finance", firstname := firstname})
    console.out("{} works in Finance".format(firstname))
end

doSomething(Employee("John", "Finance")) //Output: John works in Finance
doSomething(Employee("Steve", "IT")) //Output: Steve works in IT
```

```swift
with console from std:io

func getStatus(status);

func getStatus(status := :ok)
    console.out("Everything went well")    
end

func getStatus(:error)
    console.out("An error occured")    
end

func getStatus(status)
    console.out("Unrecognized status code")
end

getStatus(:ok) //Output: Everything went well
getStatus(:foo) //Output: Unrecognized status code
```

```swift
with console from std:io

func onReceive(e);

func onReceive(e := {:ok, message})
    console.out("Received {}".format(message))
end

func onReceive({:error, _})
    console.out("Error while receiving message")
end
```

### Nested functions

As with normal function declarations, nested functions can either explicitly name a type, or not:

#### Example

```swift
with math as m from std:math

func doMath(a int)
    func root(b int)
        put m.sqrt(b)
    end

    func square(b)
        put b * b
    end

    put square(a) + root(a)
end
```

### Access modifiers

Functions can have access modifiers. If they do, they follow the same rules as variables. See [Non-local Variables](../classes-and-variables/declaring-variables.md#non-local-variables).

### Fixed function

Fixed functions are like static function in Java or C\#. One can only declare fixed functions in classes, because in scripts or mixed files, every function which is outside a class is accessible.

## Overriding functions

One can override functions \(both built-in, as well as inherited\) by appending `!` to the `func` statement. Some internal functions are not overridable because of the way they're implemented. These functions are `type`, `nameof`, `send` and `self`.

#### Example

```swift
with assert from std:testing

class Car
    ...
    func! toString() -> string
        put "My custom string"
    end
end

assert.equal(Car().toString(), "My custom string")
assert.equal("{}".format(Car()), "My custom string")
```

## Default values

When a function that has default values is being used, the sequence of the parameters which don't have default values stays the same as an invocation without overriding these defaults.

#### Example

```swift
func functionWithDefaultValues(a,b=1,c,d="d",e,f=true)
    ...
end

functionWithDefaultValues(b=2, d="D", "This is 'a'", "This is 'c'", f=false, "This is 'e'") 
```

