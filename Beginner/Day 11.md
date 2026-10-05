# Day 11 - Beginner - The Blackjack Capstone Project

## Content

Day 11 is a **project day**: you build a Blackjack (21) game. There is no new syntax to memorise first. You combine functions, lists, `if`, `while`, `random`, and `return`.

### The goal

Play a simplified Blackjack in the console:

1. Deal two cards to the player and two to the dealer (computer).
2. The player can **hit** (take another card) or **stand** (keep the current hand).
3. The dealer draws until their score is 17 or more.
4. Closest to 21 without going over wins. Over 21 is a **bust** and loses.

### Cards and scores

Store the deck as a **list** of values. Face cards count as 10. An Ace counts as 11, or as 1 if 11 would bust the hand.

```python
import random

cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]

def deal_card():
    """Return a random card from the deck."""
    return random.choice(cards)
```

A helper that **returns** the current score is useful (Day 10). If the list has an Ace (`11`) and the total is over 21, replace that Ace with `1`.

```python
def calculate_score(hand):
    """Take a list of cards and return the score."""
    if sum(hand) == 21 and len(hand) == 2:
        return 0  # Blackjack (a special flag)
    if 11 in hand and sum(hand) > 21:
        hand.remove(11)
        hand.append(1)
    return sum(hand)
```

`0` as a flag for Blackjack makes comparisons easier: if either side has `0`, that side already won.

### Game loop

Use a `while` loop while the game is not over:

- If the player or dealer already has Blackjack, or the player busts, stop.
- Otherwise ask: `"Type 'y' to get another card, type 'n' to pass: "`.
- After the player stands, the dealer draws while `calculate_score(dealer) < 17`.
- Compare scores and `print` the result (`Win`, `Lose`, `Draw`, `Blackjack`, `Bust`).

Offer to play again with another `while` around the whole game (`y`/`n`).

### Tips from the lesson

- Break the game into **functions** (`deal_card`, `calculate_score`, `compare`) instead of one long script.
- `sum()` on a list of numbers is allowed here.
- Clear the screen between rounds if you want (empty lines or a clear function), so the next hand feels like a new game.

The working Blackjack can go in an exercise section when the code runs in PyCharm.
