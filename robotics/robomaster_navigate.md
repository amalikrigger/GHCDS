# 🤖 RoboMaster: Navigate the Room

### Program a robot to drive around the entire room and back to the start

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 1 class period &nbsp;|&nbsp; **Difficulty:** Beginner
>
> You'll learn to operate a RoboMaster robot, then write a Scratch program that drives it in a full loop around the classroom — starting and ending at the same spot. No joystick. Just your code.

---

## 🎯 What You'll Learn

- How to connect and control a RoboMaster robot
- How to program movement using **Scratch blocks** in the RoboMaster app
- How to **estimate distances and angles** for real-world navigation
- How to **test, debug, and adjust** code based on what actually happens

---

## 🧰 What You Need

- A **RoboMaster S1** robot (charged and assembled)
- A phone or tablet with the **RoboMaster app** installed
- Open floor space in the classroom
- A piece of tape to mark the start/finish spot

---

## Part 1: Get Familiar (10 minutes)

### Step 1 — Connect Your RoboMaster

1. Power on the RoboMaster (press the button on the battery)
2. Open the **RoboMaster app** on your phone or tablet
3. Connect to the robot's Wi-Fi network (it will appear in your Wi-Fi settings)
4. Once connected, you should see the camera feed from the robot

> **✅ Checkpoint:** You can see through the robot's camera on your screen.

---

### Step 2 — Practice Driving

Before coding, learn how the robot moves by driving it manually:

1. In the app, use the **joystick controls** to drive around
2. Try driving forward, backward, turning left, and turning right
3. Get a feel for how fast it moves and how wide its turns are

> **Tip:** The RoboMaster can also move sideways (it has mecanum wheels). Try pushing the joystick left and right!

---

### Step 3 — Explore the Tutorials (Optional but Recommended)

The RoboMaster app has built-in tutorials that teach you how the robot works:

1. In the app, look for **"Road to Mastery"** or **"Academy"** in the menu
2. Work through 2-3 beginner lessons to learn about movement, sensors, and shooting
3. These tutorials are great for understanding what the robot can do

> **Why bother?** The tutorials teach you commands you can use in your navigation program. The more you know, the better your code will be.

---

## Part 2: The Challenge (30 minutes)

### The Mission

Program your RoboMaster to:

1. **Start** at a taped spot on the floor
2. **Drive a complete loop** around the classroom (or a large section of it)
3. **Return** to the exact starting spot
4. Do all of this **autonomously** — no joystick, just your Scratch code running

---

### Step 1 — Plan Your Route

Before writing any code, walk the route yourself and think about it:

1. Stand at the starting spot and look around the room
2. Decide which direction to go first
3. Count your steps between each turn — this helps estimate distances
4. Note every turn: is it a 90° left turn? A slight right? A U-turn?

**Sketch your route on paper.** Draw a simple map with arrows showing:
- How far to go before each turn
- Which direction to turn
- How many segments there are

> **Why plan first?** Programming a robot is like giving directions to someone who follows them EXACTLY. If you say "go forward 2 meters" but it's actually 3 meters, the robot will stop short. Planning saves you debugging time.

---

### Step 2 — Open Scratch Programming Mode

1. In the RoboMaster app, go to **Lab** or **Programming**
2. Select **Scratch** (block-based coding)
3. You should see a workspace with draggable blocks

---

### Step 3 — Learn the Key Blocks

Here are the blocks you'll use most:

| Block | What It Does |
|---|---|
| **Chassis move forward ___ m at ___ m/s** | Drives straight for a set distance |
| **Chassis rotate ___ degrees** | Turns the robot left (negative) or right (positive) |
| **Wait ___ seconds** | Pauses between moves (helps with accuracy) |
| **Chassis move left/right ___ m** | Slides sideways (useful for adjustments) |

**Start simple.** Try this first:

1. Drag a **"move forward 0.5m"** block into your program
2. Hit **Run** and watch the robot move
3. Did it go the distance you expected? Adjust the number if needed

> **✅ Checkpoint:** You can make the robot move forward a specific distance using a single block.

---

### Step 4 — Build Your Program Step by Step

Build your route one segment at a time:

1. **Code the first segment** (e.g., "move forward 2m")
2. **Run it** and see where the robot ends up
3. **Add the first turn** (e.g., "rotate 90 degrees")
4. **Run again** from the start — does it turn at the right spot?
5. **Add the next segment** and repeat

> **Key tip:** Add a **"wait 0.5 seconds"** block between each move and turn. This gives the robot time to fully stop before starting the next action, which makes it more accurate.

**Example program for a rectangular room:**

```
[When start is pressed]
  Chassis move forward 3m at 0.5 m/s
  Wait 0.5 seconds
  Chassis rotate 90 degrees
  Wait 0.5 seconds
  Chassis move forward 5m at 0.5 m/s
  Wait 0.5 seconds
  Chassis rotate 90 degrees
  Wait 0.5 seconds
  Chassis move forward 3m at 0.5 m/s
  Wait 0.5 seconds
  Chassis rotate 90 degrees
  Wait 0.5 seconds
  Chassis move forward 5m at 0.5 m/s
  Wait 0.5 seconds
  Chassis rotate 90 degrees
```

> **Your room won't be a perfect rectangle**, so your program will be different. You'll need to measure, estimate, test, and adjust. That's the engineering process!

---

### Step 5 — Test and Debug

This is where the real learning happens. Your first attempt will NOT be perfect — and that's normal.

**Common issues and fixes:**

| Problem | Fix |
|---|---|
| Robot overshoots a turn | Decrease the rotation degrees (try 85° instead of 90°) |
| Robot doesn't go far enough | Increase the distance in the move block |
| Robot goes too far | Decrease the distance |
| Robot drifts to one side | Add a small correction turn (2-3°) after the straight section |
| Robot doesn't end at the start spot | Adjust the last segment's distance — this is the hardest part! |

> **Think like an engineer:** Every test run gives you data. Write down what happened, adjust ONE thing, and test again. Don't change 5 things at once — you won't know which fix actually worked.

---

## Part 3: Optional Extras (if you finish early)

Finished the basic navigation? Try these bonus challenges:

### 🎯 Challenge 1 — Target Shooting
Place a target (like a paper on the wall) along your route. Program the robot to stop, aim the blaster, fire, and then continue driving.

### 🔊 Challenge 2 — Sound Effects
Add a block that plays a sound or speaks text at each checkpoint. ("Turning left!" or a victory sound when it arrives back at start.)

### 💡 Challenge 3 — LED Light Show
Program the robot's LED lights to change color at different points in the route — green when moving, yellow when turning, red when it arrives back.

### 🏎️ Challenge 4 — Speed Run
Once your program works at slow speed, gradually increase the speed. How fast can you go before it starts missing turns?

### 🧠 Challenge 5 — Figure Eight
Instead of a loop around the room, program a figure-eight pattern in an open area.

---

## Part 4: Competition Mode (Optional — Extra Credit)

### 🏆 The RoboMaster Grand Prix

Think your navigation code is dialed in? Prove it. This is a class-wide competition with two events.

---

### Event 1 — The Precision Return

All teams run their room navigation program. The winner is the robot that stops **closest to the starting tape mark** after completing the full loop.

**Rules:**
- Everyone uses the same route (the full room loop)
- The robot must move autonomously — no joystick, no touching the robot mid-run
- After the robot stops, measure the distance from the front of the robot to the tape mark (in centimeters)
- Lowest distance wins
- If two teams tie, the faster completion time breaks the tie

**Scoring:**

| Finish Distance | Points |
|---|---|
| Within 10 cm | 🥇 +5 bonus points |
| Within 30 cm | 🥈 +3 bonus points |
| Within 60 cm | 🥉 +2 bonus points |
| Completed the loop | +1 bonus point |

---

### Event 2 — The Obstacle Gauntlet

The teacher sets up 3 obstacles along a straight path (cones, boxes, or chairs). Teams must program their robot to navigate around all 3 obstacles and cross a finish line.

**Rules:**
- The course is revealed at the start — no pre-programming allowed
- Teams get **10 minutes** to write their program
- Each team gets **2 attempts** — best run counts
- Hitting an obstacle = 5-second penalty added to your time
- Fastest adjusted time wins

**Scoring:**

| Result | Points |
|---|---|
| Fastest time | 🥇 +5 bonus points |
| Second fastest | 🥈 +3 bonus points |
| Third fastest | 🥉 +2 bonus points |
| Completed the course | +1 bonus point |

---

### Event 3 — Fastest to the Blue Marker

A blue marker is placed somewhere in the room. All teams start from the same spot. The first robot to reach the blue marker wins.

**Rules:**
- The blue marker location is revealed at the start — no pre-programming allowed
- Teams get **5 minutes** to write their program
- Each team gets **1 attempt** — plan carefully
- The robot must stop within 30 cm of the marker to count as a finish
- If the robot doesn't stop (drives past it), it doesn't count
- Fastest time from pressing Run to stopping at the marker wins

**Scoring:**

| Result | Points |
|---|---|
| Fastest time | 🥇 +5 bonus points |
| Second fastest | 🥈 +3 bonus points |
| Third fastest | 🥉 +2 bonus points |
| Reached the marker | +1 bonus point |

---

### 🎮 Design Your Own Competition (+3 Extra Credit)

Want even more points? **Design your own RoboMaster competition** that the class could play. Submit:

1. **A name** for your competition
2. **The rules** (1 paragraph — what does the robot have to do?)
3. **How to win** (what's being measured — speed, accuracy, creativity?)
4. **A simple sketch** of the course or setup

If your competition is good enough, we might actually run it in class!

---

## 📝 Deliverables

1. **A video** of your RoboMaster completing the room navigation (start to finish, back at the start spot)
2. **A screenshot** of your Scratch program in the app
3. **A short reflection** (3-5 sentences): How close did your robot get to the starting spot? What was the hardest part to get right? How many test runs did it take?
4. *(If competing)* Your competition results will be recorded in class
5. *(If designing a competition)* Your competition name, rules, win condition, and sketch

---

## � How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | Video of your RoboMaster completing the room navigation (start to finish, back at the start spot) |
| 2 | Screenshot of your Scratch program in the RoboMaster app |
| 3 | Your written reflection (3–5 sentences) |

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
| Route Planning | 5 | Thought through the route, estimated distances and angles |
| Working Program | 5 | Robot moves autonomously through the full route |
| Accuracy | 5 | Robot returns close to the starting spot |
| Testing & Debugging | 5 | Evidence of iterating — you didn't just run it once |
| Deliverables | 5 | Video, screenshot of code, and reflection submitted |

**Bonus:** Up to +5 points for competition placement, +3 points for designing your own competition, +50 points for building/assembling a new RoboMaster from scratch.

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Autonomous** | The robot moves on its own using code, not a joystick |
| **Scratch** | A block-based visual programming language |
| **Chassis** | The base/body of the robot that moves |
| **Mecanum Wheels** | Special wheels that let the robot move in any direction (forward, sideways, diagonal) |
| **Debugging** | Finding and fixing problems in your code |
| **Iteration** | Testing, adjusting, and testing again until it works |
| **Degrees** | A unit of rotation — 90° is a right angle turn, 180° is a U-turn, 360° is a full spin |

---

## 💡 Troubleshooting

**"The robot won't connect"**
→ Make sure the robot is powered on and your device is connected to the robot's Wi-Fi network, not the classroom Wi-Fi.

**"My program runs but the robot barely moves"**
→ Check that your distances aren't too small. `0.5m` is about one step. The room might need moves of `2-5m`.

**"The robot turns too much or too little"**
→ Floors can be slippery or sticky, which affects turns. Adjust by a few degrees at a time (try 87° instead of 90°).

**"The robot doesn't come back to the start"**
→ Small errors add up over a long route. Go back through each segment and fine-tune distances and angles. This is the hardest and most rewarding part!
