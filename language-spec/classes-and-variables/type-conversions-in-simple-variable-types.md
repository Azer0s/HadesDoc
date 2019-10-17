# Type conversions in simple variable types

Every simple variable type supports type conversion by invoking the constructor of the type.

## int

When the conversion to an int fails, an exception is thrown.

### Example

```javascript
int("22") //is being converted to 22
int(1.5) //exception is thrown
int(true) //is being converted to 1
```

## string

The string constructor accepts every type except for protos. Objects and structs are converted into JSON, other simple types are just being converted into strings \(like with `toString`\).

### Example

```javascript
string(21) //returns "21"
string(true) //returns "true"
string(22.3) //returns "true"
```

## dec

When the conversion to a dec fails, an exception is thrown.

### Example

```javascript
dec("22") //returns 22.0
dec("1.5") //returns 1.5
dec(false) //returns 0.0
dec(10) //returns 10.0
```

## bool

When the conversion to a bool fails, an exception is thrown.

### Example

```javascript
bool(1) //returns true
bool("false") //returns false
bool(0.0) //returns false
bool("not a bool") //raises TypeConversionException
```

## atom

Under the hood, the conversion to an atom will use `toString`. The conversion to an atom will only fail if one tries to convert a non-simple datatype. 

### Example

```swift
atom(1) //returns :1
atom(true) //returns :true
atom("ok") //returns :ok
```

## pid

The only datatype that can be converted to a pid is an int. That is because the value of a pid is an  int.

