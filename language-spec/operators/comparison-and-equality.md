# Comparison and equality

In Hades, there are a few comparison operators that always return a `bool` result.

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

```javascript
1 == 2 //false
"2" equals "2" //true
```

And for inequality:

```javascript
1 not 2 //true
"2" != "2" //false
```

### Of different types

We can test different types for equality \(which will, by default, always evaluate to `false`\).

```javascript
314 == "pi" // false
123 equals "123" // false
```

And for inequality \(which will, by default, always evaluate to `true`\).

```javascript
314 not "pi" // true
123 != "123" // true
```

