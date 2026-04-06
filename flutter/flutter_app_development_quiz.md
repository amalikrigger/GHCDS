# 🎮 Flutter: From Counter to Tic-Tac-Toe — Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

**Directions:** Answer each question to the best of your ability.

---

### Multiple Choice (circle one)

**1. What is a widget in Flutter?**

A) A type of phone

B) Any piece of the user interface — buttons, text, layouts, even the whole app

C) A programming language

D) A file that stores images

---

**2. What is the difference between a StatelessWidget and a StatefulWidget?**

A) StatelessWidget is for Android, StatefulWidget is for iPhone

B) StatelessWidget can change, StatefulWidget cannot

C) StatelessWidget never changes after being built, StatefulWidget can change and rebuild

D) They are the same thing with different names

---

**3. What does `setState()` do?**

A) Creates a new widget

B) Deletes a widget from the screen

C) Tells Flutter that something changed and the screen needs to rebuild

D) Saves the app to your phone

---

**4. What does Hot Reload do?**

A) Deletes your app and starts over

B) Instantly applies code changes while keeping the app's current state

C) Turns off the emulator

D) Installs a new version of Flutter

---

**5. In Tic-Tac-Toe, what does `GestureDetector` do?**

A) Draws the game board grid

B) Checks if someone won the game

C) Detects when a player taps on a cell

D) Switches turns between X and O

---

### Short Answer

**6. Look at this code:**

```dart
currentPlayer = currentPlayer == 'X' ? 'O' : 'X';
```

What does this line do? Explain it in plain English.

______________________________________________________________________________

______________________________________________________________________________

---

**7. What is the difference between a `Row` widget and a `Column` widget? When would you use each one?**

______________________________________________________________________________

______________________________________________________________________________

---

**8. Look at this code:**

```dart
board[lastRow].every((cell) => cell == symbol)
```

What does `.every()` do here? What does it return?

______________________________________________________________________________

______________________________________________________________________________

---

**9. In our Tic-Tac-Toe game, the board is stored as a `List<List<String?>>`. What does the `?` after `String` mean, and why is it important for our game?**

______________________________________________________________________________

______________________________________________________________________________

---

**10. You want to add a "Triple" button to the counter app that multiplies the counter by 3. Write the function you would create (including setState).**

______________________________________________________________________________

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B** — Any piece of the user interface — buttons, text, layouts, even the whole app

2. **C** — StatelessWidget never changes after being built, StatefulWidget can change and rebuild

3. **C** — Tells Flutter that something changed and the screen needs to rebuild

4. **B** — Instantly applies code changes while keeping the app's current state

5. **C** — Detects when a player taps on a cell

6. This is a **ternary operator** — a one-line if/else. It says: "If the current player is X, switch to O. Otherwise, switch to X." It's how the game alternates turns after each move.

7. A **Row** places widgets **side by side** (horizontally, left to right). A **Column** stacks widgets **vertically** (top to bottom). Use a Row when you want things next to each other (like an icon next to a number), and a Column when you want things stacked (like a title above a button).

8. `.every()` checks if **ALL** items in the list pass a test. Here it checks if every cell in the row equals the player's symbol. It returns `true` if ALL cells match (meaning that row is a win), or `false` if any cell doesn't match.

9. The `?` means the value can be a `String` OR `null`. This is important because empty cells start as `null` (no value). When a player taps a cell, it changes from `null` to `'X'` or `'O'`. Without the `?`, every cell would need a string value from the start.

10. Acceptable answer:
```dart
void _tripleCounter() {
  setState(() {
    _counter = _counter * 3;
  });
}
```
Key elements: the function uses `setState()`, and inside it multiplies `_counter` by 3.
