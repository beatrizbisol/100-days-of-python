# Day 4 - Beginner - Randomisation and Python Lists

## Content

### Pseudorandom number generators

Computers are not truly random. They are built from circuits and switches, so they follow instructions. Still, games and many programs need something that *feels* random. It would be boring if every move in a game was already decided.

Computer scientists built **pseudorandom number generators** (PRNGs) for this. The computer starts from a value (a seed) and runs a formula that produces a sequence that looks random. Python’s `random` module uses an algorithm called the [Mersenne Twister](https://en.wikipedia.org/wiki/Mersenne_Twister).

If you want a deeper (still friendly) explanation, Khan Academy has a short video: [How computers generate random numbers](https://www.youtube.com/watch?v=GtOt7EBNEwQ).

### The `random` module

Python keeps extra tools in **modules**. `random` is one of them. Docs: [https://docs.python.org/3/library/random.html](https://docs.python.org/3/library/random.html)

Import it once at the top of the file, then call the functions you need:

```python
import random
```

### Random whole numbers within a range

`randint(a, b)` returns a random **integer** from `a` to `b`, **including both ends**.

```python
import random

rand_num = random.randint(1, 10)
print(rand_num)  # any whole number from 1 to 10, inclusive
```

A coin toss is just two options:

```python
if random.randint(0, 1) == 0:
    print("Heads")
else:
    print("Tails")
```

### Modules in Python

You can split code into different `.py` files and **import** what you need. That keeps a project organised (modular).

Create a new file, for example `my_module.py`, put a variable or a function in it, then import it:

```python
# my_module.py
pi = 3.14159
```

```python
# main file
import my_module

print(my_module.pi)
```

- `import random` uses a module that already ships with Python.
- `import my_module` uses a file you created next to your program.

### Random floats

`random.random()` returns a float from **0.0 (included)** up to **1.0 (not included)**:

```python
import random

rand_num_0_to_1 = random.random()
print(rand_num_0_to_1)
```

```text
0.0 <= random.random() < 1.0
```

Multiply to stretch the range. `random.random() * 5` gives a number from `0.0` up to (but not including) `5.0`.

`random.uniform(a, b)` picks a random float between `a` and `b`. Because of how floats are stored, the upper bound **might** be included:

```python
import random

random_float = random.uniform(1, 10)
print(random_float)  # a float between 1 and 10
```

```text
a <= random.uniform(a, b) <= b
```

- Use `random.random()` when you want the upper end **excluded** (typical: 0.0 ≤ n < 1.0).
- Use `random.uniform(a, b)` when both ends of the range are acceptable.
- Use `random.randint(a, b)` when you need a **whole** number and both ends must be possible.

### Lists

A **list** is a **data structure**: a way to store **several values together**, in order, under one name.

Without a list, related items would each need their own variable (`state1`, `state2`, `state3`…). That does not scale. A list holds the whole collection so you can pick, count, or pick at random from one place.

**Format:** square brackets `[ ]`, items separated by commas.

```python
fruits = ["Cherry", "Apple", "Pear"]

states_of_america = ["Delaware", "Pennsylvania", "New Jersey", "Georgia", "Connecticut", "Massachusetts", "Maryland", "South Carolina", "New Hampshire", "Virginia", "New York", "North Carolina", "Rhode Island", "Vermont", "Kentucky", "Tennessee", "Ohio", "Louisiana", "Indiana", "Mississippi", "Illinois", "Alabama", "Maine", "Missouri", "Arkansas", "Michigan", "Florida", "Texas", "Iowa", "Wisconsin", "California", "Minnesota", "Oregon", "Kansas", "West Virginia", "Nevada", "Nebraska", "Colorado", "North Dakota", "South Dakota", "Montana", "Washington", "Idaho", "Wyoming", "Utah", "Oklahoma", "New Mexico", "Arizona", "Alaska", "Hawaii"]
```

- The list is the box. The values inside are the **items**.
- Order **matters**. `"Delaware"` is first because it is stored first.
- Items can be strings, numbers, booleans, or even other lists.

Lists are **mutable**: you can change an item, add one, or remove one without creating a whole new list.

Official docs: [Python list data structures](https://docs.python.org/3/tutorial/datastructures.html)

#### Accessing items

Write the list name, then square brackets with the **index** of the item you want.

```python
states_of_america[0]  # "Delaware"
```

In programming, counting starts at **0**, not 1: `0, 1, 2, 3` — not `1, 2, 3, 4`.

```python
fruits = ["Cherry", "Apple", "Pear"]
print(fruits[0])  # Cherry
print(fruits[1])  # Apple
print(fruits[2])  # Pear
```

#### Negative indices

Count from the **end** with a negative integer. `-1` is always the last item.

```python
fruits = ["Cherry", "Apple", "Pear"]
print(fruits[-1])  # Pear
print(fruits[-2])  # Apple
```

#### Modifying items

The same `list[index]` syntax can **replace** an item.

```python
fruits = ["Cherry", "Apple", "Pear"]
fruits[0] = "Orange"
# fruits is now ["Orange", "Apple", "Pear"]
```

#### Adding items

`append()` puts a new item at the **end** of the list.

```python
fruits = ["Cherry", "Apple", "Pear"]
fruits.append("Orange")
# fruits is now ["Cherry", "Apple", "Pear", "Orange"]
```

- `append()` takes one value.
- Other list methods (extend, insert, remove, pop, …) are in the [documentation](https://docs.python.org/3/tutorial/datastructures.html).

#### Length of a list

`len()` returns how many items are in a list (or how many characters are in a string). Docs: [`len()`](https://docs.python.org/3/library/functions.html#len)

```python
fruits = ["Cherry", "Apple", "Pear"]
print(len(fruits))  # 3
```

The last valid index is always `len(list) - 1`, because counting starts at 0. For three items, the indices are `0`, `1`, and `2`.

#### IndexError

An **IndexError** happens when you ask for a position that does not exist in the list.

```python
fruits = ["Cherry", "Apple", "Pear"]
print(fruits[3])  # IndexError: list index out of range
```

- There is no item 3. The list only has indices 0–2.
- This often happens if you write `list[len(list)]` instead of `list[len(list) - 1]`.
- The error message “list index out of range” means: that slot is outside the list.

#### Nested lists

A list can hold other lists. That is a **nested list** (also called a **2D list**): a list of lists.

```python
fruits = ["Cherry", "Apple", "Pear"]
veg = ["Cucumber", "Kale", "Spinnach"]
fruits_and_veg = [fruits, veg]
# [["Cherry", "Apple", "Pear"], ["Cucumber", "Kale", "Spinnach"]]
```

You can picture it as two rows:

```text
["Cherry", "Apple", "Pear"]
["Cucumber", "Kale", "Spinnach"]
```

- `fruits_and_veg[0]` is the whole fruits list.
- `fruits_and_veg[1]` is the whole veg list.
- `fruits_and_veg[0][1]` is `"Apple"` — first list, then item 1 inside it.
