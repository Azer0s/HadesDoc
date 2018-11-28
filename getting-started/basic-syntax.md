# Basic Syntax

## Hello world

```javascript
with console from std:io
console->out:"Hello world"
```

## Defining functions

In Hades, function declarations don't contain the return type of the functions. Neither do the datatypes of the input values have to be defined.

### Function with type-undefined parameters

This function can be used with every datatype.

```swift
func add(a,b)
    put a + b
end
```

### Function with type-defined parameters

This function can only be used with int.

```swift
func add(int a, int b)
    put a + b
end
```

### Varargs

Varargs allow for method invocation with multiple parameters which are treated as a single parameter array by the function. A function can only have one vararg parameter.

```swift
with console from std:io

func print(args a)
    for(var arg in a)
        console->out:arg
    end
end

func sum(args int a)
    var result = 0

    for(var i in a)
        result += i
    end

    put result
end

func printMultiple(args a, int times)
    for(var i in range(1,times))
        for(var arg in a)
            console->out:arg
        end
    end
end

print("Hello",",","world") //Output: Hello\n,\nworld
console->out:sum(1,2,3,4,5,6,7,8,9) //Output: 45
printMultiple("Hello",",","world",5/*this is the 'times' parameter*/) //Will output 'Hello\n,\nworld' 5 times
```

### Omitting braces

When a function only has one or no parameter and nothing follows after the function call, the braces can be omitted and the function can be called like so:

```swift
console->out:"Hello, World!" //✔️
connection->open: //✔️, but can also be written as connection->open()
fib:10 //✔️
fib:10 + fib:11 //This can also be written as fib(10 + fib(11))
add:10,10 //❌, because two parameters are given
```

### Function guards

With function guards, an initial condition has to be fulfilled for the function to be called. If the condition is not fulfilled, another function \(ordered by declaration\) with the same name and different, or no ,function guard is called.

```swift
with console from std:io

func myFunction(int a) requires a < 10
    console->out:"a is smaller than 10"
end

func myFunction(int a) requires a is 11
    console->out:"a is 11"
end

func myFunction(int a) requires a > 11 and a < 21
    console->out:"a is greater than 11 and smaller than 21"
end

func myFunction(int a)
    //This default function is called when every condition is false
    console->out:"a is " + a
end

myFunction:1  //Output: a is smaller than 10
myFunction:11 //Output: a is 11
myFunction:15 //Output: a is greater than 11 and smaller than 21
myFunction:50 //Output: a is 50
```

### Nested functions

As with normal function declarations, nested functions can either explicitly name a type, or not:

```swift
with math as m from std:math

func doMath(int a)
    func root(int b)
        put m->sqrt(b)
    end

    func square(b)
        put b * b
    end

    put square(a) + root(a)
end
```

## Defining variables

Variables can be assigned with the `=` operator.

### Read-only local variable

```javascript
let string a = "Hello, World!" //Immediate assignment
let b = "What's up?" //Type 'string' is inferred
let string c //Type 'string' is given, but variable is not assigned
let e //Type is inferred on first usage
```

### Mutable local variables

```kotlin
var string a = "Hello, World!" //Immediate assignment
var b = "What's up?" //Type 'string' is inferred
var string c //Type 'string' is given, but variable is not assigned
var e //Type is inferred on first usage
```

### Variables outside of functions

Variables outside of functions \(either in script files or class definitions\) can name an access modifier.

```csharp
global  //Accessible from everywhere
public  //Accessible over direct access
private //Not accessible from outside
```

When defining a global variable with the name of another global variable that already exists, the variable will not be defined and the assignment will not be executed.

#### Examples:

```swift
object[] global var EMPLOYEES

class employee
    public let string firstname = "John"
    public let lastname = "Doe"
    var int  private age = 18
    var string[] attributes //When no access modifier is given, the variable will have private access
end
```

## Comments

Hades supports end-of-line and block comments.

```c
//A simple end-of-line comment

/*
*A lot of text is best written
*into a block comment.
*/
```

## Control flow

### `if` statement

An if statement can contain n `else if` blocks and one `else` block.

```javascript
with console from std:io

if(a < 10)
    console->out:"a is smaller than 10"
else if(a is 11)
    console->out:"a is 11"
else if(a > 11 and a < 21)
    console->out:"a is greater than 11 and smaller than 21"
else
    console->out:"a is " + a
end
```

### `for` loop

In Hades, there is no C-style count-controlled loop, but only a foreach loop which iterates over an array.

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

### `while` loop

```javascript
with console from std:io
var c = 0

while(c not 10)
    console->out("c is {}"->format(c))
    c++
end
```

### Ternary and nullcheck operators

Hades supports conditional expressions and nullchecking with inline statements.

```javascript
with params from std:params
with exceptions from std:exceptions
with str from std:string
with Int from std:int

var a = params->get(0)
var b = params->get(1)

a :: raise exceptions->ArgumentNullException("{} is null"->format(nameof(a)))
b :: raise exceptions->ArgumentNullException("{} is null"->format(nameof(b)))

var number = a < b ? b : a
var numberFromString = Int->parse(value="This is not an integer", raise=false)
//one could also use int("This is not an integer")
var numberFromStringNullchecked = numberFromString :: 0
```

### Match

The match block is similar to a switch block in C languages. Match cases accept lambdas as actions. If multiple match cases evaluate to true, the first match case is invoked, except if specified otherwise \(with `to multiple`\).

```javascript
with console from std:io

let fruit = "Apple"
var lambda action = { _ => 
    console->print("Variable is of type string")
}

match(fruit) to
    "Apple" => { _ => console->out:"Apples are really tasty!"}
    fruit->type() is "string" => action
end

//Output: Apples are really tasty!

match(fruit) to multiple
    "Apple" => { _ => console->out:"Apples are really tasty!"}
    fruit->type() is "string" => action
end

/*
Output: 
Apples are really tasty!
Variable is of type string
*/
```

### Exception handling

```javascript
with client from mssql:client
with console from std:io

var object connection = client("Data Source=ServerName;Initial Catalog=DatabaseName;User ID=UserName;Password=Password")

try
    connection->open:
    console->out:"Connection open!"
    connection->close:
catch(SqlException e)
    console->out:"SqlException was caught!"
catch(default e)
    console->out:"An unknown exception was caught!"
end
```

## Instantiating classes

```javascript
with Calculator as calc from calc //loads from calc.hd

var calculator = calc() //no new keyword in Hades; instead the proto 'calc' is called
```

## Pipelines

Pipelines in Hades are a neat way to write out nested methods.

```javascript
with list fixed from std:collections
with console from std:io

var fruits = list->of({"Apple", "Banana", "Mango", "Kiwi", "Avocado"})

fruits
|> map({x => x->toLower()}, ??)
|> filter({x => x->startsWith("a")}, ??)
|> forEach({x => console->out:x}, ??)

//As opposed to

forEach({x => console->out:x}, filter({x => x->startsWith("a")}, map({x => x->toLower()}, fruits)))
//map(lambda, list), filter(lambda, list) and forEach(lambda, list) are static methods from the list class

//Or even

fruits->map({x => x->toLower()})->filter({x => x->startsWith("a")})->forEach({x => console->out:x})
//map(lambda), filter(lambda) and forEach(lambda) are methods from the list class
```

## Script file arguments

Script file arguments should be at the very top of the source file. They don't require a type specification, but can have one if you want the script execution to fail when an argument with the wrong type was given.

```javascript
with params from std:params

var address = params->getString(0)
var port = params->getInt(1)
var deamon = params->getBoolByName("d","deamon")

/*
so the execution call could look like:
hades server.hd localhost 8080 -d true
*/
```

