# Types

## Complex data types

### object

An object is the native return type of a proto. It is created when a class is instantiated. A class can contain other classes, functions, variables and constructors. A class doesn't need a constructor to be instantiated. A class can also have fixed methods which can be accessed from the proto scope \(the class must not be instantiated for them to be called\).

**See:** [Declaring classes](../classes-and-variables/declaring-classes.md)

### struct

Structs can have variables, stored in them. They can not contain functions \(however, they can contain lambdas\) or user-defined constructors. They're constructed sequentially \(constructor parameters are passed in, in the same sequence the variables are defined in the struct\).

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

The int \(or integer\) datatype stores whole numbers. Its size can vary from 8 bit \(`int8`\) to 64 bit \(`int64`\) and can be signed or unsigned \(`uint8`, `uint64`\). The default `int` type is 32 bit.

### string

A string variable stores text. There's virtually no upper limit for the size of a string.

### float

The float stores a floating point number. Its size can vary from 32 bit \(`float32`\) to 64 bit \(`float64` or `double`\). The default `float` type is 32 bit.

### bool

The bool can store a single bit represented by the values true \(meaning 1\) or false \(meaning 0\).

### atom

An atom is a constant whose value is its name. They can be used to express certain operation states like `:ok` or  `:error`. Atoms may contain `-` and `_` but not `.`. 

An atom is declared like so `:name`.

### pid

A pid or process id is a reference to another thread. You can obtain the pid by either spawning a process or calling `self()`.

### Summary

| Datatype | Range | Default Value |
| :--- | :--- | :--- |
| uint8 | 0 to 255 | 0 |
| uint16 | 0 to 65,535 | 0 |
| uint32/uint | 0 to 4,294,967,295 | 0 |
| uint64 | 0 to 18,446,744,073,709,551,615 | 0 |
| int8 | -128 to 127 | 0 |
| int16 | -32,768 to 32,767 | 0 |
| int32/int | -2,147,483,648 to 2,147,483,647 | 0 |
| int64 | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 | 0 |
| string | Pseudo infinite | "" |
| float32/float | 1.2E-38 to 3.4E+38 | 0.0 |
| float64/double | 2.3E-308 to 1.7E+308 | 0.0 |
| bool | false or true | false |
| atom | Pseudo infinite | :\_ |
| pid | 0 to 4,294,967,295 | 0 |

Since every simple data type has a default value, per default you can not assign null to a variable with a simple datatype. If you want to make a variable of a simple data type nullable, you have to explicitly declare said variable as nullable. This can be done with appending a `?` after the data type of the variable. A constant variable cannot be nullable.

#### Examples

```swift
var a int? = null
var b string? = null
```

## Arrays

### One-dimensional array

In Hades an array can be declared as an array of a fixed size or as an infinite array. The maximum theoretical maximum length of an array is  2,146,435,071.

Infinite arrays have n dimensions, meaning they can also be used as a multi-dimensional array.

### Multi-dimensional array

Multi dimensional arrays are arrays of arrays. Just like normal arrays they can be declared with a fixed size.

**See:** [Declaring arrays](../classes-and-variables/declaring-arrays.md)



