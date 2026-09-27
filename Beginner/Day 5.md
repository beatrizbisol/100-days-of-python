# Day 5 - Beginner - Python Loops

## Content

### Loops

A **loop** tells the computer to **repeat** an action without you copying the same lines over and over.

Printing the numbers 1 through 100 by hand would mean a hundred `print()` lines — or typing every number yourself. A loop states a **rule**, and the computer follows that rule as many times as needed.

### `for` loop syntax

The most common loop in this lesson walks through a **list**, one item at a time:

```python
for <variable name of each item> in <a List>:
    <do something>
    <do something else>
```

Example:

```python
fruits = ["Apple", "Peach", "Pear"]

for fruit in fruits:
    print(fruit)
```

- `for` starts the loop.
- `fruit` is a **temporary variable**. On each round it holds the current item (`"Apple"`, then `"Peach"`, then `"Pear"`). You can name it almost anything (`item`, `fruit`, `n`); pick a name that matches the data.
- `in fruits` means: go through this list.
- The colon `:` ends the header. The indented lines are the **loop body** — they run once per item.

This prints:

```text
Apple
Peach
Pear
```

### Indentation

Every time you see `:`, the lines that **belong** to that statement must be indented (same idea as `if`/`else` on Day 3). Those lines are inside the loop. Lines at the original indent run **after** the loop finishes.

These two programs look similar but behave differently.

Inside the loop — `"Hello"` prints once **per** fruit (three times):

```python
fruits = ["Apple", "Peach", "Pear"]
for fruit in fruits:
    print(fruit)
    print("Hello")
```

```text
Apple
Hello
Peach
Hello
Pear
Hello
```

Outside the loop — `"Hello"` prints **once**, after every fruit has been printed:

```python
fruits = ["Apple", "Peach", "Pear"]
for fruit in fruits:
    print(fruit)
print("Hello")
```

```text
Apple
Peach
Pear
Hello
```

- Indent = “do this on every round.”
- No indent after the loop = “do this when the loop is done.”
- A missing indent after `for ... :` causes an **IndentationError**.

### `range()`

`range()` makes a sequence of **whole numbers** so a `for` loop can count, without you writing the list by hand.

```python
for number in range(1, 10):
    print(number)
```

This prints `1` through `9`. The second number is the **stop** — it is **not included**.

```python
range(1, 10)     # 1, 2, 3, 4, 5, 6, 7, 8, 9
range(1, 11)     # 1 through 10
range(1, 101)    # 1 through 100  (as in FizzBuzz)
```

You can add a third argument: the **step** (how much to jump each time).

```python
for number in range(1, 11, 3):
    print(number)
# 1, 4, 7, 10
```

- First argument: where to start (included).
- Second argument: where to stop (excluded). To include 100, use `range(1, 101)`.
- Third argument (optional): step. Default is `1`.
- `range()` is not a list. It is a number sequence the loop walks through. Wrap it in `list()` only if you need to print the whole sequence at once: `print(list(range(1, 5)))`.

## FizzBuzz

### Exercise

You are going to write a program that automatically prints the solution to the FizzBuzz game. These are the rules of the FizzBuzz game:

Your program should print each number from 1 to 100 in turn and include number 100.

But when the number is divisible by 3 then instead of printing the number it should print `"Fizz"`.

When the number is divisible by 5, then instead of printing the number it should print `"Buzz"`.

And if the number is divisible by both 3 and 5 e.g. 15 then instead of the number it should print `"FizzBuzz"`.

e.g. it might start off like this:

```text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
Buzz
11
Fizz
13
14
FizzBuzz
```

### Solution

Tested and run successfully in PyCharm.

```python
numbers = range(1, 101)
for number in numbers:
    if number % 3 == 0:
        if number % 5 == 0:
            print("FizzBuzz")
        else:
            print("Fizz")
    elif number % 5 == 0:
        print("Buzz")
    else:
        print(number)
```
