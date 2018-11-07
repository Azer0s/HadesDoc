# Built-in functions

Every variable or constant \(simple or complex\) have built-in functions. They can be accessed like any other function. Even on a constant.

## nameof

`nameof` returns the name of a variable as a string. It can be used both with and without a parameter.

### With parameter

#### Example

```javascript
var a = 42
nameof(a) //returns 'a'; the nameof function of the `this` scope is called
```

### Without parameter

#### Example

```javascript
with console from std:io
console->nameof() //returns 'console'
```

## type

`type` returns the type of an object as a string.

#### Example

```javascript
var a = 42
var b = "Hello world"
var c = true

a->type() //returns 'int'
b->type() //returns 'string'
c->type() //returns 'bool'
```

## equals

`equals` compares two values and returns true if they're equal and false if they're not.

```javascript
with list from std:collections

1->equals(2) //returns false
"Hello"->equals("Hello") //returns true

var foo = list->of({1,2,3,4,5})
foo->equals(list->of({1,2,3,4,5})) //returns true
```

## hash

For complex types, `hash` serializes the variable into a JSON, MD5-hashes the JSON string and returns it. For simple types, the MD5-hash of the string representation of the value is returned.

```javascript
var jd = User("John", "Doe")

jd->hash() //returns the MD5 of the JSONified User object

"Hello"->hash() //returns the MD5 hash of "Hello"

9000->hash() //returns the MD5 hash of "9000"
```

