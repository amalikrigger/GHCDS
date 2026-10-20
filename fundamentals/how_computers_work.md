<!-- ===========================================================================
TEACHER PLANNING BLOCK. Delete nothing, this never renders on the site.

UNIT / FOLDER   : fundamentals
FILE NAME       : how_computers_work.md
PERIODS         : 2
FIRST TAUGHT    : T1 2026-27
SITE PAGE       : cs/fundamentals/how-computers-work/

PREP THE DAY BEFORE
- [ ] Hardware charged / counted: none for Day 1. Day 2 is a walk around the lab,
      so every machine should be visible and reachable, powered off is fine.
- [ ] Accounts or logins students need: none
- [ ] Software already on lab machines: a browser
- [ ] Headphones, or the sound activity played at low volume. Check that sound works on the lab machines.
- [ ] Netflix: the "Coding" episode of *Explained* needs a Netflix account. Decide whether
      students watch at home or in class, and whether you will have the account logged in.
- [ ] Printed or posted in the room: the four jobs, large, on the wall. It gets
      referenced in every unit after this one.
- [ ] Decide in advance what you will say the Glowforge stores. It is genuinely
      debatable and a student will ask.

TIMING FOR PERIOD 1 (the four jobs and binary)
- 5 min   Hook: name three machines in the room and ask what they have in common
- 12 min  The four jobs, then the table
- 15 min  Binary and the bits converter, students type their own names
- 15 min  The CPU stepper. Step it together on the projector first, then let them run it
          (the numbers-become-color, photo and sound activities and the cut-the-power demo
          are new and will push Period 1 long. Run color and one of photo or sound in class
          and leave the rest as work they can do when they finish)
- 10 min  Fast and stupid, tie back to password cracking, clean up

TIMING FOR PERIOD 2 (the lab audit)
- 5 min   Recap the four jobs, cold call
- 10 min  Walk the two worked examples together
- 25 min  Students audit five machines, moving around the room
- 10 min  The missing job paragraph, or the stretch
- 10 min  Share out the awkward ones, reflection, clean up

WHERE STUDENTS GET STUCK
- Memory vs storage is the one that does not stick on the first pass. The desk and
  filing cabinet works. Come back to it when someone loses unsaved work later in the term.
- "Is the loop a bug?" comes up every time. It is the moment to explain why the
  condition is checked each pass.
- The Glowforge storage question has no clean answer. That is the point, and a student
  who says "not sure, because" has done better than one who invents.
- MS students may need the binary section slowed down. The converter carries it better
  than talking does, so give them more time on the keyboard and less on you.

IF THEY FINISH EARLY   : the stretch, finding something that stores information without
                         being a computer. Answers include a printed page, a key, a lock,
                         and a filament spool with a label on it.
IF THEY NEED MORE TIME : the lab audit drops from five machines to three. Do not cut the
                         stepper, it is the part they remember.

ASSESSMENT
- Category  : Informal Assessments
- Points    : 25
- Exit ticket: separate Schoology Test/Quiz, `how_computers_work_quiz.md`
- Schoology : POSTED 2026-10-20, both sections, Fundamentals folder. Assignment 25 pts Informal Assessments, due Fri Oct 30 11:59 pm (HS 8616785848, MS 8616788344). Exit ticket 10 pts Formal Assessments, same due date (HS 8616279813, MS 8616286029). Grades not auto-published.

NOTE ON PLACEMENT
This is Fundamentals lesson 1 and it should stay first. Every later unit refers back to
the four jobs, and the micro:bit unit's input/process/output mini lesson becomes a recap
rather than a new idea.

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# ⚙️ How Computers Work

### Every machine in this room is the same machine wearing different clothes

> **Grades:** 7th to 12th &nbsp;|&nbsp; **Time:** 2 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> There is a 3D printer, a laser cutter, a robot, a tiny board with a screen made of lights, and a computer the size of a credit card in this room. They look nothing alike. Underneath, they are running the same four ideas, and once you can see those four ideas you stop being someone who uses machines and start being someone who understands them.

Full student version, including the bits converter and the program stepper, is on the
class website: **thinkinbits.site/cs/fundamentals/how-computers-work/**

---

## 🎯 What You'll Learn

- The four jobs every computer does: **input**, **processing**, **output**, **storage**
- Why everything inside is **binary**, and what that actually means
- How a **color**, a **photo** and a **sound** are all built from numbers, and how to change them
- The difference between **memory** and **storage**, which almost everyone gets wrong
- What a **program** is and what happens when one runs
- How to look at any machine in this lab and name its four jobs

---

## 🧰 What You Need

- A computer with a web browser
- Your eyes and the room. Day 2 is a walk around the lab.

---

# Day 1: The Four Jobs

**Goal:** you can explain what a computer is doing, in order, and you know why the answer to "what is it storing" is always numbers.

### Step 1: There are only four jobs

Input, processing, output, storage. Every computer ever built does these and nothing else. Everything beyond that is detail, size and speed.

### Step 2: It is all numbers, and there are only two of them

Switches, on or off, written 1 and 0. One switch is a **bit**. Eight make a **byte**, which holds 256 patterns, enough for every basic character to have its own number.

Students use the converter on the site to see their own name as bytes.

> **✅ Checkpoint:** they can read off the byte for one letter of their name.

**Numbers become color, a photo, and sound.** Three hands-on activities on the site, each followed by a short "What you just saw" panel:
- **Color:** red, green and blue are one byte each. Students move sliders and flip the eight switches (128, 64, 32 … 1) and watch the number and the color change. There is a Match game.
- **Photo:** a sunset with a sailboat shown as 4×4 up to 96×96 squares. Students read and edit one pixel's three numbers, and use Brighter, Invert and Gray to see that a filter is arithmetic on every number.
- **Sound:** students change how often the sound is measured and how precisely, draw their own wave, and listen. Tell them to turn the volume down first.

> **✅ Checkpoint:** they can make a color with lots of red and no green or blue, find the brightest pixel and read its three numbers, and hear why 1,000 measurements a second sounds worse than 44,100.

### Step 3: Memory and storage are not the same thing

RAM is the desk: fast, small, wiped when power stops. Storage is the filing cabinet: slower, bigger, survives being switched off. This is why unsaved work dies, and it is worth saying plainly, because it will happen to someone this term.

On the site, **Try it: cut the power** lets students type on the desk, save to the cabinet, cut the power and open the file back. Ask them to predict what survives before they press anything. Autosave shows why most apps rarely lose work now.

> **✅ Checkpoint:** they can say what survives a power cut and what they would have to do to keep the rest.

### Step 4: Watch a program actually run

The stepper on the site runs a real loop one instruction at a time, showing memory changing. It takes 20 steps to add four numbers. Students can turn the dial from 1 to 10 numbers and guess the step count first: it is always 4 steps per number plus 4 more.

> **✅ Checkpoint:** they can say why line 3 runs five times, even though the loop only goes round four times.

### 📝 Day 1 Deliverables
- [ ] Name converted to bits, screenshotted
- [ ] Made a color from its three numbers and read the numbers of one pixel
- [ ] Stepped the program to the end and can explain the loop

---

# Day 2: Audit the Lab

**Goal:** they can walk up to any machine in this room and name its four jobs out loud.

### Step 1 and 2: Same machine, different clothes

Two worked examples given (phone, MakerBot). A short **Warm-up: sort the parts** activity on the site then lets students tap the job each part of a Glowforge, RoboMaster S1, micro:bit, Raspberry Pi or laptop does, with a check. Students then audit the Glowforge, a RoboMaster, a micro:bit, a Raspberry Pi, and one machine not in this room.

Two are deliberately awkward: the micro:bit's storage is tiny and strange, and the RoboMaster's camera feeds decisions. Where a machine does not fit, that is the interesting part.

> **✅ Checkpoint:** five machines, four jobs each, and at least one honest "I am not sure, because".

---

## 🎚️ Base and Stretch

**Base, everyone does this.**
Five machines audited with four jobs each, plus a short paragraph: take one machine, remove one of its four jobs, and say what it becomes.

**Stretch, required for high school, bonus for middle school.**
Find something in this room that stores information without being a computer at all. Explain what it stores, how it survives losing power, and why it is not a computer.

---

## 📝 Deliverables

1. **Your name in bits**, screenshotted from the converter
2. **The lab audit**: five machines, four jobs each, including one from outside this room
3. **What did not fit**: one part or job that was hard to place, and why, in two sentences
4. **Your paragraph**: remove one job from one machine and say what it becomes. High school adds the stretch.
5. **Watch notes**: three sentences on *Explained*, "Coding" (Netflix, Season 2): one thing that surprised you, one thing that connects to the four jobs or to numbers, and one question you still have.
6. **Reflection** (3 to 5 sentences): what did you think a computer was before today, and what changed?

---

## 📤 How to Submit

Upload to **Schoology**, then take the exit ticket, which is a separate item.

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**. Do **NOT** click "Create", it will not let you attach files.
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Lab Audit | 10 | Five machines, four jobs each, accurate and specific |
| Handling the Awkward Ones | 5 | Named something that did not fit and said why, instead of inventing a tidy answer |
| Understanding | 5 | The paragraph shows they know what each job does, not just its name |
| Deliverables | 5 | Everything above submitted, on time |

**Bonus:**
- **+3 points** for a middle school student who completes the stretch
- **+2 points** for an audit of a machine nobody else in the class picked

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Bit** | One switch, on or off, written 1 or 0 |
| **Byte** | Eight bits, enough for one basic character |
| **Binary** | Counting with two digits, because a switch has two positions |
| **CPU** | The part that reads instructions and does them, one at a time, fast |
| **RAM** | Working memory. Fast, small, gone when power is |
| **Storage** | The drive. Slower, bigger, still there tomorrow |
| **Program** | A list of instructions, stored as numbers like everything else |
| **Loop** | Instructions that send the CPU back to repeat a section |
| **Pixel** | One square of a picture, stored as three numbers: red, green and blue |
| **Sample** | One measurement of a sound. A recording is thousands of them every second |

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] No em dashes or en dashes in student-facing text
- [x] Every checkpoint is something a student can actually see
- [x] Base tier is readable by a 7th grader
- [x] No safety block needed, this lesson touches no hardware in a hazardous way.
      Day 2 walks past machines but does not operate them.
- [ ] Site version: strip "How to Submit" and the rubric before publishing
=========================================================================== -->
