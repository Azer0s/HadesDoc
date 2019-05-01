# Bitwise operators

## Left shift

The left-shift operator causes the bits in the left value \(either a variable or a literal\)to be shifted to the left by the number of positions specified by the bits in the right value. 

### Example

```javascript
with console from std:io
var a = 20 << 2
console->out(a) //Output: 80
```

## Right shift

The right-shift operator causes the bits in the left value \(either a variable or a literal\)to be shifted to the right by the number of positions specified by the bits in the right value.

### Example

```javascript
with console from std:io
var a = 8 >> 2
console->out(a) //Output: 2
```

## Bitwise and

The result of the bitwise and \(denoted by `&`\) is 1 if the corresponding bits of two operands are 1. If either bit of an operand is 0, the result of corresponding bit is evaluated to 0.

### Example

```javascript
with console from std:io

var a = 12 //00001100 in binary
var b = 25 //00011001 in binary

console->out(a&b) //Output: 8
```

## Bitwise or

 The result of the bitwise or \(denoted by `|`\) is 1 if at least one corresponding bit of two operands is 1.

### Example

```javascript
with console from std:io

var a = 12
var b = 25

console->out(a|b) //Output: 29
```

## Bitwise xor

The result of the bitwise xor \(denoted by `^`\) is 1 if the corresponding bits of two operands are opposite.

### Example

```javascript
with console from std:io

var a = 12
var b = 25

console->out(a^b) //Output: 21
```

## One's complement

 The bitwise complement \(denoted by `~`\) changes 1 to 0 and 0 to 1.

### Example

```javascript
with console from std:io

var a = 35 //00100011 in binary

console->out(~a) //Output: 220
```



