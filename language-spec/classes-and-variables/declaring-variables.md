# Declaring variables

## Local variables

A variable can have a type, be nullable, be dynamic and be an array.

### Mutable

Mutable variables are declared `var`. You can specify the type of a variable by appending it after `var`.

#### Example

```kotlin
var string a = "Hello, World!" //Immediate assignment
var b = "What's up?" //Type 'string' is inferred
var string c //Type 'string' is given, but variable is not assigned
var d //Type is inferred on first usage
var* e //Dynamic variable; can be anything, type can change
```

### Immutable 

Immutable variables are declared with `let`. You can specify the type of a variable by appending it after `let`.

#### Example

```javascript
let string a = "Hello, World!" //Immediate assignment
let b = "What's up?" //Type 'string' is inferred
let string c //Type 'string' is given, but variable is not assigned
let d //Type is inferred on first usage
```

### Dynamic

Dynamic variables can change their type at runtime. A dynamic variable is declared by appending `*`after `var`. An immutable variable can not be dynamic. 

#### Example

```swift
var* my_dynamic_var
```

### Nullable

You can make variables of simple datatypes nullable by appending `?` after the datatype. An immutable variable can not be nullable. Dynamic variables can also not be nullable as assigning null to a dynamic variable works out of the box \(it will make the variable an object\).

```swift
var int? count
var string? name
```

## Deconstruct assign 

One can deconstruct/match an object or a list and assign it to a variable.

```swift
var MyResult{err := err, result := result} = doSomething()
var MyResult{err: null, result := result} = doSomething() //throws an exception if err is not null

var {status, data} = doSomethingElse()
var {:ok, data} = doSomethingElse() //throws an exception if first element of list is not :ok
```

## Access modifiers

Access modifiers can control who has access to a specific variable.

```csharp
protected //Accessible from all inherited members
public  //Accessible over direct access
private //Not accessible from outside
```

## Non-local variables

### In a class

Variables in a class can have any access modifier. Since Hades has inheritance, variables in classes can also be protected.

#### Example

```swift
class Employee
    public let string firstname
    public let lastname
    private var int age = 18
    var string[] attributes //When no access modifier is given, the variable will have private access
end
```

### In a struct

Variables in a struct can not have an access modifier because in a struct, all variables are publicly accessible. Other than that, variable declaration in a struct is the same as anywhere else.

### In a script

Variables in a script can be private or public since scripts can be used by other Hades code. Variables in scripts can not be protected as scripts are unable to inherit.

## Access modifier annotate blocks

The access modifier annotate block can set the access specifier for multiple variables at a time. Access modifier blocks can only be used in classes and scripts.

An access modifier block is declared with `@modifier`. Access modifier blocks follow the same rule as non-local variables.

### Example

```swift
class Vehicle
    @public
        var string make
        var int speed
    end
    
    @protected
        var bool manned?
    end
end

@private
    var object connection
end
```

