# Compound Assignment Operators

A compound assignment operator executes an operation \(with the variable on the left being the left operand\) and then assigns the result to the variable on the left. There are no compound assignment operators for logical operations.

* **Multiply** and assign \(`*=`\)
* **Divide** and assign \(`/=`\)
* **Modulo** and assign \(`%=`\)
* **Add** and assign \(`+=`\)
* **Subtract** and assign \(`-=`\)
* **Left bit shift** and assign \(`<<=`\)
* **Right bit shift** and assign \(`>>=`\)
* **Bitwise and** and assign \(`&=`\)
* **Bitwise xor** and assign \(`^=`\)
* **Bitwise or** and assign \(`|=`\)

```javascript
var a = 12

a += 3 //a is 15
a %= 4 //a is 3
a <<= 8 //a is 768
a &= 524 //a is 512
a >>= 2 //a is 128
```



