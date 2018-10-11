# Types

## Complex data types

### object

An object is the native return type of a proto. It is created when a class is instantiated. A class can contain other classes, functions, variables and constructors. A class doesn't need a constructor to be instantiated. A class can also have fixed methods which can be accessed from the proto scope \(the class must not be instantiated for them to be called\).

**See:** [Declaring classes](../classes-and-variables/declaring-classes.md)

### struct

Structs can have variables, stored in them. They can not contain functions \(however, they can contain lambdas\) or a constructor. They're constructed sequentially \(constructor parameters are passed in in the same sequence the variables are defined in the struct\).

A struct is declared like a block. Every variable declared in a struct is public.

**See:** [Declaring structs](../classes-and-variables/declaring-structs.md)

### proto

A proto is the entry point of a class/struct/library. There are 2 types of protos: non-instantiable protos and instantiable protos. As the name implies, non-instantiable protos can not be instantiated, while instantiable protos can be.

The constructor of a class or a struct is a proto, so are types imported from a library.

**See:** [Declaring protos](../classes-and-variables/declaring-protos.md)

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



