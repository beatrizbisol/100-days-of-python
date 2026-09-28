# Day 7 - Beginner - Hangman

## Content

Day 7 is a **project day**: you build a Hangman game by combining what you already know — lists, `for`/`while`, `if`, `input()`, `random`, and functions.

### Break the problem into steps

Do not write the whole game at once. Split it into small jobs the computer can do in order:

1. Pick a random word from a list.
2. Show the player one blank `_` per letter.
3. Ask for a guess (one letter).
4. If the letter is in the word, reveal it in the right positions.
5. If it is not, lose a life.
6. Repeat until the word is complete (**win**) or lives run out (**lose**).

A flowchart of those steps is enough to start coding. Each box becomes a few lines.

### Choose a word

Reuse Day 4: a list of words and `random.choice()` (or `randint` plus an index).

```python
import random

word_list = ["aardvark", "baboon", "camel"]
chosen_word = random.choice(word_list)
```

### Display blanks

A second list can hold what the player sees. Start with `"_"` for every letter in `chosen_word`.

```python
placeholder = []
for letter in chosen_word:
    placeholder.append("_")

print(" ".join(placeholder))
```

`len(chosen_word)` tells you how many blanks you need. Updating `placeholder[i]` later is the same list-index idea as Day 4.

### Check a guess

Loop through the chosen word. If the current letter matches the guess, put that letter in the same position of `placeholder`.

```python
guess = input("Guess a letter: ").lower()

for i in range(len(chosen_word)):
    if chosen_word[i] == guess:
        placeholder[i] = guess
```

- Convert the guess with `.lower()` so `"A"` and `"a"` count as the same letter.
- One `for` can find **every** occurrence (two `a`s in `"aardvark"`).

### Lives and the game loop

Keep going **while** the player still has lives **and** there are still `"_"` left. That is a `while` loop (Day 6), not a `for` that runs a fixed number of times.

```python
lives = 6

while lives > 0 and "_" in placeholder:
    guess = input("Guess a letter: ").lower()
    # check the guess, update placeholder or lives
```

- Wrong guess: `lives -= 1`.
- Right guess: leave lives as they are; only update `placeholder`.
- After the loop: if no `"_"` remain, they won. If `lives == 0`, they lost. Print the chosen word so the player can see it.

You can store the Hangman stages (ASCII art) in a **list** and print `stages[lives]` after each turn. Fewer lives → a later drawing.
