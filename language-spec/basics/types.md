# Types

## Complex data types

### object

### struct

Structs can have variables, stored in them. They can not contain functions \(however, they can contain lambdas\) or a constructor. They're constructed sequentially \(constructor parameters are passed in in the same sequence the variables are defined in the struct\).

A struct is declared like a block. Every variable declared in a struct is public.

**See:** [Declaring structs](../classes-and-variables/declaring-structs.md)

### proto

### lambda

A lambda is an anonymous function. In Hades, there are 2 types of lambdas: the simple lambda and the complex lambda.

Like a function, a lambda can contain other function, class or struct definitions which can not only be used inside the lambda, but can also be returned.

**See:** [Declaring lambdas](../functions-and-lambdas/declaring-lambdas.md)

## Simple data types

### int

### string

### dec

### bool

## Nullable simple data types

## Arrays

### One-dimensional array

### Multi-dimensional array

```javascript
with console from std:io

var a = {{"Hello",{"world"}},{" ","bar"}}
console->out:a[0.0] + a[1.0] + a[0.1.0] //Output: Hello world
```



