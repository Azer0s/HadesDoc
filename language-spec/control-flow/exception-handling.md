# Exception handling

## Exceptions in Hades

In Hades, every object can be an exception. There is a collection of standard exceptions \(in `std:exceptions`\) but nothing prevents you from throwing any object as an exception. This comes in quite handy when you want to handle multiple exceptions with very different error sources. 

## `try-catch` block

If you want to catch all exceptions, use the `default` keyword. 

### Example

```javascript
with client from mssql:client
with console from std:io
with file from std:io

var object connection is client("Data Source=ServerName;Initial Catalog=DatabaseName;User ID=UserName;Password=Password")
    
try
    connection->open:
    console->out:"Connection opened!"
    connection->close:
catch(SqlException e) //here, an SqlException is caught
    console->out:"SqlException was caught!"
catch(default e) //in the case that any other exception was raised, this block is invoked
    console->out:"An unknown exception was caught!"
end

try
    file->read("1.txt")
catch(default e)
    //ignored
end

try
    var f = file("2.txt")
catch(FileNotFoundException e)
    console->out("File {} not found!"->format(e->file))
end
```

## `raise` statement

The raise statement raises an exception. Since any object can be an exception, the variable/statement with which the raise statement is invoked has to be an object.

### Example

```swift
with exceptions from std:exceptions

func equals(object a, object b)
    if(a == null)
        raise exceptions->ArgumentNullException("{} is null"->format(nameof(a)))
    else if(b equals null)
        raise exceptions->ArgumentNullException("{} is null"->format(nameof(b))
    end
    
    put a == b
end
```



