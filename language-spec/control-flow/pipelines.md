# Pipelines

Pipelines in Hades are a neat way to write out nested methods.

```javascript
with list fixed from std:collections
with console from std:io

var fruits = list.of({"Apple", "Banana", "Mango", "Kiwi", "Avocado"})

fruits
|> map({x => x.toLower()})
|> filter({x => x.startsWith("a")})
|> forEach(??, {x => console.out(x)})

//As opposed to

forEach({x => console.out(x)}, filter({x => x.startsWith("a")}, map({x => x.toLower()}, fruits)))
//map(lambda, list), filter(lambda, list) and forEach(lambda, list) are static methods from the list class

//Or even

fruits.map({x => x.toLower()}).filter({x => x.startsWith("a")}).forEach({x => console.out(x)})
//map(lambda), filter(lambda) and forEach(lambda) are methods from the list class
```

## Source

In Hades, the source of a pipeline can be any variable or statement. The source is the input parameter for the next pipeline statement.

## Pipeline target with only one parameter

### Example

```javascript
{"Mango", "Avocado", "Orange", "Apple"}
|> sort
//is being converted to sort({"Mango", "Avocado", "Orange", "Apple"})
```

## Pipeline target with multiple parameters

### Example

```javascript
{"Mango", "Avocado", "Orange", "Apple"}
|> map(??, {x=>x.toLower()})

//is being converted to map({"Mango", "Avocado", "Orange", "Apple"}, {x=>x.toLower()})
```

## Pipelines in variable assignment

### Example

```javascript
var lowerList = {"Mango", "Avocado", "Orange", "Apple"}
                |> map(??, {x=>x.toLower()})
```

## List functions with pipelines

One can import the functions defined in list as fixed and use them in pipelines on lists.

```javascript
with list fixed from std:collections
with console from std:io

var fruits = list.of({"Apple", "Banana", "Mango", "Kiwi", "Avocado"})

fruits
|> map({x => x.toLower()})
|> filter({x => x.startsWith("a")})
|> forEach({x => console.out(x)})

/*
Output:
apple
avocado
*/
```

