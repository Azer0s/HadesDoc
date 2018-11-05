# Pipelines

## Source

In Hades, the source of a pipeline can be any variable or statement. The source is the input parameter for the next pipeline statement.

## Pipeline target with only one parameter

```javascript
{"Mango", "Avocado", "Orange", "Apple"}
|> sort
//is being converted to sort({"Mango", "Avocado", "Orange", "Apple"})
```

## Pipeline target with multiple parameters

```javascript
{"Mango", "Avocado", "Orange", "Apple"}
|> map(??, {x=>x->toLower()})

//is being converted to map({"Mango", "Avocado", "Orange", "Apple"}, {x=>x->toLower()})
```

## Pipelines in variable assignment

```javascript
var lowerList = {"Mango", "Avocado", "Orange", "Apple"}
                |> map(??, {x=>x->toLower()})
```

