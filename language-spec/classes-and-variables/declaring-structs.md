# Declaring structs

## Declaring a struct

A struct consists of the identifier `struct`, the name of the struct and the variables inside the struct, which can either be mutable or read-only. Variables in structs do not support initial values because the constructor is autogenerated and all parameters are required. A struct can be declared in functions, classes and outside of any block scope.

### Example

```swift
struct Person
    let string firstname
    var string lastname
    let birthday
    var nationality
end

Person("John", "Doe", Date(01,01,1970), "Scottish")
```

