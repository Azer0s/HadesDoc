# findMethod

## Parameters

| Type | Description |
| :--- | :--- |
| string | Name of the annotation |

## Return type

The method returns an `object(annotationResult)`.

## Example

```swift
with console fixed from std:io
with annotations from std:internals

#myMethod()
func method1()
    out("Hello from method1")
end

annotations.findMethod("myMethod").target() //Output: Hello from method1
```

