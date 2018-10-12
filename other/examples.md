# Examples

## Fibonacci

### fib.hd

{% tabs %}
{% tab title="With a function" %}
```swift
func calculate(n)
    if((n equals 0) or (n equals 1))
        put n
    end
    
    put fib(n-1) + fib(n-2)
end
```
{% endtab %}

{% tab title="With a lambda" %}
```javascript
var calculate = { x => (x == 0) or (x == 1) ? x : calculate(x-1) + calculate(x-2) }
```
{% endtab %}
{% endtabs %}

### main.hd

```javascript
with fib from fib.hd
with console from std:io
with Int fixed from std:int

fib->calculate:parse(value=console->in(),raise=false,defaultValue=0)
```

## 99 bottles of beer

### main.hd

```javascript
with math from std:math

for(var i in math->range(99,3))
    out:"{} bottles of beer on the wall, {} bottles of beer\nTake one down and pass it around, {} bottles of beer on the wall."->format(i,i,i-1)
end

out("""
1 bottle of beer on the wall, 1 bottle of beer.
Take one down and pass it around, no more bottles of beer on the wall.
No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall.
""")
```

## Factorial

### main.hd

```javascript
with console from std:io

var factorial = { x => x >= 1 ? x * factorial(x-1) : 1 }
console->out:factorial(6)
```

