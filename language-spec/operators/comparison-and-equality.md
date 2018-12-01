# Comparison and equality

## Comparison

We can compare values using C style comparison operators:

```javascript
less < than
lessThan <= orEqual
greater > than
greaterThan >= orEqual
```

## Equality

### Of same types

We can test two values for equality:

#### Example

```swift
1 == 2 //false
"2" is "2" //true
```

And for inequality:

#### Example

```swift
1 not 2 //true
"2" != "2" //false
```

### Of different types

We can test different types for equality \(which will, by default, always evaluate to `false`\).

#### Example

```swift
314 == "pi" // false
123 is "123" // false
```

And for inequality \(which will, by default, always evaluate to `true`\).

#### Example

```swift
314 not "pi" // true
123 != "123" // true
```

### Checking type

In Hades, the equality operator also works as a typecheck. You can check any value against a proto or type. The operation will return `true` if the value is an instance of said proto.

#### Example

```swift
123 == int
v is Vector
```

