# Reflection

## The `eval` function

The `eval` function exposed by `std:internals` might not be available in all implementations. To prevent usage, the [Hades Preprocessor](preprocessor-statements.md) exposes a variable \(`HAS_EVAL`\). The `eval` function returns whatever is returned by the content or `null`.

## The `std:internals` library

The `std:internals` library contains miscellaneous functions for reflection. Like the `eval` function, it also has a preprocessor variable \(`HAS_INTERNALS`\) to determine weather or not you can use it. Some implementations might implement the `std:internals` library but not `eval` and vice-versa.

