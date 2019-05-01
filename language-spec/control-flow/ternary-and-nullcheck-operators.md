# Ternary and nullcheck operators

## Ternary operator `? :`

Hades supports inline if \(or ternary operator\) statements. They work as such:

```text
condition ? statementIfConditionIsTrue : statementIfConditionIsFalse
```

### Example

```swift
with math from std:math

func sinc(dec x)
    put x != 0.0 ? math->sin(x)/x : 1.0
end
```

## Null-conditional operator `::`

The null conditional operator checks if the left side of the operator evaluates to `null`. If it does, the statement on the right side of the operator is executed and returned.

### Example

```swift
with exceptions from std:exceptions
with console from std:io

var doStuff = { x =>
    x :: raise exceptions->ArgumentNullException("{} is null"->format(nameof(x)))
}

try
    doStuff(null)
catch(default e)
    console->out(e->message)
end

//Output: x is null

func add(a,b) requires (a :: false) and (b :: false)
    put a + b
end
```

