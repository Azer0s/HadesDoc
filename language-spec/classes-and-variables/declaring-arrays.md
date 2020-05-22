# Declaring arrays

## Declaring one-dimensional arrays

A one dimensional fixed array is created either via an array literal or via appending `[]` to  the type of the variable with the size or `*`\(for an infinite array\) between the brackets. If no variable type is given, the type array is infered on first use and the variable will be an infinite array

### Example

```javascript
with console from std:io

var hello = {"Hello","world"} //type of the array is infered here, fooBar is now a string[2]
console.out(hello[0] + hello[1]) //Output: Hello world

var fooBar
fooBar[0] = 10 //type of the array is infered here, fooBar is now an int[*]
fooBar[1] = 20

var fib int[10] = {1,1,2,3,5,8,13,21,34,55}

var barFoo
barFoo[0] = null //type of the array is infered here, barFoo is now an object[*]

let text string[*] = console.in().split(" ")
```

## Declaring arrays with mixed types

An array of `*any` can contain data of multiple types. This means that the array can be used as a tuple. 

```javascript
var arr *any[2]
arr = {:ok, "Hello world"}

let result = {1, true, 20.231}
```

## Declaring multi-dimensional arrays

The syntax of creating multi-dimensional arrays is similar to that of creating one-dimensional arrays. But instead of a single size, you put the size of each dimension between the brackets seperated by a `,` .

### Example

```swift
var matrix int[3,3] = {{1,0,0},{0,1,0},{0,0,1}}

var names = {{"John", "Greg"}, {"Anna", "Susan"}} //type of the array is infered here, names is now a string[2.2]

let a int[*] = {{3,7,3,0},{0,2,-1,1},{5,4,3,2},{6,6,4,-1}}
```

## Arrays of nullable types

Making an array nullable is done in the same way as making a variable nullable: you put a `?` in front of the datatype or let the interpreter infer the array type.

### Example

```swift
var 3dArray int?[2,2,2] = {{{1,2},{3,null}},{{null,6},{7,8}}}

var strings = {null, "Hello","World"} //type of the array is infered here, strings is now a string?[3]
```

