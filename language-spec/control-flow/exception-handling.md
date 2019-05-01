# Exception handling

Exceptions in Hades

In Hades, everything can be an exception. There is a collection of standard exceptions \(in `std:exceptions`\) but nothing prevents you from throwing any object as an exception. This comes in quite handy when you want to handle multiple exceptions with very different error sources. 

## `try-catch-else` block

If you want to catch all exceptions, don't specify a type in the catch block. 

### Example

```javascript
with client from mssql:client
with server from std:http
with console from std:io
with file from std:io

var object connection = client("Data Source=ServerName;Initial Catalog=DatabaseName;User ID=UserName;Password=Password")
    
try
    connection->open()
    console->out("Connection opened!")
    connection->close()
catch(object::SqlException e) //here, an SqlException is caught
    console->out("SqlException was caught!")
catch(e) //in the case that any other exception was raised, this block is invoked
    console->out("An unknown exception was caught!")
end

try
    file->read("1.txt")
catch(e)
    //ignored
end

try
    var f = file("2.txt")
catch(object::FileNotFoundException e)
    console->out("File {} not found!"->format(e->file))
end

let srv = server(port=8080)
srv->get("/:path", {req, res => 
    let path = req->param["path"]
    try
        if (file->exists(path))
            let f = file->open(path)
            res->send(f->read())
        else
            raise 404
        end
    catch(int status)
        res->status(status)
    else
        res->status(200)
    end
})

srv->start()
```

Code in an `else` block after a `try-catch` will be executed if the execution didn't fail.

### Example

```javascript
with console from std:io
var number

try
    number = int(console->in())
catch(e)
    console->out("Could not parse number")
else
    console->out("Number is {}"->format(number))
end
```

## `raise` statement

The raise statement raises an exception. 

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



