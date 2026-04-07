# 🎛️ Micro:bit: Tiny Computer, Big Ideas

### Program a pocket-sized computer with sensors, buttons, and LEDs

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 2 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> The micro:bit is a tiny programmable computer with built-in sensors, buttons, and an LED display. You'll program it using blocks or Python — right in your browser. No installation needed. By the end, you'll build something interactive that responds to your input.

---

## 🎯 What You'll Learn

- How to program a **micro:bit** using the MakeCode block editor
- How **sensors** work (accelerometer, temperature, light, compass)
- How **inputs and outputs** make devices interactive
- Basic **programming logic** (variables, conditionals, loops)
- How to build a fun interactive project from scratch

---

## 🧰 What You Need

- A **micro:bit** (V1 or V2)
- A **USB cable** (micro-USB)
- A computer with a web browser
- Go to [makecode.microbit.org](https://makecode.microbit.org/) — everything runs in the browser

---

# Day 1: Learn the Basics

**Goal:** Connect your micro:bit, learn the key blocks, and build 3 mini projects to understand how it works.

---

### Step 1 — Open MakeCode

1. Go to [makecode.microbit.org](https://makecode.microbit.org/)
2. Click **New Project**
3. Give it a name like "my-first-project"

You'll see:
- **The simulator** on the left — a virtual micro:bit that runs your code instantly
- **Block categories** in the middle — drag these to build your program
- **The workspace** on the right — where you build your code

> **✅ Checkpoint:** You can see the MakeCode editor with a simulated micro:bit on the left.

---

### Step 2 — Your First Program: Display a Message

Drag these blocks into the workspace:

1. From **Basic**, drag `show string "Hello!"` into the `on start` block
2. Click the play button on the simulator

The virtual micro:bit scrolls "Hello!" across its LED display.

Now change `"Hello!"` to your name!

> **What just happened?** `on start` runs once when the micro:bit powers on. `show string` scrolls text across the 5×5 LED grid, one letter at a time.

---

### Step 3 — React to Button Presses

1. From **Input**, drag `on button A pressed` into the workspace
2. Inside it, put `show icon ❤️` (from **Basic**)
3. Add another `on button B pressed` block
4. Inside it, put `show icon 😃`

Click button A and B on the simulator to test.

> **What you learned:** `on button pressed` is an **event** — it waits for something to happen, then runs the code inside. This is how all interactive devices work: input → processing → output.

---

### Step 4 — Use the Accelerometer (Motion Sensor)

The micro:bit knows when you shake, tilt, or flip it.

1. From **Input**, drag `on shake` into the workspace
2. Inside it, put `show number` with a `pick random 1 to 6` block (from **Math**)

You just built a digital dice! Shake the micro:bit (or click "SHAKE" on the simulator) and it shows a random number.

> **What you learned:** The **accelerometer** is a sensor that detects motion and orientation. Your phone uses the same kind of sensor to know when you rotate it.

---

### Step 5 — Download to Your Real Micro:bit

1. Connect your micro:bit to your computer with the USB cable
2. Click **Download** in MakeCode
3. A `.hex` file will download
4. Drag the `.hex` file onto the **MICROBIT** drive that appears (it shows up like a USB drive)
5. The micro:bit's yellow LED will flash while it loads
6. When it stops flashing, your program is running!

> **✅ Checkpoint:** Your program runs on the real micro:bit. Press button A, button B, and shake it to test all three features.

---

### 🧠 Mini Lesson — Inputs, Processing, and Outputs

Every computer — from your phone to a Raspberry Pi to a micro:bit — follows the same pattern:

| Stage | What It Means | Micro:bit Examples |
|---|---|---|
| **Input** | Something comes in | Button press, shake, tilt, temperature, light level |
| **Processing** | The code decides what to do | If button A → show heart. If shake → pick random number. |
| **Output** | Something goes out | LED display, sound (V2), pins controlling motors/LEDs |

This **Input → Process → Output** loop is the foundation of all computing.

---

### 📝 Day 1 Deliverables

1. Screenshot of your MakeCode code with at least 3 different interactions (button A, button B, shake)
2. A photo or video of your micro:bit running your program

---

# Day 2: Build Your Project

**Goal:** Build one of the projects below (or invent your own) and present it.

---

### Pick a Project

Choose one from the list below, or combine ideas, or invent something entirely new:

---

**🎮 Project 1 — Rock Paper Scissors**

When you shake the micro:bit, it randomly picks rock, paper, or scissors and shows it on the display. Play against a friend who has another micro:bit!

Key blocks:
- `on shake`
- `set variable to pick random 0 to 2`
- `if variable = 0 then show icon ✊` (rock)
- `if variable = 1 then show icon ✋` (paper)
- `if variable = 2 then show icon ✌️` (scissors)

**What you'll learn:** Variables, conditionals (if/else), random numbers.

---

**🌡️ Project 2 — Temperature Alert**

Display the current temperature on the LEDs. If it goes above a threshold, show a warning icon and play a sound (V2).

Key blocks:
- `forever` loop
- `temperature (°C)` from Input
- `if temperature > 28 then show icon ⚠️`
- `else show number temperature`

**What you'll learn:** Sensor reading, comparison operators, forever loops.

---

**🧭 Project 3 — Compass**

Turn the micro:bit into a compass that shows which direction you're facing (N, S, E, W).

Key blocks:
- `forever` loop
- `compass heading (°)` from Input
- `if heading < 45 OR heading > 315 then show string "N"`
- Similar for S, E, W

**What you'll learn:** The compass sensor, range checking, directional logic.

---

**🎵 Project 4 — Musical Instrument (V2 only)**

Use the logo touch sensor and buttons to play different notes. Tilt the micro:bit to change the pitch.

Key blocks:
- `on logo pressed` → play note
- `on button A pressed` → play different note
- `on tilt left` → change pitch
- `forever` → read accelerometer for continuous pitch changes

**What you'll learn:** Sound output, touch input, continuous sensor reading.

---

**⏱️ Project 5 — Reaction Time Game**

The micro:bit shows a countdown (3, 2, 1) then displays a random icon. Two players race to press their button (A or B) first. The micro:bit shows who won.

Key blocks:
- `show number 3`, `pause 1000`, `show number 2`...
- `pause random 1000 to 3000` (random delay before the signal)
- `on button A pressed` → if game is active, player A wins
- Variables to track game state

**What you'll learn:** Game logic, timing, variables as state, competitive interaction.

---

**🎯 Project 6 — Step Counter**

Count how many steps you take by detecting the shake motion. Display the count on the LEDs. Press button A to reset.

Key blocks:
- `on shake` → increment steps variable
- `forever` → show number steps
- `on button A pressed` → set steps to 0

**What you'll learn:** Variables as counters, persistent state, reset functionality.

---

### Build It Step by Step

1. **Start with the simplest version** — just one input and one output
2. **Test on the simulator** — make sure it works virtually first
3. **Add features one at a time** — don't build everything at once
4. **Download to the real micro:bit** — test with real sensors
5. **Polish it** — add extra interactions, improve the display

---

### Optional: Switch to Python

MakeCode also supports Python! Click the **Python** toggle at the top of the editor to see your blocks as Python code. You can edit directly in Python too.

Example — the dice program in Python:

```python
def on_gesture_shake():
    basic.show_number(randint(1, 6))
input.on_gesture(Gesture.SHAKE, on_gesture_shake)
```

> **Why try Python?** Blocks are great for learning, but Python is what professionals use. Seeing how blocks translate to code is a great way to start learning a real programming language.

---

## 📝 Deliverables

1. **Your project code** — screenshot of MakeCode blocks (and Python version if you did it)
2. **A demo video** (30-60 seconds) showing your project running on the real micro:bit
3. **Reflection** (3-5 sentences): What did you build? What sensor or feature was most interesting? What would you add with more time?

---

## � How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | Screenshot of your MakeCode blocks (Day 1 — showing at least 3 interactions: button A, button B, shake) |
| 2 | Photo or video of your micro:bit running your Day 1 program |
| 3 | Screenshot of your Day 2 project code in MakeCode |
| 4 | Demo video (30–60 seconds) of your Day 2 project running on the real micro:bit |
| 5 | Your written reflection (3–5 sentences) |

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
| Working Project | 10 | Your project runs on the micro:bit and does what you intended |
| Complexity | 5 | Uses at least 2 inputs (buttons, sensors, shake) and has meaningful logic |
| Understanding | 5 | Reflection shows you understand Input → Process → Output |
| Deliverables | 5 | Code screenshot, demo video, and reflection submitted |

**Bonus:**
- **+3 points** for building in Python instead of (or in addition to) blocks
- **+2 points** for inventing your own project idea (not from the list)

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Micro:bit** | A pocket-sized programmable computer with built-in sensors, buttons, and LEDs |
| **MakeCode** | Microsoft's block-based editor for programming micro:bits (runs in browser) |
| **Accelerometer** | A sensor that detects motion, shaking, and tilt |
| **LED** | Light Emitting Diode — the 25 tiny lights on the micro:bit's 5×5 display |
| **Event** | Something that happens (button press, shake) that triggers code to run |
| **Variable** | A named container that stores a value (like a score or step count) |
| **Conditional** | Code that makes a decision: if this, then do that |
| **Sensor** | A component that detects something in the physical world (temperature, light, motion) |
| **Input** | Data coming into the computer (button press, sensor reading) |
| **Output** | Data going out of the computer (LED display, sound) |
| **.hex file** | The compiled program file that gets loaded onto the micro:bit |

---

## 💡 Troubleshooting

**"The micro:bit doesn't show up as a drive"**
→ Try a different USB cable. Some cables are charge-only and don't transfer data. If still nothing, try a different USB port.

**"My program works on the simulator but not on the real micro:bit"**
→ Make sure you downloaded the latest `.hex` file and dragged it to the MICROBIT drive. The yellow LED should flash during transfer.

**"The compass isn't working"**
→ The micro:bit needs to be calibrated first. When you first use the compass, it will ask you to tilt it around to draw a circle on the LEDs. Follow the instructions.

**"The temperature reading seems wrong"**
→ The temperature sensor measures the chip's temperature, not room temperature. It's usually a few degrees higher than the actual room temperature.

**"The sound blocks don't work"**
→ Sound is only available on micro:bit V2 (the one with the speaker and microphone built in). V1 needs an external speaker connected to pin 0 and GND.
