# 🎮 Flutter: From Counter App to Tic-Tac-Toe

### Learn app development by building real things

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 4 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> You'll start by running your first mobile app, learn how Flutter works by customizing it, then build a full Tic-Tac-Toe game from scratch. By the end, you'll understand how real apps are built.

---

## 🎯 What You'll Learn

- How to create and run a Flutter app on an Android emulator
- What **widgets** are and how they build an app's interface
- The difference between **StatelessWidget** and **StatefulWidget**
- How **setState** makes your app react to user actions
- How to build a game with a grid, tap detection, and win logic

---

## 🧰 What You Need

- A computer with **Flutter** installed ([flutter.dev/get-started/install](https://docs.flutter.dev/get-started/install))
- **Android Studio** with the Flutter and Dart plugins installed
- An Android emulator set up and running
- A computer with **Flutter** installed ([flutter.dev/get-started/install](https://docs.flutter.dev/get-started/install))

> **Don't have Flutter yet?** Ask your teacher for help with the install. It takes about 20-30 minutes the first time.

---

## 🔍 Pro Tip: The Find Tool

Throughout this tutorial, you'll need to find specific lines of code to change. Instead of scrolling through everything, use the **Find** shortcut:

- **Mac:** Cmd + F
- **Windows/Chromebook:** Ctrl + F

A search bar will pop up. Type what you're looking for (like `Colors.teal` or `setState`) and it will jump right to it. This is how real developers navigate code — use it constantly!

---

# Day 1: Your First Flutter App

**Goal:** Create a Flutter project, run it on the emulator, and understand how the code works.

---

### Step 1 — Create Your Project

1. Open **Android Studio**
2. Click **New Flutter Project** (or File → New → New Flutter Project)
3. Make sure the Flutter SDK path is set (ask your teacher if it's not)
4. Name your project `my_first_app` (no spaces, no capital letters)
5. Click **Create**

Android Studio will generate a complete app with a working counter already built in.

> **What just happened?** Flutter generated a complete app with folders for Android, iOS, web, and your Dart code. The code you'll edit lives in the `lib/` folder — specifically the file `lib/main.dart`.

---

### Step 2 — Run It on the Emulator

1. In Android Studio, look at the **toolbar** near the top. You should see a device dropdown (it might say "Pixel" or "No device"). Click it and select your emulator. If none appear, go to **Tools → Device Manager** and start one.
2. Click the green **▶ Run** button (or press **Shift + F10**)
3. Wait for it to build (this takes a minute the first time)
4. You should see a simple app with a counter and a "+" button
5. Tap the "+" button and watch the number go up

> **✅ Checkpoint:** The counter app is running on your emulator. Every time you tap "+", the number increases.

---

### 🔄 Mini Lesson — Hot Reload vs Hot Restart

Flutter has two superpowers that save you a ton of time:

**Hot Reload (⚡ lightning bolt button, or press `r` in terminal)**
Instantly applies your code changes WITHOUT losing the app's current state. If your counter is at 5 and you change a color, hot reload keeps the counter at 5 and just updates the color. Use this for small changes like colors, text, and layout tweaks.

**Hot Restart (green circular arrow button, or press `Shift + R`)**
Restarts the entire app from scratch. The counter goes back to 0, all state is reset. Use this when you change something structural — like adding new variables, new functions, or changing how the app starts up.

**When in doubt:** Try hot reload first. If the change doesn't show up, do a hot restart. If that doesn't work, stop the app (red ■ button) and hit Run again.

---

### Step 3 — Understand the Code

Open the file **`lib/main.dart`**. This is the only file we'll edit. Let's break it down.

---

### 🧠 Mini Lesson — How Flutter Apps Work

Flutter apps are built with **widgets**. A widget is any piece of the screen — a button, a piece of text, a container, even the whole app itself. Widgets stack inside each other like building blocks.

There are two types, and understanding the difference is the most important concept in Flutter:

**StatelessWidget — Cannot change once built**

Think of a **printed poster**. Once it's printed, the text and images stay the same forever. A StatelessWidget is like that — it displays something, but it never updates.

Example: The `MyApp` widget in your counter app. It sets up the theme and title once, and that's it. It never needs to change.

```dart
class MyApp extends StatelessWidget {  // "I never change"
```

**StatefulWidget — Can change and rebuild itself**

Think of a **scoreboard at a basketball game**. The score starts at 0-0, but it updates throughout the game. A StatefulWidget is like that — it holds data (called **state**) that can change, and when it does, the screen rebuilds to show the new data.

Example: The `MyHomePage` widget tracks the counter number. When you tap "+", the number changes, and the widget rebuilds to show the new number.

```dart
class MyHomePage extends StatefulWidget {  // "I can change"
```

**setState() — The update trigger**

`setState()` is how you tell Flutter "something changed — rebuild the screen." Without it, you could change a variable in your code, but the screen would never update. It's like updating the score on the scoreboard's computer but forgetting to press the button that refreshes the display.

```dart
void _increment() {
  setState(() {       // "Hey Flutter, update the screen!"
    _counter++;       // Change the data
  });                 // Flutter rebuilds with the new number
}
```

**The widget tree** is the structure of your app — widgets nested inside widgets:

```
MaterialApp
  └── Scaffold
       ├── AppBar
       │    └── Text("Flutter Demo")
       └── Center
            └── Column
                 ├── Text("You have pushed...")
                 └── Text("0")  ← this updates with setState
```

> **Think of it like HTML:** In web development, you nest `<div>` inside `<div>`. In Flutter, you nest Widget inside Widget. Same idea, different language.

---

### 📝 Day 1 Deliverables

1. Screenshot of the counter app running on your emulator
2. In your own words (2-3 sentences): What is the difference between a StatelessWidget and a StatefulWidget?

---

# Day 2: Customize the Counter App

**Goal:** Transform the default counter app step by step. Each change teaches a new Flutter concept. You'll make one change at a time, hot reload, and see the result.

---

### Before You Start

Open your `my_first_app` project from Day 1 in Android Studio. Open `lib/main.dart` — this is the only file we'll edit. Make sure the app is running on the emulator (green ▶ button).

Every time you make a change below, **save the file** (Ctrl+S / Cmd+S) and the app should update instantly via hot reload. If it doesn't, click the ⚡ button.

---

### Step 1 — Change the Theme Color

Use **Cmd+F / Ctrl+F** to search for `deepPurple`. You should find a line like:

```dart
colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple),
```

Change `Colors.deepPurple` to `Colors.teal`:

```dart
colorScheme: ColorScheme.fromSeed(seedColor: Colors.teal),
```

**Save and hot reload.**

> **✅ Checkpoint:** The app bar and floating button should change from purple to teal.

> **What you learned:** `ColorScheme.fromSeed` generates an entire color palette from one color. Changing this one line updates buttons, the app bar, and other themed elements across the whole app.

---

### Step 2 — Change the App Bar Title

Use **Cmd+F / Ctrl+F** to find `Flutter Demo Home Page`. Change it to something fun:

```dart
appBar: AppBar(
  backgroundColor: Theme.of(context).colorScheme.inversePrimary,
  title: Text('My Counter App'),
),
```

**Save and hot reload.**

> **✅ Checkpoint:** The app bar now shows your custom title.

---

### Step 3 — Make the Counter Number Bigger and Bolder

Find the `Text` widget that displays the counter. It looks like:

```dart
Text(
  '$_counter',
  style: Theme.of(context).textTheme.headlineMedium,
),
```

Replace the style with your own custom style:

```dart
Text(
  '$_counter',
  style: const TextStyle(
    fontSize: 60,
    fontWeight: FontWeight.bold,
    color: Colors.teal,
  ),
),
```

**Save and hot reload.**

> **✅ Checkpoint:** The counter number is now huge, bold, and teal.

> **What you learned:** `TextStyle` lets you control exactly how text looks — size, weight (bold), color, font, and more. The `$_counter` syntax is called **string interpolation** — it inserts the value of `_counter` into the text.

---

### Step 4 — Change the Floating Action Button Icon

Find the `FloatingActionButton` near the bottom of the file:

```dart
floatingActionButton: FloatingActionButton(
  onPressed: _incrementCounter,
  tooltip: 'Increment',
  child: const Icon(Icons.add),
),
```

Change the icon and add a custom color:

```dart
floatingActionButton: FloatingActionButton(
  onPressed: _incrementCounter,
  tooltip: 'Increment',
  backgroundColor: Colors.teal,
  child: const Icon(Icons.thumb_up, color: Colors.white),
),
```

**Save and hot reload.**

> **✅ Checkpoint:** The floating button is now teal with a thumbs-up icon.

> **What you learned:** `Icons.thumb_up` is one of thousands of built-in Material icons. You can browse them all at [fonts.google.com/icons](https://fonts.google.com/icons). Try `Icons.star`, `Icons.favorite`, `Icons.bolt`, or `Icons.rocket_launch`.

---

### Step 5 — Add a Decrement Button

Now we're adding something new — not just changing what's there. First, you need a new function. Find the `_incrementCounter` function:

```dart
void _incrementCounter() {
  setState(() {
    _counter++;
  });
}
```

Right **below** that function, add a new one:

```dart
void _decrementCounter() {
  setState(() {
    if (_counter > 0) _counter--;
  });
}
```

Now you need a button that calls it. Find the `Column` in the `body` section that contains the counter text. Add a new button **after** the counter `Text` widget. The column's `children` list should now look like:

```dart
children: <Widget>[
  const Text('You have pushed the button this many times:'),
  Text(
    '$_counter',
    style: const TextStyle(
      fontSize: 60,
      fontWeight: FontWeight.bold,
      color: Colors.teal,
    ),
  ),
  const SizedBox(height: 20),
  ElevatedButton.icon(
    onPressed: _decrementCounter,
    icon: const Icon(Icons.remove),
    label: const Text('Subtract'),
  ),
],
```

**Save and hot reload.**

> **✅ Checkpoint:** There's now a "Subtract" button below the counter. Tapping it decreases the number (but never goes below 0).

> **What you learned:** You just did three important things:
> 1. Created a **new function** with `setState` — Flutter now knows how to subtract
> 2. Used `if (_counter > 0)` to **prevent negative numbers** — that's input validation
> 3. Added `SizedBox(height: 20)` — that's a **spacer** widget that adds vertical space between widgets

---

### Step 6 — Add a Reset Button

Add another function below `_decrementCounter`:

```dart
void _resetCounter() {
  setState(() {
    _counter = 0;
  });
}
```

Then add another button to the `children` list, after the subtract button:

```dart
const SizedBox(height: 10),
ElevatedButton.icon(
  onPressed: _resetCounter,
  icon: const Icon(Icons.refresh),
  label: const Text('Reset'),
  style: ElevatedButton.styleFrom(
    backgroundColor: Colors.red[300],
    foregroundColor: Colors.white,
  ),
),
```

**Save and hot reload.**

> **✅ Checkpoint:** There's now a red "Reset" button that sets the counter back to 0.

> **What you learned:** `ElevatedButton.styleFrom()` lets you customize a specific button's appearance. `backgroundColor` is the button's fill color, and `foregroundColor` is the text/icon color.

---

### Step 7 — Add an Icon Next to the Counter

Right now the counter text sits alone. Let's put an icon next to it using a `Row` widget.

Find your counter `Text` widget and wrap it in a `Row`. Replace just the `Text` widget with this:

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    const Icon(Icons.star, color: Colors.amber, size: 36),
    const SizedBox(width: 10),
    Text(
      '$_counter',
      style: const TextStyle(
        fontSize: 60,
        fontWeight: FontWeight.bold,
        color: Colors.teal,
      ),
    ),
  ],
),
```

**Save and hot reload.**

> **✅ Checkpoint:** A gold star icon now appears next to the counter number.

> **What you learned:** `Row` places widgets **side by side** (horizontally). `Column` stacks them **vertically**. These are the two most important layout widgets in Flutter. `SizedBox(width: 10)` adds horizontal spacing inside a Row.

---

### Step 8 — Free Customization (Your Turn!)

Make at least **2 more changes** on your own. Here are ideas:

- Change the star icon to something else (use Cmd+F to find `Icons.star`)
- Change `Colors.teal` to your favorite color everywhere
- Change the counter font size
- Add a "Double" button that multiplies the counter by 2:
  ```dart
  void _doubleCounter() {
    setState(() {
      _counter = _counter * 2;
    });
  }
  ```
- Change the background color: find `Scaffold(` and add `backgroundColor: Colors.grey[100],` inside it

---

### 📝 Day 2 Deliverables

1. Screenshot of your customized counter app (should look noticeably different from the default)
2. List every change you made (should be at least 8 — the 7 guided steps plus your own)
3. In your own words: What does `setState()` do and why is it important?

---

# Day 3: Build Tic-Tac-Toe — The Board

**Goal:** Create a new Flutter project and build a working Tic-Tac-Toe game step by step.

---

### Step 1 — Create a New Project

1. In Android Studio, click **File → New → New Flutter Project**
2. Name it `tictactoe`
3. Click **Create**
4. Wait for it to set up

---

### Step 2 — Paste the Full Game Code

Open **`lib/main.dart`** (in the Project panel on the left, under `lib`). Select all, delete, and paste this entire file:

```dart
import 'package:flutter/material.dart';

void main() => runApp(const TicTacToeApp());

// --- THE APP SHELL ---
// This is a StatelessWidget because the app setup never changes.
class TicTacToeApp extends StatelessWidget {
  const TicTacToeApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Tic Tac Toe',
      theme: ThemeData(
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
        useMaterial3: true,
      ),
      home: const GameScreen(),
    );
  }
}

// --- THE GAME SCREEN ---
// This is a StatefulWidget because the board changes every turn.
class GameScreen extends StatefulWidget {
  const GameScreen({super.key});

  @override
  State<GameScreen> createState() => _GameScreenState();
}

class _GameScreenState extends State<GameScreen> {
  // --- GAME STATE ---
  // The board: a 3x3 grid. Each cell is null (empty), 'X', or 'O'.
  static const int size = 3;
  final List<List<String?>> board =
      List.generate(size, (_) => List.generate(size, (_) => null));

  // Whose turn is it?
  String currentPlayer = 'X';

  // Score tracking
  int xWins = 0;
  int oWins = 0;

  // --- GAME LOGIC ---

  // Check if every cell on the board is filled
  bool get isBoardFull {
    for (var row in board) {
      for (var cell in row) {
        if (cell == null) return false;
      }
    }
    return true;
  }

  // Reset the board for a new game
  void resetGame() {
    setState(() {
      for (var r = 0; r < size; r++) {
        for (var c = 0; c < size; c++) {
          board[r][c] = null;
        }
      }
      currentPlayer = 'X';
    });
  }

  // Handle a tap on a cell
  void handleTap(int row, int col) {
    // Ignore taps on cells that are already taken
    if (board[row][col] != null) return;

    setState(() {
      // Place the current player's mark
      board[row][col] = currentPlayer;

      // Check if this move won the game
      if (checkWinner(row, col)) {
        // Update score
        if (currentPlayer == 'X') {
          xWins++;
        } else {
          oWins++;
        }
        showEndDialog('$currentPlayer wins! 🎉');
      } else if (isBoardFull) {
        showEndDialog("It's a draw! 🤝");
      } else {
        // Switch turns: if it was X, now it's O, and vice versa
        currentPlayer = currentPlayer == 'X' ? 'O' : 'X';
      }
    });
  }

  // Check if the last move created a winning line
  bool checkWinner(int lastRow, int lastCol) {
    final symbol = board[lastRow][lastCol];

    // Check the row where the last move was made
    bool rowWin = true;
    for (var c = 0; c < size; c++) {
      if (board[lastRow][c] != symbol) {
        rowWin = false;
        break;
      }
    }
    if (rowWin) return true;

    // Check the column where the last move was made
    bool colWin = true;
    for (var r = 0; r < size; r++) {
      if (board[r][lastCol] != symbol) {
        colWin = false;
        break;
      }
    }
    if (colWin) return true;

    // Check the main diagonal (top-left to bottom-right)
    // Only need to check if the last move was ON the diagonal
    if (lastRow == lastCol) {
      bool diagWin = true;
      for (var i = 0; i < size; i++) {
        if (board[i][i] != symbol) {
          diagWin = false;
          break;
        }
      }
      if (diagWin) return true;
    }

    // Check the anti-diagonal (top-right to bottom-left)
    if (lastRow + lastCol == size - 1) {
      bool antiWin = true;
      for (var i = 0; i < size; i++) {
        if (board[i][size - 1 - i] != symbol) {
          antiWin = false;
          break;
        }
      }
      if (antiWin) return true;
    }

    return false;
  }

  // Show a popup when the game ends
  void showEndDialog(String message) {
    showDialog(
      context: context,
      barrierDismissible: false,
      builder: (_) => AlertDialog(
        title: Text(message, textAlign: TextAlign.center),
        actions: [
          TextButton(
            onPressed: () {
              Navigator.pop(context);
              resetGame();
            },
            child: const Text('Play Again'),
          ),
        ],
      ),
    );
  }

  // --- BUILD THE UI ---
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.grey[100],
      appBar: AppBar(
        backgroundColor: Colors.indigo,
        title: const Text(
          'Tic Tac Toe',
          style: TextStyle(color: Colors.white, fontWeight: FontWeight.bold),
        ),
        actions: [
          IconButton(
            onPressed: resetGame,
            icon: const Icon(Icons.refresh, color: Colors.white),
          ),
        ],
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            // Scoreboard
            Row(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                _buildScoreCard('X', xWins, Colors.blue),
                const SizedBox(width: 30),
                _buildScoreCard('O', oWins, Colors.red),
              ],
            ),
            const SizedBox(height: 20),

            // The game board
            SizedBox(
              width: 300,
              height: 300,
              child: GridView.count(
                crossAxisCount: size,
                mainAxisSpacing: 4,
                crossAxisSpacing: 4,
                children: List.generate(size * size, (index) {
                  final row = index ~/ size;
                  final col = index % size;
                  return _buildCell(row, col);
                }),
              ),
            ),
            const SizedBox(height: 20),

            // Turn indicator
            Text(
              "It's $currentPlayer's turn",
              style: const TextStyle(fontSize: 20, fontWeight: FontWeight.bold),
            ),
          ],
        ),
      ),
    );
  }

  // Build a single cell of the grid
  Widget _buildCell(int row, int col) {
    final value = board[row][col];
    return GestureDetector(
      onTap: () => handleTap(row, col),
      child: Container(
        decoration: BoxDecoration(
          color: Colors.white,
          borderRadius: BorderRadius.circular(8),
          boxShadow: [
            BoxShadow(
              color: Colors.black.withValues(alpha: 0.1),
              blurRadius: 4,
              offset: const Offset(0, 2),
            ),
          ],
        ),
        child: Center(
          child: Text(
            value ?? '',
            style: TextStyle(
              fontSize: 40,
              fontWeight: FontWeight.bold,
              color: value == 'X' ? Colors.blue : Colors.red,
            ),
          ),
        ),
      ),
    );
  }

  // Build a score card for X or O
  Widget _buildScoreCard(String player, int score, Color color) {
    return Column(
      children: [
        Text(
          player,
          style: TextStyle(
            fontSize: 28,
            fontWeight: FontWeight.bold,
            color: color,
          ),
        ),
        Text(
          '$score wins',
          style: TextStyle(fontSize: 16, color: Colors.grey[600]),
        ),
      ],
    );
  }
}
```

Save the file and click the green **▶ Run** button (or press **Shift + F10**). If you get asked to select a device, choose your emulator.

> **✅ Checkpoint:** You should see a Tic-Tac-Toe board with a scoreboard at the top, X and O take turns, and a popup appears when someone wins or it's a draw.

---

### Step 3 — Understand How the Game Works

Let's walk through the key parts of the code you just pasted.

---

**The board is a 2D list (a grid):**

```dart
final List<List<String?>> board =
    List.generate(size, (_) => List.generate(size, (_) => null));
```

This creates a 3×3 grid where every cell starts as `null` (empty). When a player taps a cell, it becomes `'X'` or `'O'`. The `String?` means the value can be a string OR null.

Think of it like this:
```
[null, null, null]
[null, null, null]
[null, null, null]
```

After a few moves it might look like:
```
['X',  null, 'O' ]
[null, 'X',  null]
['O',  null, null]
```

---

**Handling taps with GestureDetector:**

```dart
GestureDetector(
  onTap: () => handleTap(row, col),
  child: Container(...)
)
```

`GestureDetector` wraps any widget and listens for taps, swipes, or other gestures. When the player taps a cell, it calls `handleTap` with that cell's row and column.

---

**Switching turns with a ternary:**

```dart
currentPlayer = currentPlayer == 'X' ? 'O' : 'X';
```

This is a shortcut that means: "If the current player is X, switch to O. Otherwise, switch to X." It's called a **ternary operator** — a one-line if/else.

---

**Checking for a winner:**

The `checkWinner` function checks 4 things after every move:
1. Did the current player fill an entire **row**?
2. Did they fill an entire **column**?
3. Did they fill the **main diagonal** (↘)?
4. Did they fill the **anti-diagonal** (↙)?

It uses `for` loops to check each cell in that line. If any cell doesn't match the player's symbol, it's not a win.

---

**GridView.count — the game board layout:**

```dart
GridView.count(
  crossAxisCount: size,  // 3 columns
  children: List.generate(size * size, (index) {
    final row = index ~/ size;    // integer division
    final col = index % size;     // remainder
    return _buildCell(row, col);
  }),
)
```

`GridView.count` creates a grid with a fixed number of columns. We generate 9 cells (3×3) and convert each cell's index into a row and column number using division and remainder.

| Index | row (index ÷ 3) | col (index % 3) |
|---|---|---|
| 0 | 0 | 0 |
| 1 | 0 | 1 |
| 2 | 0 | 2 |
| 3 | 1 | 0 |
| 4 | 1 | 1 |
| ... | ... | ... |

---

### 📝 Day 3 Deliverables

1. Screenshot of the Tic-Tac-Toe game running
2. Screenshot of a win popup appearing
3. In your own words: How does the game know which row and column you tapped?

---

# Day 4: Customize and Level Up

**Goal:** Refactor the win-checking code to be cleaner, then make the game your own.

---

### Step 1 — Cleaner Win Logic with `.every()`

The `checkWinner` function works, but it's a lot of code. Dart has a built-in method called `.every()` that checks if ALL items in a list pass a test. Let's use it.

Use **Cmd+F / Ctrl+F** to search for `checkWinner`. Find the entire function and **replace it** with this:

```dart
bool checkWinner(int lastRow, int lastCol) {
  final symbol = board[lastRow][lastCol];

  // Row: does every cell in this row match?
  bool rowWin = board[lastRow].every((cell) => cell == symbol);
  if (rowWin) return true;

  // Column: does every row's cell in this column match?
  bool colWin = board.every((row) => row[lastCol] == symbol);
  if (colWin) return true;

  // Main diagonal (top-left to bottom-right)
  bool diagWin = (lastRow == lastCol) &&
      List.generate(size, (i) => i).every((i) => board[i][i] == symbol);
  if (diagWin) return true;

  // Anti-diagonal (top-right to bottom-left)
  bool antiWin = (lastRow + lastCol == size - 1) &&
      List.generate(size, (i) => i).every((i) => board[i][size - 1 - i] == symbol);
  if (antiWin) return true;

  return false;
}
```

Save and test. The game should work exactly the same, but the code is much shorter.

> **What just happened?** `.every()` takes a test (a function) and returns `true` only if EVERY item in the list passes. For example, `board[lastRow].every((cell) => cell == symbol)` asks: "Is every cell in this row equal to the player's symbol?" That replaces a 5-line for loop with one line.

---

### Step 2 — Also Clean Up isBoardFull

Find `isBoardFull` and replace it:

```dart
bool get isBoardFull {
  return board.every((row) => row.every((cell) => cell != null));
}
```

This reads almost like English: "The board is full if every row has every cell not null."

---

### Step 3 — Customize Your Game

Try these challenges. Each one teaches you something new. Use **Cmd+F / Ctrl+F** to find the code you need to change:

**Challenge 1 — Change the colors:**
Find `Colors.blue` and `Colors.red` for X and O. Try any colors you like: `Colors.purple`, `Colors.green`, `Colors.orange`, etc.

**Challenge 2 — Change the board size:**
Find `static const int size = 3;` and change it to `4` for a 4×4 game. Everything else adapts automatically because we used `size` everywhere instead of hardcoding `3`. This is called **avoiding magic numbers**.

**Challenge 3 — Change the symbols:**
Instead of 'X' and 'O', try emoji:
```dart
String currentPlayer = '🔥';
```
And in `handleTap`, change the switch line:
```dart
currentPlayer = currentPlayer == '🔥' ? '❄️' : '🔥';
```

**Challenge 4 — Change the cell style:**
In `_buildCell`, try changing:
- `borderRadius: BorderRadius.circular(8)` → try `20` for more rounded corners
- `color: Colors.white` → try `Colors.indigo[50]` for a tinted background
- `fontSize: 40` → make the symbols bigger or smaller

**Challenge 5 (Advanced) — Add a reset score button:**
Add a new button below the turn indicator:
```dart
ElevatedButton.icon(
  onPressed: () {
    setState(() {
      xWins = 0;
      oWins = 0;
    });
    resetGame();
  },
  icon: const Icon(Icons.delete),
  label: const Text('Reset Scores'),
),
```

---

### 📝 Day 4 Deliverables

1. Screenshot of your customized Tic-Tac-Toe game
2. A short reflection (3-5 sentences): What did you customize? What was the trickiest part of understanding the code? What would you add if you had more time?

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | **Day 1:** Screenshot of the default counter app running on the emulator |
| 2 | **Day 1:** Written explanation — What is the difference between StatelessWidget and StatefulWidget? |
| 3 | **Day 2:** Screenshot of your customized counter app (showing your UI changes) |
| 4 | **Day 2:** Written list of 3+ changes you made and explanation of how setState works |
| 5 | **Day 3:** Screenshot of Tic-Tac-Toe game running with a win/draw popup visible |
| 6 | **Day 3:** Written explanation of how Row and Column widgets helped with the layout |
| 7 | **Day 4:** Screenshot of your customized Tic-Tac-Toe game showing your enhancements |
| 8 | **Day 4:** Written reflection (3–5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"** — do **NOT** click "Create" (Create is for text only and won't let you attach files)
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## �📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Counter App | 5 | App runs, you understand StatelessWidget vs StatefulWidget |
| Counter Customization | 5 | Made 3+ visible changes, can explain setState |
| Tic-Tac-Toe Running | 5 | Game runs, turns alternate, wins are detected |
| Code Understanding | 5 | Can explain how the board, taps, and win logic work |
| Customization + Reflection | 5 | Made changes to the game, submitted reflection |

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Widget** | Any piece of the UI — a button, text, container, even the whole app |
| **StatelessWidget** | A widget that never changes after it's built |
| **StatefulWidget** | A widget that can change (rebuild) when data updates |
| **setState()** | Tells Flutter "something changed, rebuild the screen" |
| **Scaffold** | The base layout widget — gives you an app bar, body, and floating button |
| **Row / Column** | Layout widgets: Row = side by side, Column = stacked vertically |
| **GridView** | Displays widgets in a grid (rows and columns) |
| **GestureDetector** | Wraps a widget to detect taps, swipes, and other gestures |
| **Ternary Operator** | A one-line if/else: `condition ? valueIfTrue : valueIfFalse` |
| **`.every()`** | Checks if ALL items in a list pass a test — returns true or false |
| **2D List** | A list of lists — used to represent grids like our game board |
| **Null (`null`)** | Means "no value" — our empty cells start as null |
| **Hot Reload** | Flutter updates the running app instantly when you save — no restart needed |
| **Widget Tree** | The nested structure of widgets that makes up your app's UI |

---

## 💡 Troubleshooting

**"No devices found" or "No device selected"**
→ Open **Tools → Device Manager** in Android Studio and start an emulator. Then select it from the device dropdown in the toolbar.

**"The app builds but shows a blank screen"**
→ Check for red error text in the emulator or in the Run console at the bottom of Android Studio. Usually a typo in the code. Use **Cmd+F / Ctrl+F** to search and compare your code to the code blocks above.

**"Hot reload isn't working"**
→ Click the ⚡ hot reload button. If that doesn't work, click the green circular arrow for a hot restart. If still broken, stop the app (red ■ button) and hit Run again.

**"The game doesn't detect wins correctly"**
→ Make sure you replaced the entire `checkWinner` function, not just part of it. Use **Cmd+F / Ctrl+F** to search for `checkWinner` and verify it matches.

**"I changed the board size to 4 but it looks weird"**
→ Use **Cmd+F / Ctrl+F** to find `width: 300` and `height: 300`, and increase both to `400` so the cells aren't too small.

**"I can't find the code I need to change"**
→ Use the **Find** tool! Press **Cmd+F** (Mac) or **Ctrl+F** (Windows) and type part of what you're looking for, like `Colors.teal` or `checkWinner`.
