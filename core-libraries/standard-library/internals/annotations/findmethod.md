---
description: Finds a method by annotation name.
---

# findMethod

## Parameters

| Type | Description |
| :--- | :--- |
| string | Name of the annotation |

## Return type

The method returns an `obj(annotationResult)`.

## Example

```swift
with console from std:io
with annotations from std:internals

#myMethod()
func method1()
    out:"Hello from method1"
end

annotations->findMethod("myMethod")->target() //Output: Hello from method1
```

