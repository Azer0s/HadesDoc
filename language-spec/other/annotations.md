# Annotations

```swift
with annotations from std:internals
with console from std:io

#route("/")
func handleMain()
    put 200
end

var foundAnnotations = annotations->findMethods("route") //returns list of annotationResult
console->out:foundAnnotations->get(0)->value
```



