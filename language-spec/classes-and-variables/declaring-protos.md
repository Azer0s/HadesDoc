# Declaring protos

## Import statements

Protos are usually created when importing libraries or external code. 

## Instantiable protos

Classes and structs are imported as protos. The constructor of a class or struct is therefore an instantiable proto.

## Non-instantiable protos

Every other proto \(fixed classes, libraries\) are not instantiable. You can call methods and instantiate classes on non-instantiable protos.

```javascript
with math from std:math

var res = math.sqrt(16) //call a function on the proto

var velocity = math.Function("10x²+5x+3") //instantiate an object from the proto
var position = fn.integrate()
```

## Manually declaring protos

### Protos as variables

One can declare variables with the datatype `proto`. This is useful to create aliases for protos or pass protos to functions.

