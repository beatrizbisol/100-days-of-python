# Day 6 - Beginner - Python Functions & Karel

## Content

### Functions

A **function** is a named block of code you can **reuse**. Python already gives you functions such as `print()`, `len()`, and `input()`. On Day 6 you start **creating your own**.

**Define** the function with `def` (the recipe). **Call** it by writing its name with `()` (cook from the recipe).

```python
def my_function():
    print("Hello")
    print("Bye")

my_function()
```

- `def` starts the definition.
- `my_function` is the name. Use `snake_case`.
- `()` is where inputs (parameters) would go. Empty `()` means “no extra information needed.”
- The colon `:` starts the body. Indented lines belong to the function.
- Nothing in the function runs until you **call** it: `my_function()`.

Defining without calling is like writing a recipe and never cooking. Calling without defining causes a **NameError**.

Built-in vs yours:

```python
print("Hello")      # built-in: Python already knows this
my_function()       # yours: only works after the def above
```

### Indentation

Same rule as `if` and `for`: after `:`, indent the lines that belong to the function. Un-indent when the function is finished.

```python
def my_function():
    print("This is inside the function")

print("This is outside the function")
```

### `while` loops

A `for` loop repeats **for each item** in a list (or each number in a `range`). A **`while` loop** repeats **as long as a condition is True**.

```python
while <something is true>:
    # do this
    # keep doing this
```

Example — keep going until a counter hits zero:

```python
def jump():
    print("Jump")

hurdles_left = 6
while hurdles_left > 0:
    jump()
    hurdles_left -= 1
```

- Check the condition **before** each round.
- If the condition never becomes `False`, the loop never stops — an **infinite loop**. Always change something inside the loop (or the world) so the condition can fail.
- Use `for` when you know how many times (or you have a list). Use `while` when you only know **when to stop** (“until the flag is reached”).

```python
# for: you already know the sequence
for n in range(1, 6):
    print(n)

# while: keep going until a condition is false
n = 1
while n < 6:
    print(n)
    n += 1
```
