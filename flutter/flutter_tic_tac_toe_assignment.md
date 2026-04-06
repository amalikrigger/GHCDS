# Flutter Mini–Module: From Counter App to Tic-Tac-Toe

## Learning Goals

- Install Flutter and run your first app on an emulator or device.
- Understand `StatelessWidget` vs `StatefulWidget`, `setState`, and widget trees.
- Build a 3×3 grid UI, handle taps, and manage game state.
- Ship a simple Tic-Tac-Toe without `.every()`, then refactor to use `.every()` for cleaner logic.

---

## Part A — Set Up Flutter and Run the Counter App

1. **Install Flutter**

   - Follow the official platform-specific install instructions (Windows, macOS, Linux).
   - If you’re brand new to Flutter, review the “Write your first Flutter app” guide.

2. **Editor and Toolchain**

   - Use Android Studio or VS Code.
   - Set up an emulator or connect a phone in developer mode.

3. **Create and Run Your Starter Project**

   ```bash
   flutter create my_first_flutter
   cd my_first_flutter
   flutter run
   ```

   - Tap the “+” button and watch the counter update.
   - This demonstrates how `StatefulWidget` and `setState` update UI.
   - For instructions, see [Flutter Counter Customization](https://github.com/amalikrigger/GHCDS/blob/main/flutter_counter_customizations.md)

---

## Part B — Build a Simple Tic-Tac-Toe (No `.every()`)

We’ll create a new project and implement the game with explicit loops.

1. **Create a New App**

   ```bash
   flutter create tictactoe_simple
   cd tictactoe_simple
   ```

2. **Open **`` and replace with this code:

```dart
import 'package:flutter/material.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Tic Tac Toe (Simple)',
      theme: ThemeData(colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo), useMaterial3: true),
      home: const TicTacToeSimpleScreen(),
    );
  }
}

class TicTacToeSimpleScreen extends StatefulWidget {
  const TicTacToeSimpleScreen({super.key});
  @override
  State<TicTacToeSimpleScreen> createState() => _TicTacToeSimpleScreenState();
}

class _TicTacToeSimpleScreenState extends State<TicTacToeSimpleScreen> {
  static const int size = 3;
  final List<List<String?>> board =
      List.generate(size, (_) => List.generate(size, (_) => null));
  String currentPlayer = 'X';

  bool get isBoardFull {
    for (var r = 0; r < size; r++) {
      for (var c = 0; c < size; c++) {
        if (board[r][c] == null) return false;
      }
    }
    return true;
  }

  void resetGame() {
    for (var r = 0; r < size; r++) {
      for (var c = 0; c < size; c++) {
        board[r][c] = null;
      }
    }
    currentPlayer = 'X';
    setState(() {});
  }

  bool isValidMove(int row, int col) => board[row][col] == null;

  void handleTap(int row, int col) {
    if (!isValidMove(row, col)) return;
    setState(() {
      board[row][col] = currentPlayer;

      if (checkWinnerNoEvery(row, col)) {
        showEndDialog('$currentPlayer wins!');
      } else if (isBoardFull) {
        showEndDialog("It's a draw!");
      } else {
        currentPlayer = currentPlayer == 'X' ? 'O' : 'X';
      }
    });
  }

  bool checkWinnerNoEvery(int lastRow, int lastCol) {
    final symbol = board[lastRow][lastCol];

    bool rowWin = true;
    for (var c = 0; c < size; c++) {
      if (board[lastRow][c] != symbol) { rowWin = false; break; }
    }
    if (rowWin) return true;

    bool colWin = true;
    for (var r = 0; r < size; r++) {
      if (board[r][lastCol] != symbol) { colWin = false; break; }
    }
    if (colWin) return true;

    if (lastRow == lastCol) {
      bool diagWin = true;
      for (var i = 0; i < size; i++) {
        if (board[i][i] != symbol) { diagWin = false; break; }
      }
      if (diagWin) return true;
    }

    if (lastRow + lastCol == size - 1) {
      bool antiWin = true;
      for (var i = 0; i < size; i++) {
        if (board[i][size - 1 - i] != symbol) { antiWin = false; break; }
      }
      if (antiWin) return true;
    }

    return false;
  }

  void showEndDialog(String title) {
    showDialog(
      context: context,
      builder: (_) => AlertDialog(
        title: Text(title),
        actions: [
          TextButton(onPressed: () { Navigator.pop(context); resetGame(); }, child: const Text('Play Again')),
        ],
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    final cells = List.generate(size * size, (index) {
      final row = index ~/ size;
      final col = index % size;
      final value = board[row][col] ?? '';
      return GestureDetector(
        onTap: () => handleTap(row, col),
        child: Container(
          decoration: BoxDecoration(border: Border.all(color: Colors.black54)),
          child: Center(child: Text(value, style: const TextStyle(fontSize: 32, fontWeight: FontWeight.bold))),
        ),
      );
    });

    return Scaffold(
      appBar: AppBar(title: const Text('Tic Tac Toe (Simple)')),
      body: Center(
        child: Column(
          mainAxisSize: MainAxisSize.min,
          children: [
            GridView.count(
              crossAxisCount: size,
              mainAxisSpacing: 2, crossAxisSpacing: 2,
              shrinkWrap: true,
              children: cells,
            ),
            const SizedBox(height: 16),
            Text('Next turn: $currentPlayer', style: const TextStyle(fontWeight: FontWeight.bold)),
            const SizedBox(height: 8),
            FilledButton(onPressed: resetGame, child: const Text('Reset')),
          ],
        ),
      ),
    );
  }
}
```

Run it with:

```bash
flutter run
```

---

## Part C — Refactor with `.every()`

Now that the simple version works, refactor your winner logic to use `.every()` for cleaner, more expressive code.

- **Row**:

```dart
bool rowWin = board[lastRow].every((cell) => cell == symbol);
```

- **Column**:

```dart
bool colWin = board.every((row) => row[lastCol] == symbol);
```

- **Main diagonal**:

```dart
bool diagWin = (lastRow == lastCol) &&
    List.generate(size, (i) => i).every((i) => board[i][i] == symbol);
```

- **Anti-diagonal**:

```dart
bool antiWin = (lastRow + lastCol == size - 1) &&
    List.generate(size, (i) => i).every((i) => board[i][size - 1 - i] == symbol);
```

- **Draw**:

```dart
bool draw = board.every((row) => row.every((cell) => cell != null));
```

Test each scenario: row win, column win, both diagonals, and draw.

---

## Stretch Goals

- Add a scoreboard to track wins.
- Highlight the winning line.
- Add player names and 3x3 vs 4x4 option.
- Extract the grid cell into its own widget.

---

## References

- [Flutter install guide](https://docs.flutter.dev/get-started/install)
- [Flutter first app tutorial](https://docs.flutter.dev/get-started/codelab)
- [Dart language tour](https://dart.dev/guides/language/language-tour)
- [GridView docs](https://api.flutter.dev/flutter/widgets/GridView-class.html)
- [GestureDetector docs](https://api.flutter.dev/flutter/widgets/GestureDetector-class.html)

