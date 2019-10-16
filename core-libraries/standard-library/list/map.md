---
description: 'Maps keys to values, no fancy magic.'
---

# map

## Methods

| Method | Parameters | Return type | Is fixed? |
| :--- | :--- | :--- | :--- |
| `put` | `object, object` | `undefined` | ❌ |
| `get` | `object` | `object` | ❌ |
| `index` | `object, object` | `undefined` | ❌ |
| `index` | `object` | `object` | ❌ |

### Examples

```javascript
with map from std:collections

let pets = map()

pets.put("Joe", "Dog")
pets.get("Joe")

// is equivalent to

pets["Joe"] = "Dog"
pets["Joe"]
```

