# Script file arguments

Script file arguments should be at the very top of the source file. They don't require a type specification, but can have one if you want the script execution to fail when an argument with the wrong type was given.

```javascript
with params from std:params

var address = params->getString(0)
var port = params->getInt(1)
var deamon = params->getBoolByName("d","deamon")

/*
so the execution call could look like:
hades server.hd localhost 8080 -d true
*/
```

