# Day 9 - Beginner - Dictionaries, Nesting and the Secret Auction

## Content

A **dictionary** is a data structure that stores data in **pairs**: a **key** and a **value**. A list is ordered by index (`[0]`, `[1]`). A dictionary is ordered by the key you choose (`"name"`, `"score"`).

### Creating a dictionary

Curly braces `{ }`. Each item is `key: value`, separated by commas.

```python
programming_dictionary = {
    "Bug": "An error in a program that prevents the program from running as expected.",
    "Function": "A piece of code that you can easily call over and over again."
}
```

- Keys are often **strings**. Values can be strings, numbers, lists, or even other dictionaries.
- Think of a real dictionary: the word is the key, the definition is the value.

### Retrieving items

Use the key in square brackets — not a number index.

```python
print(programming_dictionary["Bug"])
```

A key that does not exist raises a **KeyError**. Spelling and capital letters must match.

### Adding and modifying items

The same syntax **adds** a new pair or **overwrites** an existing key.

```python
programming_dictionary["Loop"] = "The action of doing something over and over again."
programming_dictionary["Bug"] = "A moth in your computer."
```

Wipe the whole dictionary with `programming_dictionary = {}`.

### Looping through a dictionary

A `for` loop over a dictionary gives you the **keys**. Use each key to get the value.

```python
for key in programming_dictionary:
    print(key)
    print(programming_dictionary[key])
```

### Nesting

You can put a **list** or another **dictionary** inside a dictionary. That is nesting (same idea as nested lists on Day 4).

```python
travel_log = {
    "France": ["Paris", "Lille", "Dijon"],
    "Germany": ["Stuttgart", "Berlin"],
}

# first city in France
print(travel_log["France"][0])  # Paris
```

A dictionary inside a dictionary:

```python
travel_log = {
    "France": {
        "cities_visited": ["Paris", "Lille", "Dijon"],
        "total_visits": 12,
    },
    "Germany": {
        "cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
        "total_visits": 5,
    },
}

print(travel_log["Germany"]["cities_visited"][2])  # Stuttgart
```

A list of dictionaries is also common:

```python
travel_log = [
    {"country": "France", "cities": ["Paris", "Lille"], "visits": 12},
    {"country": "Germany", "cities": ["Berlin"], "visits": 5},
]
```

### Secret auction (the Day 9 project)

The project is a silent bidding program: each person types a **name** and a **bid**. The next person should not see the previous bid (clear the screen / print empty lines). Store every bid in a dictionary (`name` → `bid`). When there are no more bidders, loop through the dictionary and find the **highest** bid.

Typical pieces:

1. An empty dictionary, e.g. `bids = {}`.
2. A `while` loop until nobody else wants to bid.
3. `bids[name] = bid` for each person.
4. After the loop, compare values and print the winner.

The working auction can go in an exercise section when the code runs in PyCharm.

## Grading Program

### Exercise

You have access to a database of `student_scores` in the format of a dictionary. The keys in `student_scores` are the names of the students and the values are their exam scores.

Write a program that converts their scores to grades.

By the end of your program, you should have a new dictionary called `student_grades` that should contain student names as keys and their assessed grades for values.

The final version of the `student_grades` dictionary will be checked.

**DO NOT** modify lines 1–7 to change the existing `student_scores` dictionary.

Scoring criteria:

- Scores 91–100: Grade = `"Outstanding"`
- Scores 81–90: Grade = `"Exceeds Expectations"`
- Scores 71–80: Grade = `"Acceptable"`
- Scores 70 or lower: Grade = `"Fail"`

### Solution

Tested and run successfully in PyCharm.

```python
student_scores = {
    'Harry': 88,
    'Ron': 78,
    'Hermione': 95,
    'Draco': 75,
    'Neville': 60
}

student_grades = {}

for key in student_scores:
    if student_scores[key] >= 91:
        student_grades[key] = "Outstanding"
    elif student_scores[key] >= 81:
        student_grades[key] = "Exceeds Expectations"
    elif student_scores[key] >= 71:
        student_grades[key] = "Acceptable"
    else:
        student_grades[key] = "Fail"

print(student_scores)
print(student_grades)
```
