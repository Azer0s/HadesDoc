# Preprocessor statements

## `set` statement

The set statement, sets a preprocessor variable to a value. The values of preprocessor variables are not bound to types. 

```csharp
%set VERSION 0.7.1%
%set APPLICATION_NAME My Application%
```

Some variables are set by the Hades interpreter.

| Variable | Content |
| :--- | :--- |
| OS | The operating system, a script is being ran on \(can be: NT, Mac, Linux, Other\) |
| OS\_VERSION | The version of the operating system as int \(417, 1803, 10136, etc...\) |
| HADES\_VERSION | The version of the Hades interpreter the script is being ran on as int |

## `if-else if-fi` statement

The `if-elif-fi` block has a couple special commands to compare values to each other.

| Command | Full name | Returns true if |
| :--- | :--- | :--- |
| `eq` | Equals | Variables are equal |
| `ne` | Not equals | Variables are not equal |
| `gt` | Greater than | First variable is greater than second variable |
| `lt` | Lower than | First variable is lower than second variable |
| `ge` | Greater or equals | First variable is greater or equal to second variable |
| `le` | Lower or equals | First variable is lower or equal to second variable |

```swift
with os from std:os
with console from std:io

var listCommand

%if eq OS Windows%
listCommand = "dir"
%else if eq OS Linux%
listCommand = "ls"
%else%
console->out("OS not recognized!")
os->exit(-1)
&fi%

%if ge OS_VERSION 1803%
os->exec("wslpath 'c:\users'")
%fi%

os->exec(listCommand)
```

## `import` statement

The import statement copies the content of the specified file and pastes it into the source code \(works recursively\).

### function.hd

```swift
func print(args a)
    for(var arg in a)
        console->out(arg)
    end
end
```

### classDef.hd

```swift
class printer
%import function.hd%
end
```

### main.hd

```javascript
with console from std:io

%import classDef.hd%

printer()->print("Hello","world")
```

### Result

**main.hd** is being converted to:

```javascript
with console from std:io

class printer
    func print(args a)
        for(var arg in a)
            console->out(arg)
        end
    end
end

printer()->print("Hello","world")
```

