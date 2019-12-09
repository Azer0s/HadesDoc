---
description: 'Maps keys to values, no fancy magic.'
---

# map

## Methods

| Method | Parameters | Return type | Is fixed? |
| :--- | :--- | :--- | :--- |
| `put` | `any, any` | `null` | ❌ |
| `get` | `any` | `any` | ❌ |
| `index` | `any, any` | `null` | ❌ |
| `index` | `any` | `any` | ❌ |

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

