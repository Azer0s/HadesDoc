# Conditions

## `if` statement

The `if` statement executes statements based on some conditions.

```swift
if(a < 10)
    console->out:"a is smaller than 10"
else if(a equals 11)
    console->out:"a is 11"
else if(a > 11 and a < 21)
    console->out:"a is greater than 11 and smaller than 21"
else
    console->out:"a is " + a
end
```

An `if` block can contain multiple `else if` block.

```swift
if(condition)
    console->out:"yes"
else if(otherCondition)
    console->out:"maybe"
else if(otherOtherCondition)
    console->out:"maybe not"
else
    console->out:"no"
end
```

## `match` block

The match block is similar to a switch block in C languages. Match cases accept lambdas as actions. If multiple match cases evaluate to true, the first match case is invoked, except if specified otherwise \(with `to multiple`\).

```javascript
let fruit = "Apple"
var lambda action = { x => 
    console->print("Variable is of type: ")
    console->out:x
}

match(fruit) to
    "Apple" => { _ => console->out:"Apples are really tasty!"}
    fruit->type() equals "string" => action
end

//Output: Apples are really tasty!

match(fruit) to multiple
    "Apple" => { _ => console->out:"Apples are really tasty!"}
    fruit->type() equals "string" => action
end

/*
Output: 
Apples are really tasty!
Variable is of type: string
*/
```

