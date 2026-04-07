# 🚁 Tello Drone: Code Your First Flight

### Write Python code that makes a real drone fly

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 1-2 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> You'll connect to a DJI Tello drone, write Python commands to control it, and program a flight routine that navigates a course. This is real Python — running real hardware.

---

## 🎯 What You'll Learn

- How to connect to and control a drone with Python
- Basic Python concepts: **variables**, **functions**, **loops**
- How to **think in distances and angles** to navigate physical space
- How to **test and debug** code that controls real hardware

---

## 🧰 What You Need

- A **DJI Tello** drone (charged)
- A computer with **Python 3** installed
- The `djitellopy` library (we'll install it)
- Open indoor space — **NO flying near people, windows, or fragile objects**

---

## ⚠️ Safety Rules — Read Before Flying

These are non-negotiable. Breaking them means you lose drone privileges.

1. **Only fly in the approved area** — your teacher will designate the space
2. **Everyone stands back** while a drone is in the air
3. **Never fly above head height** — keep it low until your code is solid
4. **Keep hands away** from spinning propellers
5. **If something goes wrong**, the drone will auto-land after 15 seconds of lost connection — don't panic
6. **Battery below 20%** = stop flying and charge

---

# Part 1: Connect and Test (15 minutes)

### Step 1 — Install the Library

Open your terminal (or VS Code terminal) and run:

```bash
pip install djitellopy
```

> **What is djitellopy?** It's a Python library that translates simple commands like `tello.move_forward(50)` into the signals the Tello drone understands. Without it, you'd have to send raw network packets — much harder.

---

### Step 2 — Connect to the Drone

1. Power on the Tello (press the button on the side — the light will blink)
2. On your computer, open **Wi-Fi settings**
3. Connect to the network named **TELLO-XXXXXX** (the X's are unique to your drone)
4. You'll lose internet while connected to the drone — that's normal

---

### Step 3 — Test the Connection

Create a new file called `test_flight.py` and paste this:

```python
from djitellopy import Tello

# Connect to the drone
tello = Tello()
tello.connect()

# Check the battery level
battery = tello.get_battery()
print(f"Battery: {battery}%")

# Take off, hover for 3 seconds, and land
tello.takeoff()
tello.land()
```

Run it:

```bash
python test_flight.py
```

The drone should take off, hover briefly, and land.

> **✅ Checkpoint:** The terminal shows the battery percentage, and the drone took off and landed safely.

---

### 🐍 Mini Lesson — Python Basics You'll Use

If this is your first time writing Python, here's what you need to know:

**Variables** store values:
```python
battery = tello.get_battery()   # battery now holds a number like 85
distance = 100                   # distance holds the number 100
```

**Functions** are actions you call:
```python
tello.takeoff()                  # Tell the drone to take off
tello.move_forward(100)          # Move forward 100 centimeters
tello.land()                     # Land the drone
```

The number in parentheses is called an **argument** — it tells the function HOW MUCH to do. `move_forward(100)` means move forward 100cm (about 3 feet). `move_forward(50)` is half that distance.

**Loops** repeat code:
```python
for i in range(4):               # Do this 4 times
    tello.move_forward(100)
    tello.rotate_clockwise(90)
```

This makes the drone fly in a square! It moves forward then turns right, 4 times.

---

# Part 2: Learn the Commands (10 minutes)

Before building your flight routine, practice these commands one at a time. Add them to your file BETWEEN `tello.takeoff()` and `tello.land()`:

| Command | What It Does |
|---|---|
| `tello.move_forward(x)` | Fly forward `x` centimeters |
| `tello.move_back(x)` | Fly backward `x` cm |
| `tello.move_left(x)` | Fly left `x` cm |
| `tello.move_right(x)` | Fly right `x` cm |
| `tello.move_up(x)` | Fly up `x` cm |
| `tello.move_down(x)` | Fly down `x` cm |
| `tello.rotate_clockwise(x)` | Turn right `x` degrees |
| `tello.rotate_counter_clockwise(x)` | Turn left `x` degrees |
| `tello.flip_forward()` | Do a front flip (needs 50%+ battery) |

> **Distance tip:** 100cm = about 3 feet. The minimum for any move command is 20cm. Start with small numbers and increase.

**Try this — fly a simple square:**

```python
from djitellopy import Tello

tello = Tello()
tello.connect()
print(f"Battery: {tello.get_battery()}%")

tello.takeoff()

# Fly a square
for i in range(4):
    tello.move_forward(80)
    tello.rotate_clockwise(90)

tello.land()
```

> **✅ Checkpoint:** The drone flies in a square and lands near where it started.

---

# Part 3: Build Your Flight Routine (remaining time)

### The Mission

Design a flight course using classroom materials, then write a Python program that flies the drone through it.

---

### Step 1 — Design Your Course

Use safe materials to set up at least **3 challenges**. Ideas:

- **Fly through a hoop** (hold up a cardboard hoop or hula hoop)
- **Navigate around cones** (zig-zag between 3 cones)
- **Fly over an obstacle** (go up, forward, then back down)
- **Land on a target** (tape an X on the floor as the landing zone)
- **Fly through a doorway or under a table**

**Sketch your course on paper** with distances and turns marked, just like the RoboMaster assignment.

---

### Step 2 — Code It Step by Step

Build your flight one segment at a time. **Do NOT write the entire program and run it** — that's how drones crash into walls.

```python
from djitellopy import Tello
import time

tello = Tello()
tello.connect()
print(f"Battery: {tello.get_battery()}%")

tello.takeoff()

# --- YOUR FLIGHT ROUTINE ---
# Segment 1: Fly forward to the first obstacle
tello.move_forward(100)

# Segment 2: Turn and go around it
tello.rotate_clockwise(90)
tello.move_forward(60)
tello.rotate_counter_clockwise(90)

# Segment 3: Fly through the hoop
tello.move_forward(120)

# Segment 4: Rise up, fly over obstacle, come back down
tello.move_up(50)
tello.move_forward(80)
tello.move_down(50)

# Segment 5: Land on the target
tello.land()
```

> **Key tip:** After each segment, add a `time.sleep(1)` to give the drone a moment to stabilize. This makes flights smoother and more accurate.

---

### Step 3 — Test and Adjust

Just like with the RoboMaster:

| Problem | Fix |
|---|---|
| Drone goes too far | Decrease the distance (e.g., 100 → 80) |
| Drone doesn't go far enough | Increase the distance |
| Drone turns too much | Reduce the degrees (90 → 85) |
| Drone drifts to one side | The Tello drifts naturally — add small corrections |
| Drone won't do a flip | Battery must be above 50% for flips |

> **Change ONE thing per test.** Real engineers don't change five things and hope for the best.

---

### Step 4 — Add Style (Optional)

Once your basic routine works, try adding flair:

**Use a function to reuse moves:**
```python
def fly_around_cone():
    tello.move_forward(60)
    tello.rotate_clockwise(90)
    tello.move_forward(40)
    tello.rotate_counter_clockwise(90)

# Now you can call it multiple times
fly_around_cone()
fly_around_cone()
```

> **What you just learned:** Functions let you name a chunk of code and reuse it. Instead of copying and pasting the same 4 lines, you write them once and call `fly_around_cone()` whenever you need them. This is one of the most important concepts in programming.

**Use a loop for repeated patterns:**
```python
# Zig-zag through 3 cones
for i in range(3):
    tello.move_forward(80)
    tello.rotate_clockwise(45)
    tello.move_forward(40)
    tello.rotate_counter_clockwise(45)
```

**Add a flip for bonus points:**
```python
if tello.get_battery() > 50:
    tello.flip_forward()
else:
    print("Battery too low for flips!")
```

> **What you just learned:** `if/else` is how programs make decisions. This code checks the battery first — if it's above 50%, do the flip. Otherwise, skip it and print a warning. Your code just made a smart decision on its own.

---

## 📝 Deliverables

1. **A video** of your drone completing your flight course
2. **Your Python file** (`.py`) — the code that flew the drone
3. **A screenshot** of your terminal output showing a successful connection and battery level
4. **A short reflection** (3-5 sentences): What was the hardest part? How many test flights did it take? What would you change if you had more time?

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | Video of your drone completing the flight course |
| 2 | Your Python file (`.py`) |
| 3 | Screenshot of your terminal output showing a successful connection and battery level |
| 4 | Your written reflection (3–5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"** — do **NOT** click "Create" (Create is for text only and won't let you attach files)
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Course Design | 5 | Creative, safe, at least 3 challenges |
| Python Program | 10 | Drone completes the course autonomously using your code |
| Execution | 5 | Smooth flight, drone navigates accurately |
| Deliverables | 5 | Video, code file, and reflection submitted |

**Bonus:**
- **+1 point** for including a flip or aerial trick safely
- **+2 points** for exceptionally creative course design
- **+2 points** for using functions or loops in your code (not just straight-line commands)

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Python** | A programming language — you're writing commands the computer runs |
| **Library** | Pre-written code someone else made that you can use (`djitellopy`) |
| **Variable** | A name that stores a value (`battery = 85`) |
| **Function** | A named block of code you can call (`tello.takeoff()`) |
| **Argument** | The value you pass into a function (`move_forward(100)` — 100 is the argument) |
| **Loop** | Code that repeats (`for i in range(4):` runs 4 times) |
| **If/Else** | Code that makes a decision based on a condition |
| **SDK** | Software Development Kit — tools for building programs that control hardware |

---

## 💡 Troubleshooting

**"Connection timed out" or "Can't connect"**
→ Make sure you're connected to the Tello's Wi-Fi (TELLO-XXXXXX), not the classroom Wi-Fi. Power cycle the drone and try again.

**"Battery too low"**
→ Land immediately and charge. Don't fly below 20%.

**"The drone drifts sideways"**
→ The Tello doesn't have GPS indoors, so it drifts. Add small corrections (`move_left(10)` or `move_right(10)`) to compensate. Fly on a flat, textured floor — the Tello's bottom camera uses the floor pattern to stabilize.

**"The drone takes off but won't respond to commands"**
→ Check your code for errors. Make sure every command is AFTER `tello.takeoff()` and BEFORE `tello.land()`. Add `time.sleep(2)` after takeoff to give it time to stabilize.

**"My flip command crashes the drone"**
→ Make sure there's at least 1 meter of clearance above and around the drone. Battery must be above 50%. Don't flip right after takeoff — move to open space first.
