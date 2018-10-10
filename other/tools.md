# Tools

## Hades project initializer

## Hermes

Hermes is the Hades package manager. Similar to maven or nuget, Hermes has a package file which contains a list of dependencies. Hermes doesn't have its own dedicated package server, but uses Github as a package server instead. The version of a package specified in the Hermes file translates to the git branch.

### Example

```javascript
{
  "name" : "demoproject",
  "version" : "0.1",
  "dependencies" : [
    {
      "name" : "hades/web",
      "version" : "3.2.4"
    },
    {
      "name" : "hades/json",
      "version" : "master"
    }
  ]
}
```

