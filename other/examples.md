# Examples

## Fibonacci

### fib.hd

{% tabs %}
{% tab title="With a function" %}
```swift
func calculate(n)
    if((n is 0) or (n is 1))
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

## Perceptron

```swift
let dec[*] points = 
{
    {245, 1400},
    {312, 1600},
    {279, 1700},
    {308, 1875},
    {199, 1100},
    {219, 1550},
    {405, 2350},
    {324, 2450},
    {319, 1425},
    {255, 1700}
}

var weight = 10.0
var bias = 100.0
var lr = 0.000001

for(_ in range(1000000))
    for(var point in points)
        var prediction = point[0] * weight + bias
        var error = point[1] - prediction
        var gradient = point[0] * error * lr

        bias = bias + gradient
        weight = weight + weight * gradient
    end
end
```

## Factorial

### main.hd

```javascript
with console from std:io

var factorial = { x => x >= 1 ? x * factorial(x-1) : 1 }
console->out:factorial(6)
```

