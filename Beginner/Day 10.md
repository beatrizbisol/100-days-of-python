# Day 10 - Beginner - Functions with Outputs

## Content

Until now, functions either printed something or changed a value you passed in. Day 10 functions **return** a result you can save in a variable and use later.

### Functions with outputs

`return` sends a value **out** of the function, back to the line that called it.

```python
def my_function():
    result = 3 * 2
    return result

output = my_function()
print(output)  # 6
```

You can return the expression directly:

```python
def my_function():
    return 3 * 2
```

- `print()` **shows** a value on the screen. The program cannot reuse it as data.
- `return` **gives the value back**. You can store it: `n = my_function()`.
- After `return`, the function **stops**. Lines below `return` in that function do not run.

### Title case example

A function can take a string, build a new string, and return it:

```python
def format_name(f_name, l_name):
    formated_f_name = f_name.title()
    formated_l_name = l_name.title()
    return f"{formated_f_name} {formated_l_name}"

print(format_name("angela", "YU"))  # Angela Yu
```

`.title()` capitalises the first letter of each word. Combining that with `return` and an f-string is the same idea as Day 8, but the result is **data**, not only a print.

### Multiple return values

You can have more than one `return`. Use `if` to decide which one runs. The others are skipped.

```python
def format_name(f_name, l_name):
    if f_name == "" or l_name == "":
        return "You didn't provide valid inputs."
    formated_f_name = f_name.title()
    formated_l_name = l_name.title()
    return f"{formated_f_name} {formated_l_name}"
```

Empty inputs hit the first `return` and never reach `.title()`.

### Docstrings

A string in **triple quotes** right under `def` documents what the function does. It is not printed unless you ask for help.

```python
def format_name(f_name, l_name):
    """Take a first and last name and format it to return the title case version of the name."""
    formated_f_name = f_name.title()
    formated_l_name = l_name.title()
    return f"{formated_f_name} {formated_l_name}"
```

### Calculator (the Day 10 project)

The project is a calculator: ask for a number, an operation (`+`, `-`, `*`, `/`), and another number. Each operation can be its own function that **returns** the result. Store the operations in a **dictionary** (`"+": add`) and call `operations[symbol](n1, n2)`.

A `while` loop lets the user keep calculating with the previous result, or start a new calculation.

The working calculator can go in an exercise section when the code runs in PyCharm.

## Leap Year

### Exercise

Write a program that returns `True` or `False` whether a given year is a leap year.

A normal year has 365 days; leap years have 366, with an extra day in February.

This is how you work out whether a particular year is a leap year:

- on every year that is divisible by 4 with no remainder
- except every year that is evenly divisible by 100 with no remainder
- unless the year is also divisible by 400 with no remainder

e.g. The year 2000:

- 2000 ÷ 4 = 500 (Leap)
- 2000 ÷ 100 = 20 (Not Leap)
- 2000 ÷ 400 = 5 (Leap!)

So the year 2000 is a leap year.

But the year 2100 is not a leap year because:

- 2100 ÷ 4 = 525 (Leap)
- 2100 ÷ 100 = 21 (Not Leap)
- 2100 ÷ 400 = 5.25 (Not Leap)

**Warning:** Your return should be a boolean and match the Example Output format exactly, including spelling and punctuation.

Example input 1: `2400` → example return 1: `True`

Example input 2: `1989` → example return 2: `False`

Udemy coding exercises do not have a console, so you cannot use `input()`. Call your function with hard-coded values:

```python
def is_leap_year(year):
    # your code here

is_leap_year(2024)
```

### Solution

Tested and run successfully in PyCharm.

```python
def is_leap_year(year):
    if year % 4 == 0:
        if year % 100 == 0:
            if year % 400 == 0:
                return True
            else:
                return False
        else:
            return True
    else:
        return False

print(is_leap_year(2024))
```
