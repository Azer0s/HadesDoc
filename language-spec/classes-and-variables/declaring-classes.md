# Declaring classes

## Declaring a class

### Example

```swift
with date from std:date

class Member
    private string var id
    
    @public
        var firstname
        var lastname
        var birthday
    end
    
    func Member(firstname, lastname, birthday, id)
        this->firstname = firstname
        this->lastname = lastname
        this->birthday = birthday
        this->id = id
    end
end

var member1 = Member("John", "Doe", Date(1,1,1970), "25aca5a7-cbfa-47ed-aeb5-f96cb1eb46ee")
//Create a new member instance
```

## Declaring a class without a constructor

A class without a constructor can still be instantiated. In the following example the class Calculator has two fixed methods which can be accessed without the class needing to be instantiated.

### Example

```swift
class Calculator
    fixed func add(a,b)
        put a + b
    end
    
    fixed func sub(a,b)
        put a - b
    end
end

var calc = Calculator //assign calc to the class proto
calc->add(2,2)
```

## Declaring a non-instantiable class

A class marked fixed can not be instantiated. All functions or structs declared in it, are fixed. It may contain a constructor \(but it can't be accessed without using reflection\). One can declare a non-fixed class inside a fixed class and vice-versa.

### Example

```swift
fixed class Calculator
    class Adder
        func add(a,b)
            put a + b
        end
    end
    
    func add(a,b)
        put Adder()->add(a,b)
    end
    
    func sub(a,b)
        put a - b
    end
end

Calculator->add(2,2)
Calculator->Adder()->add(2,2) //This works too because we declared a non-fixed (instantiable) class inside the fixed class
```

## Declaring a class within a class

### Example

```swift
with console fixed from std:io

class outerClass
    class innerClass
        func innerClass()
            out:"Hello from inner class"
        end
    end
end

var innerClass = outerClass->innerClass() //Outputs: Hello from inner class
```

## Declaring a class within a function

In Hades, it is possible to declare a class in a function. This function can only be instantiated \(provided it's an instantiable class\) in said function but can be returned and therefore used outside the function scope.

```swift
func getPerson(fn,ln)
    class Person
        @public
            var firstname
            var lastname
        end
        
        func Person(firstname,lastname)
            this->firstname = firstname
            this->lastname = lastname
        end
    end
    
    put Person(fn,ln)
end
```

## Working with inheritance

#### Base classes

```swift
with console fixed from std:io

class Mother
    func talk()
        out:"I am female"
    end
end

class Father
    func talk()
        out:"I am male"
    end
end
```

### Simple inheritance

#### Example

```swift
class Daughter < Mother
end

Daughter()->talk() //Outputs: I am female
```

### Multiple inheritance

When functions overlap each other when inheriting from multiple members, the order of the members to inherit from dictates which function is taken.

#### Example

```swift
class Child < Mother, Father
end

Child()->talk() //Outputs: I am male
/*
 Because the Father class was inherited after the Mother class,
 the talk function of Father overwrites the talk function in Mother
*/
```

## Overriding inherited members

To override a function, use the `func!` keyword. This overrides functions and functions groups with function guards.

### Example

```swift
with console fixed from 

class OverrideChild < Father
    func! talk()
        out:"I am a child"
    end
end

OverrideChild()->talk() //Outputs: I am a child
```



