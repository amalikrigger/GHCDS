# Flutter Counter App Customizations

This guide walks you through making simple changes to the default Flutter counter app to understand how Flutter widgets, properties, and hot reload work.

## Change the App's Theme Color

In `lib/main.dart`, find the `ThemeData` section and edit the `primarySwatch` (or use `colorScheme` if Material 3):

```dart
theme: ThemeData(
  primarySwatch: Colors.green, // Change this to any color you like
),
```

Save and hot reload to see the new app bar color.

## Change the App Title

In the `MyApp` widget:

```dart
return MaterialApp(
  title: 'My First Flutter App',
  home: const MyHomePage(title: 'Custom Counter'),
);
```

The app’s name and the title in the app bar will update.

## Change the Counter Text Style

Inside `_MyHomePageState`, locate the `Text` widget that displays the counter:

```dart
Text(
  '$_counter',
  style: const TextStyle(fontSize: 40, color: Colors.blue, fontWeight: FontWeight.bold),
),
```

This makes the counter larger, bold, and blue.

## Change the Floating Action Button

Locate the `FloatingActionButton`:

```dart
floatingActionButton: FloatingActionButton(
  onPressed: _incrementCounter,
  backgroundColor: Colors.purple,
  child: const Icon(Icons.thumb_up),
),
```

This changes the button color and icon.

---

## Add a Reset Button
Include an extra button to reset the counter:

```dart
ElevatedButton(
  onPressed: () {
    setState(() {
      _counter = 0;
    });
  },
  child: const Text('Reset Counter'),
),
```

---

## Change AppBar Color and Title Style
```dart
appBar: AppBar(
  backgroundColor: Colors.teal,
  title: const Text('Custom Counter', style: TextStyle(color: Colors.white, fontWeight: FontWeight.bold)),
),
```

---

## Add an Icon Next to the Counter
```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    const Icon(Icons.star, color: Colors.amber, size: 32),
    const SizedBox(width: 8),
    Text('$_counter', style: const TextStyle(fontSize: 36, fontWeight: FontWeight.bold)),
  ],
),
```

---

## Change the Increment Icon
```dart
floatingActionButton: FloatingActionButton(
  onPressed: _incrementCounter,
  tooltip: 'Increment',
  child: const Icon(Icons.thumb_up), // Changed icon
),
```

---

## Add a Decrement Button
```dart
ElevatedButton.icon(
  onPressed: () {
    setState(() {
      if (_counter > 0) _counter--;
    });
  },
  icon: const Icon(Icons.remove),
  label: const Text('Decrement'),
),
```

---

## Experiment

Try adding:

- A background color to the `Scaffold`:

```dart
Scaffold(
  backgroundColor: Colors.yellow[100],
  ...
)
```

- Another button that decreases the counter:

```dart
FloatingActionButton(
  onPressed: _decrementCounter,
  backgroundColor: Colors.red,
  child: const Icon(Icons.remove),
),
```

Be creative and see how different properties affect the app’s look and behavior!
