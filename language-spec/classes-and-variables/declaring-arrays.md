# Declaring arrays

## Declaring one-dimensional arrays

A one dimensional fixed array is created either via an array literal or via appending `[]` to the `var/let` keyword or the type of the variable with the size or \* \(for an infinite array\) between the brackets.

```javascript
with console from std:io

var hello = {"Hello","world"}
console->out:hello [0] + hello [1] //Output: Hello world

var[2] fooBar
fooBar[0] = 10 //type of the array is infered here
fooBar[1] = 20

let string[*] text be console->in()->split(" ")
```

## Declaring multi-dimensional arrays

The syntax of creating multi-dimensional arrays is similar to that of creating one-dimensional arrays. But instead of a single size, you put the size of each dimension between the brackets seperated by a `.` .

```swift
var int[3.3] matrix = {{1,0,0},{0,1,0},{0,0,1}}

var names = {{"John", "Greg"}, {"Anna", "Susan"}}

let int[*] a = {{3,7,3,0},{0,2,-1,1},{5,4,3,2},{6,6,4,-1}}
```

