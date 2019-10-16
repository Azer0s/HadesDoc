# Conditions

## `if` statement

The `if` statement executes statements based on some conditions.

### Example

```python
with console from std:io

if(a < 10)
    console.out("a is smaller than 10")
else if(a is 11)
    console.out("a is 11")
else if(a > 11 and a < 21)
    console.out("a is greater than 11 and smaller than 21")
else
    console.out("a is " + a)
end
```

An `if` block can contain multiple `else if` block.

### Example

```python
with console from std:io

if(condition)
    console.out("yes")
else if(otherCondition)
    console.out("maybe")
else if(otherOtherCondition)
    console.out("maybe not")
else
    console.out("no")
end
```

## `match` block

The match block is similar to a switch block in C languages. Match cases accept lambdas as actions. By default only the first block that matches is invoked. If the desired behavior is instead to invoke all matching blocks, use `match`.

### Example

```javascript
with console from std:io

let fruit = "Apple"
var lambda action = { _ => 
    console.print("Variable is of type string")
}

match all(fruit)
    "Apple" => console.out("Apples are really tasty!")
    fruit.type() is "string" => action
end

/*
Output: 
Apples are really tasty!
Variable is of type string
*/

match(fruit)
    "Apple" => { _ => console.out("Apples are really tasty!")}
    fruit.type() is "string" => action
end

//Output: Apples are really tasty!
```

The match block is also able to filter objects and lists.

### Example

```swift
with console from std:io

let person = Person("John", "Doe")
let list = {:ok, "Hello world"}

func doMatch(a)
    match(a)
        Person{firstName: "John"} =>
            console.out("Hello, John") //single operations can be written like so
        {:ok, msg} => console.out(msg)
    end
end

doMatch(person) //Output: Hello, John
doMatch(list) //Output: Hello world
```

