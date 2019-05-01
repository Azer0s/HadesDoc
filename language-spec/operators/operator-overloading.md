# Operator overloading

All operator in Hades can be overloaded. The syntax for this is similar to overloading an inherited function. Operator overloading in Hades always assumes a right operation so the base for the operation is always the parameter on the left.

### Example

```swift
with console from std:io

class Vector
    var x = 0
    var y = 0
    var z = 0
    
    func Vector(x,y,z)
        this->x = x
        this->y = y
        this->z = z
    end
    
    func! toString()
        put "{},{},{}"->format(x,y,z)
    end
    
    func! op+(v)
        if(v is int)
            put Vector(x+v,y+v,z+v)
        else if(v is Vector)
            put Vector(x + v->x, y + v->y, z + v->z)
        end
        
        put null
    end
end

var v1 = Vector(1,2,3)
var v2 = Vector(4,5,6)

var v3 = v1 + v2 //overloaded operator is called on v1
console->out(v3) //outputs: 5,7,9
```

