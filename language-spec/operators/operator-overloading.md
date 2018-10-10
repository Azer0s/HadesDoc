# Operator overloading

All operator in Hades can be overloaded. The syntax for this is similar to overloading an inherited function.

#### Example

```swift
class Couple
    @public
        var person1
        var person2
    end
    
    func Couple(p1,p2)
        person1 = p1
        person2 = p2
    end

end

class Person
    @public
        var string name
        var gender
    end
    
    func Person(name, gender)
        this->name = name
        this->gender = gender
    end
    
    func! op+(person1, person2) //Overloads the operator +
        put Couple(person1, person2)
    end
end

Person("John Doe", "M") + Person("Jane Doe", "F") //Returns a couple object
```

