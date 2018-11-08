# Coding Conventions

## Source code organization

### Source file names

Hades files can either be script files \(non instantiable proto\), resource files \(with instantiable protos like classes or structs\) or mixed files \(both script and resource files\).

#### Script files

Script files, in Hades, are named after their function. If a script calculates something, call it `calculateSomething.hd`, if a script starts up a web server, call it `startWebServer.hd` and so on and so forth.

#### Resource files

Since there are no namespaces in Hades, the closest thing to a namespace structure is nesting classes and naming the source file after the highest, unique sub-namespace name.

So for a project that is organized like so:

```text
src/
 org/
  example/
   hades/
    main.hd
libs/
project.json
```

With a class called **connection** and a subclass called **client**, in the namespace **org.example.hades.weather** \(so the full class name of **client** would be **org.example.hades.weather.connection.client**\), the correct filename would be **weather.hd**.

```text
src/
 org/
  example/
   hades/
    main.hd
    weather.hd
libs/
project.json
```

And the import statement would look like this:

```javascript
with connection->client from weather.hd
```

#### Mixed files

Mixed files can be both script and resource files, so they can be executed as a script, but you can also load classes or structs from it. Mixed files use the same naming convention as script files.

So the import statements would look like so:

```javascript
with webStarter as starter from startWebServer.hd //Gets the webStarter class proto from startWebServer.hd
with startWebServer.hd as web sets address="localhost", port=8080 //This would just execute the script
```

### Project structure

For smaller projects, just put the source files in one folder.

For bigger projects, use the [Hades project initializer](../other/tools.md#hades-project-initializer), which creates a Hades project with the following structure \(example for a project with the organization name **example.org** and the project name **testing**\):

```text
project.json - Contains the project configuration, initial data (config, connection keys, etc...) and meta-data of libraries installed via Hermes.
libs/ - Source files of libraries
src/ - Upper most directory for source files
 org/ - Organization tld
  example/ - Organization name
   testing/ - Project name
     main.hd - Entrypoint
```

## Naming rules

Most things in Hades follow [Lower Camel Case](http://wiki.c2.com/?LowerCamelCase), except for global variables and preprocessor variables which are uppercase and underscore separated and native libraries which are named like so: `native library name : library file`. Classes, constructors and struct names follow [PascalCase](https://wiki.c2.com/?PascalCase) while proto names are in [Lower Camel Case](http://wiki.c2.com/?LowerCamelCase).

### Global variables

```csharp
//In a global annotation block
@global
    var string API_KEY = "1fea971e-55e3-4ce2-a5a4-6057388a7809"
    var SESSION_USER
    var SESSION_PASSWORD
    var SESSION_PASSWORD_HASH
end

//As standalone
let global string VERSION_NUMBER = "0.7.1"
global var int HIGH_SCORE = 0
```

### Preprocessor variables

```csharp
%set VERSION 0.7.1%
%set APPLICATION_NAME My Application%
```

### Functions \([Lower Camel Case](http://wiki.c2.com/?LowerCamelCase)\)

```swift
func addTwoNumbers(a,b)
    put a + b
end

class classWithFixedFunction
    fixed func addTwoNumbers(a,b)
        put a + b
    end
end
```

### Classes \([PascalCase](https://wiki.c2.com/?PascalCase)\)

```swift
class Person
    var int id

    @public
        var string firstname
        var string lastname
    end
end
```

### Structs \([PascalCase](https://wiki.c2.com/?PascalCase)\)

```csharp
struct Person
    var int id
    var string firstname
    var string lastname
end
```

### Protos \([Lower Camel Case](http://wiki.c2.com/?LowerCamelCase)\)

```javascript
with list from std:collections
```

### Native library names

```javascript
with list from std:collections
with car from nativeLib:domain
with button from gui:controls
```

## Formatting

### Lambdas

Lambdas that have more than one expression \(complex lambdas\) are formatted like Java methods \(the parameters on the first line\) and need a manual `put`:

```javascript
var pow = { x,y => 
    var result = 1

    while(y not 0)
        result *= x
        y--
    end

    put result
}

var add = {x,y => x + y} //Simple lambda, don't need a put statement
```

Same for match:

```javascript
var fruit = "Apple"

match(fruit) to multiple
    "Apple" => { _ =>
        console->out:"Apples are really tasty!"
        console->out:"I like apples!"
    }
    fruit->type() equals "string" => { _ => console->out:"Variable is a string"} //Simple lambda
end
```

### Pipelines

Pipelines don't have indentation. A pipeline statement uses the indentation of the pipeline source.

```swift
with list fixed from std:collections

func filterAndPrint(fruits, filterBy="a")
    list->of(fruits)
    |> map({x => x->toLower()}, ??)
    |> filter({x => x->startsWith(filterBy)}, ??)
    |> forEach({x => console->out:x}, ??)
end

{"Apple", "Banana", "Mango", "Kiwi", "Avocado"}
|> filterAndPrint //For methods with only one parameter, brackets can be omitted; results in filterAndPrint({"Apple", "Banana", "Mango", "Kiwi", "Avocado"})
```

### Tabs vs spaces

It is absolutely irrelevant whether you choose tabs or spaces for indentation. As long as you stay consistent and don't mix tabs and spaces, it doesn't matter.

## Miscellaneous

### Ignored catch block

If you choose not to handle a exception, mark the block as ignored with a comment.

```javascript
with console from std:io
with file from std:io

try
    file->read("hello.txt")
catch(default e)
    //ignored
end
```

