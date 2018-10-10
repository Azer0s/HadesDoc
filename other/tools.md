# Tools

## Hades project initializer

The Hades project initializer pretty much does what the name implies. It initializes a Hades project, lets you choose a project template and lets you add packages through a CLI.

### Example

{% tabs %}
{% tab title="Create with organization name" %}
### Initialize the project

```text
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
### Initialize a project

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

Hermes is the Hades package manager. Similar to maven or nuget, Hermes has a package file which contains a list of dependencies. Hermes doesn't have its own dedicated package server, but uses Github as a package server instead. The version of a package specified in the Hermes file translates to the git branch.

### Examples

#### Add a package to your Hades project

```text
$ hermes add hades/xml master
```

## project.json

```javascript
{
  "name" : "demoproject",
  "version" : "0.1",
  "before-exec" : [
    {
      "execute" : "script/bash",
      "target" : "install.sh"
    },
    {
      "execute" : "command",
      "target" : "kill $(lsof -t -i:8080)"
    }
  ]
  "after-exec" : [
    {
      "execute" : "script/hades",
      "target" : "clean.hd"
    }
  ]
  "dependencies" : [
    {
      "name" : "hades/web",
      "version" : "3.2.4"
    },
    {
      "name" : "hades/json",
      "version" : "master"
    },
    {
      "name" : "hades/xml",
      "version" : "master"
    }
  ]
}
```

