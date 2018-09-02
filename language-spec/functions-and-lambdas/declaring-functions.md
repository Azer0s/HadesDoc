# Declaring functions

## Declaring a function

### With static types

### With dynamic types

### With varargs

## Function attributes

### Access modifiers

### Fixed function

Fixed functions are like static function in Java or C\#. One can only declare fixed functions in classes, because in scripts or mixed files, every function which is outside a class is accessible.

### Using function guards

## Overriding functions

### Overriding built-in functions and operators

### Overriding inherited functions

## Nested functions

## Default values

When a function that has default values is being used, the sequence of the parameters which don't have default values stays the same as an invocation without overriding these defaults.

```swift
func functionWithDefaultValues(a,b=1,c,d="d",e,f=true)
end

functionWithDefaultValues(b=2, d="D", "This is 'a'", "This is 'c'", f=false, "This is 'e'") 
```

## Functions and lambdas

### Internal representation of functions

### Assigning a function to a lambda

