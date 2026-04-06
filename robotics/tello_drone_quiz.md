# 🚁 Tello Drone — Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

---

### Multiple Choice

**1. What does `tello.move_forward(100)` do?**

A) Moves the drone forward 100 meters

B) Moves the drone forward 100 centimeters (about 3 feet)

C) Sets the drone's speed to 100

D) Rotates the drone 100 degrees

---

**2. What is a Python "library"?**

A) A place where you check out books about coding

B) Pre-written code someone else made that you can use in your program

C) A folder where Python stores error messages

D) A website for downloading drones

---

**3. What does this code do?**

```python
for i in range(4):
    tello.move_forward(80)
    tello.rotate_clockwise(90)
```

A) Moves the drone forward 4 times without turning

B) Flies the drone in a square

C) Spins the drone in a circle

D) Makes the drone flip 4 times

---

### Short Answer

**4. What is the difference between a variable and a function in Python? Give one example of each from the drone code.**

______________________________________________________________________________

______________________________________________________________________________

---

**5. Look at this code:**

```python
if tello.get_battery() > 50:
    tello.flip_forward()
else:
    print("Battery too low for flips!")
```

Explain what this code does in plain English. Why is the `if` check important?

______________________________________________________________________________

______________________________________________________________________________

---

**6. Your drone keeps drifting to the left during a straight `move_forward(200)` command. What would you add to your code to fix this?**

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B** — Moves the drone forward 100 centimeters (about 3 feet). All Tello distance commands use centimeters.

2. **B** — Pre-written code someone else made that you can use. `djitellopy` is a library that gives us simple commands like `tello.takeoff()` instead of having to write complex network code ourselves.

3. **B** — Flies the drone in a square. It moves forward 80cm then turns right 90°, and repeats this 4 times. Four 90° turns = 360° = back to the start facing the same direction.

4. A **variable** stores a value with a name — example: `battery = tello.get_battery()` stores the battery percentage. A **function** is an action you call — example: `tello.takeoff()` tells the drone to launch. The key difference is that variables hold data, while functions do something.

5. This code checks the battery level before attempting a flip. If the battery is above 50%, it does a front flip. If the battery is 50% or below, it skips the flip and prints a warning message instead. The `if` check is important because flips require a lot of power — attempting one with low battery could cause the drone to crash or lose control mid-flip.

6. Add a small correction after the forward movement, like `tello.move_right(10)` or `tello.move_right(15)` to compensate for the drift. You'd need to test different amounts to find the right correction. Indoor drones drift because they don't have GPS — they rely on a downward camera to track position.
