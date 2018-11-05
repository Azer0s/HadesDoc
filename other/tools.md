# Tools

## Hades project initializer

The Hades project initializer pretty much does what the name implies. It initializes a Hades project, lets you choose a project template and lets you add packages through a CLI.

### Example

{% tabs %}
{% tab title="Create with organization name" %}
### Initialize the project

```bash
$ hades new demoproject.example.org
```

### The project structure will look like this

```text
project.json - Contains the project configuration, initial data (config, connection keys, etc...) and meta-data of libraries installed via Hermes.
libs/ - Source files of libraries
src/ - Upper most directory for source files
 org/ - Organization tld
  example/ - Organization name
   demoproject/ - Project name
     main.hd - Entrypoint
```
{% endtab %}

{% tab title="Create without organization name" %}
### Initialize the project

```bash
$ hades new demoproject
```

### The project structure will look like this

```text
project.json - Contains the project configuration, initial data (config, connection keys, etc...) and meta-data of libraries installed via Hermes.
libs/ - Source files of libraries
src/ - Upper most directory for source files
 demoproject/ - Project name
   main.hd - Entrypoint
```
{% endtab %}
{% endtabs %}

## Hermes

Hermes is the Hades package manager. Similar to maven or nuget, Hermes has a package file which contains a list of dependencies. Hermes doesn't have its own dedicated package server, but uses Github \(if not specified otherwise\) as a package server instead. The version of a package specified in the `project.json` file translates to the git branch.

### Examples

#### Add a package to your Hades project

```bash
$ hermes add hades/xml master
```

## project.json

A `project.json` file defines a Hades project. The `project.json` file contains meta-data of all packages installed through Hermes, initial data \(like configuration or connection keys\), information about the project itself and even a basic pipeline to execute commands/scripts before and after the execution of a Hades project.

```javascript
{
  "name" : "demoproject", // name of the project
  "version" : "0.1", // version of the project
  
  "config" : { // initial config/connectionkeys of the project
    "motd" : "Hello world",
    "logo" : "resources/logo.png",
    "default-lang" : "en-US",
    "db1" : "Server=localhost;Database=demo;User Id=demo;Password=myPassword;"
  },
  
  "before-exec" : [ // will be executed before the project starts up
    {
      "execute" : "script/bash",
      "target" : "install.sh"
    },
    {
      "execute" : "command",
      "target" : "kill $(lsof -t -i:8080)"
    }
  ],
  
  "after-exec" : [ // will be executed after the project has been killed
    {
      "execute" : "script/hades",
      "target" : "clean.hd"
    }
  ],
  
  "dependencies" : [ // dependencies installed via Hermes
    {
      "name" : "hades/web",
      "version" : "3.2.4",
      "from" : "github.com"
    },
    {
      "name" : "hades/json",
      "version" : "master",
      "from" : "github.com"
    },
    {
      "name" : "hades/xml",
      "version" : "master",
      "from" : "github.com"
    }
  ]
}
```

