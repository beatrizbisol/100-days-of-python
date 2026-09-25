# Day 2 - Beginner - Understanding Data Types and How to manipulate strings

## Content

Python treats different kinds of data as different **types**. The type decides what you can do with a value (for example, you can add two numbers, but you cannot add a number to a string without converting it first).

Check a value’s type with `type()`:

```python
print(type("Hello"))  # <class 'str'>
print(type(123))      # <class 'int'>
print(type(3.14))     # <class 'float'>
print(type(True))     # <class 'bool'>
```

### Strings

A **string** (`str`) is text: a sequence of characters inside quotes.

```python
print("Hello")
print("123")          # this is text, not the number 123
print("Hello"[0])     # H  (subscripting: first character)
print("Hello"[-1])    # o  (last character)
```

- Use `"..."` or `'...'`.
- `+` concatenates strings: `"Hello" + " " + "Angela"`.
- Square brackets `[]` pull out one character by **index**. Counting starts at `0`.
- A negative index counts from the end: `-1` is the last character.
- Digits in quotes are still a string. `"123" + "456"` becomes `"123456"`, not `579`.

### Integers

An **integer** (`int`) is a whole number: no decimal point.

```python
print(123 + 456)      # 579
print(123_456_789)    # 123456789  (underscores are only for readability)
```

- You can add, subtract, multiply, and divide integers.
- Underscores `_` in a number are ignored by Python; they just make large numbers easier to read.

### Floats

A **float** (`float`) is a number with a decimal point (a floating-point number).

```python
print(3.14159)
print(3.0)
print(type(3.14))     # <class 'float'>
```

- `3` is an integer; `3.0` is a float.
- Division with `/` always produces a float in Python 3: `6 / 2` is `3.0`.

### Booleans

A **boolean** (`bool`) has only two values: `True` or `False`.

```python
print(True)
print(False)
print(type(True))     # <class 'bool'>
```

- Write `True` and `False` with a capital first letter. `true` or `false` will cause an error.
- Booleans are used later for conditions (yes/no questions in code), such as “is this number larger than 10?”.

### TypeError

A **TypeError** happens when you use a value in a way that its type does not allow.

A common Day 2 example: concatenating a string with an integer using `+`.

```python
len("Hello")          # 5 (an integer)
print("Hello" + 5)    # TypeError: can only concatenate str (not "int") to str
```

- `+` between two strings means concatenate.
- `+` between two numbers means add.
- Mixing them with `+` is not allowed, so Python stops and raises a **TypeError**.
- Read the error message: it usually names the types that do not match (`str` vs `int`).

`len()` itself does not print. If you write `print(len(12345))`, you also get a TypeError, because `len()` expects a string (or another sequence), not an integer.

### Type checking

**Type checking** means asking Python what type a value (or a variable) is. Use the `type()` function.

```python
print(type("Hello"))  # <class 'str'>
print(type(123))      # <class 'int'>
print(type(3.14))     # <class 'float'>
print(type(True))     # <class 'bool'>

user_input = input("Type something: ")
print(type(user_input))  # always <class 'str'> — input() returns a string
```

- The result looks like `<class 'str'>`. The useful part is the name: `str`, `int`, `float`, or `bool`.
- Check types when something fails or looks “wrong” (for example, `"123"` vs `123`).
- `input()` **always** returns a string, even if the user types digits.

### Type conversion

**Type conversion** (also called type casting) changes a value from one type to another with functions named after the types: `int()`, `float()`, `str()`, `bool()`.

```python
print(int("123") + int("456"))  # 579
print(str(123) + str(456))      # 123456
print(float("3.14"))            # 3.14
print(int(3.9))                 # 3  (the decimal part is dropped, not rounded)

num_char = len(input("What is your name? "))
print("Your name has " + str(num_char) + " characters.")
```

- `int("123")` turns the string `"123"` into the number `123`, so you can do math.
- `str(70)` turns the number `70` into `"70"`, so you can concatenate it into a sentence.
- `float("3.14")` turns text into a decimal number.
- Conversion only works when the value **makes sense** for the new type. `int("Hello")` raises a **ValueError**.
- Convert first, then use the value: do not mix types in the same `+` expression.

### Mathematical operators

These operators work on numbers (`int` and `float`).

```python
print(3 + 5)    # 8    addition
print(7 - 4)    # 3    subtraction
print(3 * 2)    # 6    multiplication
print(6 / 3)    # 2.0  division (always a float)
print(5 // 2)   # 2    floor division (drops the decimal, result is an int)
print(2 ** 3)   # 8    exponent (2 to the power of 3)
```

- `+` add, `-` subtract, `*` multiply.
- `/` divide. In Python 3 the result is **always a float**, even when it divides evenly (`6 / 3` is `2.0`, not `2`).
- `//` is **floor division**: it divides and throws away the remainder. `5 // 2` is `2`, not `2.5`.
- `**` is **exponent**: `2 ** 3` means 2 × 2 × 2.

Python follows **PEMDAS** when an expression has more than one operator. It is the same idea as “order of operations” in math:

1. **P**arentheses `()` — innermost first
2. **E**xponents `**`
3. **M**ultiplication `*` and **D**ivision `/` `//` — same priority, left to right
4. **A**ddition `+` and **S**ubtraction `-` — same priority, left to right

Multiplication and division are one level. Addition and subtraction are one level. When two operators share a level, Python goes **left to right**.

```python
print(3 * 3 + 3 / 3 - 3)    # 7.0
# 3 * 3 = 9
# 3 / 3 = 1.0
# 9 + 1.0 - 3 = 7.0

print(3 * (3 + 3) / 3 - 3)  # 3.0
# parentheses first: (3 + 3) = 6
# 3 * 6 / 3 - 3 = 3.0
```

Use parentheses when you want a different order than the default PEMDAS.

### Flooring a number

You can **floor** a number (remove all decimal places) using `int()`, which converts a floating-point number into an integer (a whole number).

```python
int(3.738492)  # becomes 3
```

- `int()` does **not** round. It just cuts off everything after the decimal point.
- `int(3.9)` is `3`, not `4`.

### Rounding a number

If you want to **round** a decimal the usual mathematical way — `.5` and above rounds up, below `.5` rounds down — use `round()`.

```python
round(3.738492)     # becomes 4
round(3.14159)      # becomes 3
round(3.14159, 2)   # becomes 3.14
```

- One argument: rounds to the nearest whole number.
- A second argument: how many decimal places to keep (`2` → two digits after the point).

### Assignment operators

An **assignment operator** updates a variable using its current value. The addition assignment operator `+=` adds the number on the right to the original value on the left, then stores the result back in the variable.

```python
score = 0
score += 1    # same as score = score + 1
score -= 1    # same as score = score - 1
score *= 2    # same as score = score * 2
score /= 2    # same as score = score / 2
```

- `+=` add and assign
- `-=` subtract and assign
- `*=` multiply and assign
- `/=` divide and assign

### f-Strings

An **f-string** inserts a variable or an expression into a string. Put `f` before the quotes and wrap the value in `{ }`.

```python
age = 12
print(f"I am {age} years old")
# output: I am 12 years old
```

- You do not need `str()` to mix numbers into the text.
- Anything inside `{ }` is evaluated, then placed in the string: `{age}`, `{age + 1}`, `{len(name)}`.

## BMI Calculator

### Exercise

The body mass index (BMI) is a measure used in medicine to see if someone is underweight or overweight. This is the formula used to calculate it:

bmi is equal to the person's weight divided by the person's height squared.

Convert this sentence into code on line 6.

### Solution

Tested and run successfully in PyCharm.

```python
height = 1.65 
weight = 84

# Write your code here.
# Calculate the bmi using weight and height.
bmi = weight / (height*height)

print(bmi)
```
