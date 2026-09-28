# Day 8 - Beginner - Function Parameters & Caesar Cipher

## Content

Day 6 functions had empty `()`. Day 8 functions **take inputs** so the same code can run with different values.

### Functions with inputs

A **parameter** is the name you put in `def` — a placeholder. An **argument** is the real value you pass when you **call** the function.

```python
def greet():
    print("Hello")
    print("How do you do?")
    print("Isn't the weather nice?")

greet()
```

With an input:

```python
def greet_with_name(name):
    print(f"Hello {name}")
    print(f"How do you do {name}?")

greet_with_name("Angela")
```

- In `def greet_with_name(name):`, `name` is the **parameter**.
- In `greet_with_name("Angela")`, `"Angela"` is the **argument**.
- Inside the function, use `name` as a variable. Each call can pass a different argument.

### More than one input

Separate parameters with commas. The order in the call must match the order in `def` unless you use keyword arguments.

```python
def greet_with(name, location):
    print(f"Hello {name}")
    print(f"What is it like in {location}?")

greet_with("Jack Bauer", "Nowhere")
```

### Positional vs keyword arguments

**Positional:** values line up by position. First argument → first parameter, second → second.

```python
greet_with("Jack Bauer", "Nowhere")
# name = "Jack Bauer", location = "Nowhere"
```

**Keyword:** you name each argument. Order no longer matters.

```python
greet_with(location="Nowhere", name="Jack Bauer")
```

- Mixing them is allowed if all positional arguments come **first**.
- A mismatch in order with positional arguments is a common bug: `greet_with("Nowhere", "Jack")` would greet “Nowhere”.

### Caesar cipher (the Day 8 project)

The project encodes and decodes a message by **shifting** each letter along the alphabet.

```text
alphabet:  a b c d e ...
shift 3:   d e f g h ...
```

`"hello"` with shift `5` becomes `"mjqqt"`. Decoding uses the same idea in reverse (or a negative shift).

Typical pieces:

1. An `alphabet` list of 26 letters.
2. A function that takes `text`, `shift`, and a direction (`encode` / `decode`).
3. A loop over each letter, find its index, add (or subtract) the shift, wrap around with modulo `26` so `z` + 1 becomes `a`.
4. Keep spaces and punctuation as they are (not in the alphabet).

Notes and the working cipher can go in an exercise section when the code runs in PyCharm.

## Life in Weeks

### Exercise

I was reading this article by Tim Urban — [Your Life in Weeks](https://waitbutwhy.com/2014/05/life-weeks.html) — and realised just how little time we actually have.

Create a function called `life_in_weeks()` using maths and f-Strings that tells us how many weeks we have left, if we live until 90 years old.

It will take your current age as the input and output a message with our time left in this format:

```text
You have x weeks left.
```

Where `x` is replaced with the actual calculated number of weeks the input age has left until age 90.

**Warning:** The function must be called `life_in_weeks` for the tests to pass. Also the output must have the same punctuation and spelling as the example. Including the full stop!

Example input: `56`

Example output:

```text
You have 1768 weeks left.
```

Udemy coding exercises do not have a console, so you cannot use `input()`. Call your function with hard-coded values:

```python
def life_in_weeks(age):
    # your code here

life_in_weeks(12)
```

### Solution

Tested and run successfully in PyCharm.

```python
def life_in_weeks(age):
    years_left = 90 - age
    weeks_left = years_left * 52
    print(f"You have {weeks_left} weeks left.")

life_in_weeks(32)
```

## Love Calculator

### Exercise

You are going to write a function called `calculate_love_score()` that tests the compatibility between two names. To work out the love score between two people:

1. Take both people's names and check for the number of times the letters in the word **TRUE** occur.
2. Then check for the number of times the letters in the word **LOVE** occur.
3. Then combine these numbers to make a 2-digit number and print it out.

Example: `name1 = "Angela Yu"`, `name2 = "Jack Bauer"`

- T occurs 0 times, R occurs 1 time, U occurs 2 times, E occurs 2 times → total **5**
- L occurs 1 time, O occurs 0 times, V occurs 0 times, E occurs 2 times → total **3**
- Love score = **53**

Example input:

```python
calculate_love_score("Kanye West", "Kim Kardashian")
```

Example output:

```text
42
```

Udemy coding exercises do not have a console, so you cannot use `input()`. Call your function with hard-coded values.

### Solution

Tested and run successfully in PyCharm.

```python
def calculate_love_score(name1, name2):
    names = (name1 + name2).lower()
    t = names.count("t")
    r = names.count("r")
    u = names.count("u")
    e = names.count("e")
    l = names.count("l")
    o = names.count("o")
    v = names.count("v")
    score_true = t + r + u + e
    score_love = l + o + v + e
    print(f"{score_true}{score_love}")

calculate_love_score(name1="Kanye West", name2="Kim Kardashian")
```
