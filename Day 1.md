# Day 1 - Beginner - Working with variables in python to manage data

## Content

### `print()`

`print()` is a built-in Python **function**. It takes a value (the argument) and **displays it in the console**.

Syntax:

```python
print("Hello")
print("Hello" + " " + "Angela")
print("Hello\nWorld")
```

- The function name is `print`.
- Parentheses `()` **call** the function.
- What goes inside the parentheses is the **argument** — the value you want to print.
- Text (a string) goes in quotes: `"..."` or `'...'`.
- `+` joins strings together (**concatenation**).
- `\n` creates a **new line** inside a string.

You can pass more than one argument, separated by commas. Python prints each one with a space in between:

```python
print("Hello", "Angela")
```

### `len()`

`len()` is also a built-in function. It takes a string (or another sequence) and **returns the number of characters**.

Syntax:

```python
len("Angela")          # returns 6
print(len("Angela"))   # prints 6
print(len(input("What is your name?")))
```

- `len("Angela")` does **not** print by itself: it only calculates and **returns** the value `6`.
- To see the result in the console, combine it with `print()`: `print(len("Angela"))`.
- You can nest functions: `input()` asks for text, `len()` counts the characters, `print()` shows the number.

### Variables

A **variable** is a name that stores a value in memory so you can reuse it later.

```python
name = "Angela"
print(name)
name = "Jack"   # the old value is replaced
print(name)
```

- `=` is **not** the same as “equals” in math. In Python it means **assignment**: “store the value on the right in this name”.
- The right-hand side is evaluated first, then stored in the variable on the left.
- To **swap** the contents of two variables, use an extra variable (as in the glasses exercise):

```python
glass1 = "milk"
glass2 = "juice"
temp = glass1
glass1 = glass2
glass2 = temp
```

Without that temporary variable, one of the values would be lost on the first assignment.

### Naming (best practices)

Python is **case-sensitive**: `name` and `Name` are different variables.

Day 1 rules and habits:

- Use names that **describe the data**: `user_name` is better than `n` or `x`.
- Use **snake_case**: lowercase words separated by `_` (`user_name`, `glass_1`).
- Do not start with a number: `1name` is invalid; `name1` is valid.
- Avoid spaces: `user name` is invalid.
- Avoid Python reserved words (`print`, `len`, `input`, `if`, `for`, …).
- Stay consistent: if the project uses `user_name`, do not mix in `userName` in the same code.

```python
# bad
n = "Angela"
UserName = "Angela"

# better
user_name = "Angela"
```

## Printing Practice

### Exercise

Write a program that uses print statements to print the following recipe into the Output console. The text to print is already there, you just need to make it into code. Your code should print all five lines exactly the same as the example output below. Make sure that you don't change any of these existing text as everything, punctuation and casing all need to match!

### Solution

Tested and run successfully in PyCharm.

```python
print("1. Mix 500g of Flour, 10g Yeast and 300ml Water in a bowl.")
print("2. Knead the dough for 10 minutes.")
print("3. Add 3g of Salt.")
print("4. Leave to rise for 2 hours.")
print("5. Bake at 200 degrees C for 30 minutes.")
```

## Debugging Practice

### Exercise

Look at the code in the code editor. There are errors on all 5 lines of code. Fix the code so that it runs without errors.

Try to run the code and debug each line using the error messages and feedback.

Broken code:

```python
# Fix the code below 👇

print(Notes from Day 1")
 print("The print statement is used to output strings")
print("Strings are strings of characters"
priint("String Concatenation is done with the + sign")
print(("New lines can be created with a \ and the letter n")
```

### Solution

Tested and run successfully in PyCharm.

```python
print("Notes from Day 1")
print("The print statement is used to output strings")
print("Strings are strings of characters")
print("String Concatenation is done with the + sign")
print("New lines can be created with a \ and the letter n")
```

## Variables

### Exercise

We have 2 variables glass1 and glass2. glass1 contains milk and glass2 contains juice. Write 3 lines of code to switch the contents of the variables. You are not allowed to type the words "milk" or "juice". You are only allowed to use variables to solve this exercise.

### Solution

Tested and run successfully in PyCharm.

```python
glass1 = "milk"
glass2 = "juice"
glass = glass1
glass1 = glass2
glass2 = glass
```
