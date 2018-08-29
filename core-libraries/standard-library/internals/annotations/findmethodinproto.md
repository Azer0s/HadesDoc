---
description: Finds a method by annotation name in the given proto.
---

# findMethodInProto

## Parameters

| Type | Description |
| :--- | :--- |
| string | Name of the annotation |
| proto | The proto in which to search for the method |

## Return type

The method returns an `obj(annotationResult)`.

## Example

### myScript.hd

```swift
with console from std:io

#myMethod()
func method1(x)
    out:"Hello from method1 (invoked by {})"->format(x)
end
```

### main.hd

```swift
with annotations from std:internals
with myScript.hd as script

annotations->findMethodInProto("myMethod",script)->target("main.hd") //Output: Hello from method1 (invoked by main.hd)
```



