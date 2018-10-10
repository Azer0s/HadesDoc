# Annotations

Methods, classes, structs and class-variables can be annotated. Annotations do not have to be declared. Multiple annotations can be used.

```swift
with UserRepository //automatically imports from the first file that matches UserRepository\.hd (case insensitive)

#route("/")
func handleMain()
    put 200
end

#service
#constructor(true)
class UserService
    #injected(UserRepository)
    let userRepository
    
    func getById(id)
        put userRepository->findById(id)->orElse(null)
    end
end
```



