<!-- ===========================================================================
TEACHER PLANNING BLOCK. Delete nothing, this never renders on the site.

UNIT / FOLDER   : robotics
FILE NAME       : robomaster_navigate.md
PERIODS         : 3   (one period = 60-65 min)
FIRST TAUGHT    : T1 2026, rebuilt 2026-10-07 (the 2026 original was a one-period, six-slide version)

PREP THE DAY BEFORE
- [ ] Hardware charged / counted: RoboMaster S1, 4 working (about 4 more being repaired). HS crews of 4, MS crews of 3.
- [ ] Accounts or logins students need: NONE. Robots are activated on Mr. Krigger's account. Students never sign in to DJI (accounts are 18+).
- [ ] Software already on school iPads: RoboMaster app, robots paired and connecting.
- [ ] Printed or posted in the room: tape X start spot (same spot for every crew); number cards 1 to 5 from the kit, plus spares; Day 3 only: two tables set up before class and not moved.
- [ ] TEST EVERY BLOCK NAME ON THE iPAD BEFORE DAY 1. The page was written from DJI's programming guide, not from the app. Confirm: (a) which way 90 degrees sends the robot on the translate block, (b) the wording of the rotate block and its left/right dropdown, (c) the event block that fires on number markers, and how its dropdown lists numbers 1 to 5, (d) that the LED block says "set chassis (all) LED color to ...". Fix the site page and this file if the app words anything differently.
- [ ] Test the whole build myself end to end: {{ date }}

TIMING FOR DAY 1 (Circle)
- 5 min   Safety rules out loud, crews, tape X
- 10 min  Power on, connect, drive (no code yet)
- 10 min  Open Scratch, find blocks, run the four behavior tests
- 30 min  Plan the route on paper, build one piece at a time, tune
- 5 min   Screenshot, power off, back on the charger

TIMING FOR DAY 2 (Number Lights)
- 5 min   Start, finish Circle first if needed, new program
- 10 min  Enable marker identification, first card works
- 20 min  All five numbers, five colors
- 20 min  Stress tests: distance, light, angle, speed
- 5 min   Screenshot, put away

TIMING FOR DAY 3 (Figure 8)
- 5 min   Start, safety, tables already set
- 10 min  Sketch the figure 8, walk it
- 35 min  Build in four pieces, tune
- 10 min  Screenshot, exit ticket in Schoology

WHERE STUDENTS GET STUCK
- Robot turns left when they wanted right -> they skipped the Day 1 behavior tests. Send them back to Step 3.
- Circle ends 30 cm off the X -> the last side holds every earlier error. Fix the first piece that goes wrong, not the last.
- Numbers do nothing -> marker identification not enabled (it is off by default), or the card is outside the distance they set (0.5 to 3 m), or poor light.
- Two crews want the same colors -> fine, colors are their choice.
- One student does all the coding -> pass the iPad every run. Everyone submits their own screenshots.

IF THEY FINISH EARLY   : Stretch. Reverse Circle, Number moves, or Card chooses the course.
IF THEY NEED MORE TIME : Finish the Circle first, even if it eats into Day 2. Number Lights is a separate program so it can wait. Cut the Day 2 stress tests, not the five colors. The Figure 8 can slip a period.

ASSESSMENT
- Category  : Formal Assessments
- Points    : 25
- Exit ticket: robomaster_quiz.md, separate Schoology item
- Schoology : {{ due date }}   Section(s): MS 01YR and Comp Sci 01T1

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🤖 RoboMaster: Navigate the Room

### Make a robot drive a loop, read a card, and draw a figure 8 with nobody touching the controls

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 3 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> A parade starts and ends in the same place, and a robot can do that too, if you tell it exactly how. Over three days you program a RoboMaster S1 to loop the whole room and stop on the spot where it began, change its lights to match whichever number card you hold up, and drive a figure 8 around two tables. You write every instruction. The robot follows every one of them, including the wrong ones, with total confidence.

---

## 🎯 What You'll Learn

- How to **program** a robot to move by distance, time, and angle instead of steering it
- How to **plan, test, and fix** a route, changing one thing at a time
- How a robot uses its camera to **read a vision marker** and react to it
- Why a robot that does exactly what you said is not always doing what you meant

---

## 🧰 What You Need

- A **RoboMaster S1**, charged, and a school iPad with the RoboMaster app. Mr. Krigger has both ready.
- Open floor, tape on the floor for the start spot, and two tables for Day 3
- The number cards (1 to 5) from the robot kit
- Paper and a pencil for sketching your route

**You never sign in to anything.** The robots are already activated on Mr. Krigger's account. Do not create a DJI account and do not type a password into the app.

## ⚠️ Safety Rules: Read Before You Start

These are non-negotiable. Breaking them on purpose means you lose access to the robots and earn a 0 for the day.

1. **Say "clear" before you press Run.** Check that no feet, bags, or hands are near the robot, then say it out loud and wait for your crew to answer.
2. **One person holds the Stop button** every time the robot runs. Autonomous does not mean unsupervised.
3. **The robot lives on the floor.** Never run it on a table, a chair, or near stairs. Never carry it while the wheels are spinning.
4. **Leave the blaster alone.** This lesson never fires it.
5. **Batteries charge at the charging station** and nowhere else.
6. **Report damage, a burn smell, or an injury right away.** You will not be in trouble for reporting something. These are the only RoboMasters this class has.

---

## 👥 Your Crew and the Plan

You work in your competition crew, three or four people sharing one robot. **Pass the iPad around.** Every person writes and runs part of every program, because every person turns in their own code.

| Day | Mission | You finish with |
|---|---|---|
| Day 1 | The Circle: loop the room and come back | A robot that starts in one light color, drives around the room, and stops on the start spot in a different color |
| Day 2 | Number Lights: show a card, change the color | Numbers 1 to 5 each turn the robot a different color |
| Day 3 | The Figure 8: around two tables | A figure 8 that touches neither table and ends back on the start spot |

**What is fixed:** the three missions, the safety rules, and what you turn in. **What moves:** how you build each one. There is never just one right program. If the Circle takes you into Day 2, finish it first. Day 2 is built so you can.

---

# Day 1: The Circle

**Goal:** By the end of today your robot has started in one light color, driven a full loop around the room, and stopped back on the X in a different color.

**Start here:** pick up your crew's robot and iPad, say the safety rules out loud, and find the tape X on the floor. That is the start spot for every crew.

---

### Step 1: Wake it up and drive it

1. Press the button on the battery to power on the robot.
2. Open the **RoboMaster app** on the iPad and connect to the robot's own Wi-Fi network. It shows up in the iPad's Wi-Fi settings, and it is not the school network.
3. You should see the robot's camera on the screen.
4. Drive it with the on-screen joysticks: forward, backward, turn, and then push sideways. That one is different.

The wheels are **mecanum wheels**, which have small rollers set at an angle. Spin the four wheels in the right pattern and the robot slides in any direction without turning. A shopping cart cannot do that.

> **✅ Checkpoint:** You can see through the robot's camera and you have driven it forward, back, around, and sideways.

---

### Step 2: Open the code editor

1. In the app, go to **Lab**, then create a new **Scratch** program.
2. Find the **Chassis** blocks. The chassis is the body that moves.
3. Find the **LED** blocks.

| Block | What it does |
|---|---|
| `set chassis to translate at (0)° for (1) m` | Drives a set distance in the direction of the angle. 0° is forward. Longest allowed is 5 m. |
| `set chassis to translate at (0)° for (1) s` | Same, but for an amount of time instead of a distance |
| `set chassis to rotate (right) at (0)°` | Turns by that many degrees. Pick left or right in the block. |
| `set chassis translation speed to (0.5) m/s` | Sets how fast it drives. Start slow. |
| `set chassis (all) LED color to (green) and effect to (solid)` | Lights the robot in a color you choose |
| `wait (1) s` | Pauses the program |

---

### Step 3: Find out how it behaves

Before you plan a route, learn your robot. Build each test, run it, and write down what you saw. Mark the floor with tape so you can measure.

| Test | Question it answers |
|---|---|
| Translate at 0° for 1 m | Did it go one meter? Measure it. Run it three times. Does it land in the same place? |
| Rotate right 90° | Is it a right angle? Which way does a right turn go? |
| Translate at 90° for 1 m | Which way does 90° send it, left or right? Try −90° too. |
| Translate at 0° for 2 s | How far does two seconds take you? Is that the same as a distance block would give? |

**Several ways to do everything.** You can move by distance or by time. You can turn the whole robot, or slide it sideways without turning. You can drive an angled line with a single translate block. Nobody on this page is telling you which is best. Try more than one and keep the one that works for you.

> **✅ Checkpoint:** You know which way 90° goes, how far a 1 m block really drives, and what a right turn does.

---

### Step 4: The Circle mission

Your program must:

1. **Start** with the robot sitting on the tape X, with its LED set to a color you pick.
2. **Drive a complete loop around the room**, around the furniture and open floor Mr. Krigger marks out. The route is your design.
3. **Stop on the X.** As close as you can get.
4. **End in a different color** than you started. Set the LED to the new color as the last thing the program does.
5. Run on its own. Nobody touches the joysticks.

**Before any code:** walk the route yourself. Count your steps between the turns, and sketch a map on paper with the distance of each side and which way you turn. Programming a robot is giving directions to someone who follows them exactly. If you say 3 meters and the real answer is 4, it stops short and does not complain.

---

### Step 5: Build it a piece at a time

1. Start the program by setting the starting color.
2. Add the first side of the route. **Run it.** Where did the robot end up?
3. Add the first turn. **Run it again from the X.** Did it turn where you wanted?
4. Add the next side and repeat. Do not build the whole loop and then test it.
5. Last block: set the finish color.

A translate block drives at most 5 meters, so a long wall needs two blocks back to back. This is the shape of a program for a rectangular room. Your numbers will be different, because your room is not a perfect rectangle.

```
set chassis (all) LED color to (green) and effect to (solid)
set chassis translation speed to (0.5) m/s
set chassis to translate at (0)° for (3) m
set chassis to rotate (right) at (90)°
set chassis to translate at (0)° for (4) m
set chassis to rotate (right) at (90)°
... more sides, until you are back at the X ...
set chassis (all) LED color to (red) and effect to (solid)
```

---

### Step 6: It missed. Now fix it.

| What happened | Try this |
|---|---|
| It turned too far | Lower the angle a little, like 87° instead of 90° |
| It did not turn enough | Raise the angle a little |
| It stopped short of the corner | Make that side a bit longer |
| It drives past the corner | Make that side a bit shorter |
| It drifts to one side on a straight run | Slow it down, or add a small correction turn after the straight part |
| It ends near the X but not on it | Adjust the last side. This is the hardest one, because every earlier error is in it. |

**Change one thing, then run it again.** If you change five things and it gets better, you will not know which one did it. If you want to test whether a short `wait` block between a move and a turn helps, test that and nothing else, and keep it only if it does.

---

### 🧠 Mini Lesson: Why a robot drifts

Your robot has no map. It cannot see the room and decide where the wall is. It knows what you told it and roughly how far its wheels have turned, and that is all.

Wheels slip a little on a smooth floor and grip a little on a rough one. Each move is off by a small amount. The next move starts from that wrong spot and adds its own small error, so the errors **pile up**. That is why the last side of a long loop is the hardest to get right. Navigating by counting how far you have gone, with no map, is called **dead reckoning**. Sailors did it for centuries before anyone had GPS.

---

### 📝 Day 1 Deliverables

- [ ] The Circle works: starts in one color, loops the room, stops on the X in a different color
- [ ] A screenshot of your finished Circle program
- [ ] Robot powered off and back on the charging station, with the iPad

The Circle is **Precision Return**, one of the Open Events your crew can enter in the RoboMaster Competition.

---

# Day 2: Number Lights

**Goal:** By the end of today you can hold up a number card from 1 to 5 and the robot lights up a different color for each one.

**Start here:** finish the Circle first if it is not done. Collect your robot, iPad, and the number cards 1 to 5. Say the safety rules again, and someone new holds the Stop button. Start a **new** Scratch program. Do not build this one on top of the Circle.

---

### Step 1: A robot that can read

The RoboMaster has a camera and it can recognize **vision markers**: printed cards with a symbol on them. Number cards are one kind. Show it a card and it knows which one you showed it, with no joystick and no one telling it. The robot is not reading the word. It is matching a pattern, the same way a store scanner matches a barcode.

**It is switched off by default.** The robot will not look for markers until your program tells it to. If you build everything else correctly and nothing happens, this is the first suspect.

---

### Step 2: Turn on marker detection

| Block | What it does |
|---|---|
| `(enable) (vision marker) identification` | Turns on the robot's marker recognition. Put this first in your program. |
| `set vision marker identification distance to (1) m` | How far away the robot looks. It works between 0.5 and 3 meters. One meter is a good start. |
| `when ___ identified` | An **event** block. The blocks inside it run when the robot sees that marker. Open the dropdown and choose a number marker. |

Build one `when` event for the number 1, and inside it set the chassis LED to a color. Run the program and hold up the 1 card about a meter in front of the camera.

> **✅ Checkpoint:** You hold up the 1 and the robot's LED changes color.

---

### Step 3: All five numbers

Numbers 1 through 5 each get their own color. **You pick the colors.** They only have to be five different ones, so you can tell them apart from across the room. Test each one by itself, then flip through all five quickly. Does the robot keep up? Does the color change when you switch cards, and not before?

> **✅ Checkpoint:** Five cards, five different colors, every time.

---

### Step 4: Make it hard to fool

Real sensors fail in boring ways. Find your robot's limits before someone else does.

- **Distance.** Back away until it stops recognizing the card. How far is that? Does it match the distance you set?
- **Light.** Tilt the card toward a window, then into your own shadow. What happens?
- **Angle.** Hold the card a little crooked. How crooked can it be?
- **Speed.** Hold the card still for a second. A card waved past may never register.

---

### 🧠 Mini Lesson: How a robot sees

A camera gives the robot a picture, which to a computer is a grid of tiny colored dots. Looking for a marker means searching that grid for a pattern the robot already knows. When it finds one, it tells your program, and your program decides what to do. That is the same path a self-checkout scanner, a license plate reader, and a phone's face unlock all follow. It is also why a dim room or a crooked card can fool it: the pattern in the picture stops matching the pattern in its memory.

---

### 📝 Day 2 Deliverables

- [ ] Cards 1 to 5 each turn the robot a different color
- [ ] A screenshot of your Number Lights program
- [ ] You know how far away, and in what light, your robot recognizes a card

---

# Day 3: The Figure 8

**Goal:** By the end of today your robot drives a figure 8 around the two tables, touches neither one, and ends back on the start spot.

**Start here:** Mr. Krigger has set two tables on the floor. Do not move them. Everyone runs the same course. Open your Circle program. You have already built half of what you need.

---

### Step 1: The mission

A figure 8 is two loops joined at a crossing. The robot goes around one table one way, passes back through the middle, and goes around the other table the opposite way.

- Start on the X, in the middle between the tables
- Loop the first table, cross back through the middle, loop the second table the other way
- Finish on the X, and touch neither table

---

### Step 2: Why this is harder

In the Circle, every turn went the same direction. Here the robot turns one way on the first loop and the other way on the second. It also passes through the same spot twice, so any drift on loop one ruins the crossing and then loop two.

**Plan before you code.** Sketch the figure 8 on paper. Mark where the robot turns, which way, and how far each side is. Then walk the robot's path yourself, heel to toe.

**Build it in four pieces** and run each one before you add the next: loop one, the crossing, loop two, the finish. Your Circle program already knows how to loop. That is your starting point. You will change the turn directions for the second loop.

---

### Step 3: Build and tune it

1. Build loop one. Run it from the X. Does it clear the first table?
2. Add the crossing. Run it. Is the robot lined up for the second loop?
3. Add loop two with the opposite turns. Run it.
4. Adjust until it finishes on the X without touching a table.

**Same rule as Day 1: change one thing, then run it again.** If it drifts into a table, find the first piece where it went wrong and fix that piece. Do not fix the last piece first.

---

### 📝 Day 3 Deliverables

- [ ] The Figure 8 works: around both tables, touching neither, ending on the X
- [ ] A screenshot of your Figure 8 program
- [ ] Robot powered off and back on the charging station

The Figure 8 is the autonomous division of the **Figure 8 Grand Prix**, the other Open Event in the RoboMaster Competition.

---

## 🎚️ Base and Stretch

**Base: everyone does this.**
All three missions working. **The Circle:** starts in one color, loops the room, stops on the X in a different color. **Number Lights:** cards 1 to 5 each give a different color. **The Figure 8:** around both tables, touching neither, ending on the X. Your own code for each, and a reflection.

**Stretch: required for high school, bonus for middle school.**
Pick **two**.

- **Reverse Circle:** make the Circle run the other way around the room by changing as little as you can, and say what you changed.
- **Number moves:** card 5 also makes the robot spin once, as well as changing the color.
- **Card chooses the course:** show a 1 before the Figure 8 to loop the left table first, or a 2 to loop the right table first, and the robot decides on its own.

---

## 📝 Deliverables

1. **The Circle code.** A screenshot of your whole Scratch program. Show every block.
2. **The Number Lights code.** A screenshot of the whole program.
3. **The Figure 8 code.** A screenshot of the whole program.
4. **If you did a Stretch:** a screenshot of that code, and a sentence saying which one it is.
5. **Reflection** (3-5 sentences): which mission was hardest, what you changed to fix it, and what you would do differently if you started again.

There is no video and no test log. The code and the reflection are the work.

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | Screenshot of your Circle program |
| 2 | Screenshot of your Number Lights program |
| 3 | Screenshot of your Figure 8 program |
| 4 | Screenshot of your Stretch program, if you did one |
| 5 | Your written reflection (3-5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**. Do **NOT** click "Create" (Create is for text only and will not let you attach files)
4. Select your files and click **Submit**

The **exit ticket** is a separate Schoology item, taken in class. Both have to be done.

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| The Circle | 7 | Loops the room on its own, stops on or close to the X, starts and ends in different light colors |
| Number Lights | 6 | Marker identification is enabled, and cards 1 to 5 each give a different color |
| The Figure 8 | 7 | Around both tables, touches neither, ends on or close to the X |
| Code and Reflection | 5 | Your own code for all three missions is submitted, and the reflection shows you know why you changed what you changed |

**Bonus:**
- **+3 points** for a middle school student who completes two Stretch items (required of high school students)
- **+2 points** for a Stretch idea of your own that Mr. Krigger approves first

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Autonomous** | The robot runs on its program with nobody touching the controls |
| **Chassis** | The body of the robot that moves, wheels included |
| **Mecanum wheels** | Wheels with angled rollers that let the robot slide sideways and diagonally |
| **Scratch** | Code you build by snapping blocks together instead of typing it |
| **Translate** | Move in a straight line, in any direction, without turning |
| **Rotate** | Turn in place |
| **Dead reckoning** | Working out where you are by counting how far you have gone, with no map or GPS |
| **Vision marker** | A printed card with a symbol or number on it that the robot's camera recognizes |
| **Event block** | A block that waits for something to happen, like seeing a card, and then runs the blocks inside it |
| **Debugging** | Finding and fixing what is wrong with your program |
| **Iteration** | Test, change one thing, test again, until it works |

---

## 💡 Troubleshooting

**"The app will not connect to the robot."**
→ Check that the robot is powered on and that the iPad is on the robot's own Wi-Fi network, not the school network. If it still will not connect, ask Mr. Krigger before you try anything else. The robots are activated on his account.

**"My program runs but the robot barely moves."**
→ Check the distance and the speed. A tiny distance like 0.5 m is about one big step. A route around a room needs several meters.

**"It turns too far or not far enough."**
→ Floors change how a turn comes out. Adjust the angle a few degrees at a time and run it again. Change nothing else.

**"It turned left when I wanted right."**
→ Check the left or right choice in the rotate block. For sideways movement, run the 90° test from Day 1 Step 3 to see which side it sends you to.

**"It does not end on the X."**
→ Errors pile up over a long route, and the last side holds all of them. Fix the first place the robot goes wrong, then work toward the end.

**"The LED does not change color."**
→ Make sure the LED block is set to the chassis you are looking at, with the effect set to solid.

**"It never reacts to a number card."**
→ Three suspects. Did the program enable marker identification first? Is the card within the distance you set, at most 3 meters? Is the room bright enough that the camera can see the card clearly?

**"It reacts to the wrong number."**
→ Open each `when` block and check which marker is chosen in its dropdown. It is easy to build two blocks for the same number.

**"It hit a table."**
→ Press Stop, tell Mr. Krigger if anything is scratched, and move it back to the X. Then find the first piece of the program where the robot went off course. That is the piece to fix.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [ ] Every block name checked against the app on the iPad
- [ ] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [ ] Every checkpoint is something a student can actually see
- [ ] Base tier is readable by a 7th grader
- [ ] Safety block present
- [ ] Site version stands alone: rubric and Schoology steps stay in this file
=========================================================================== -->
