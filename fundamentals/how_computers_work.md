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
- [ ] Printed or posted in the room: the four jobs, large, on the wall. It gets
      referenced in every unit after this one.
- [ ] Decide in advance what you will say the Glowforge stores. It is genuinely
      debatable and a student will ask.

TIMING FOR PERIOD 1 (the four jobs and binary)
- 5 min   Hook: name three machines in the room and ask what they have in common
- 12 min  The four jobs, then the table
- 15 min  Binary and the bits converter, students type their own names
- 15 min  The CPU stepper. Step it together on the projector first, then let them run it
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
- Points    : 25 (proposed, awaiting sign off)
- Exit ticket: separate Schoology Test/Quiz, `how_computers_work_quiz.md`
- Schoology : ____   Section(s): both

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

### Step 3: Memory and storage are not the same thing

RAM is the desk: fast, small, wiped when power stops. Storage is the filing cabinet: slower, bigger, survives being switched off. This is why unsaved work dies, and it is worth saying plainly, because it will happen to someone this term.

### Step 4: Watch a program actually run

The stepper on the site runs a real loop one instruction at a time, showing memory changing. It takes 20 steps to add four numbers.

> **✅ Checkpoint:** they can say why line 3 runs four times before giving up.

### 📝 Day 1 Deliverables
- [ ] Name converted to bits, screenshotted
- [ ] Stepped the program to the end and can explain the loop

---

# Day 2: Audit the Lab

**Goal:** they can walk up to any machine in this room and name its four jobs out loud.

### Step 1 and 2: Same machine, different clothes

Two worked examples given (phone, MakerBot). Students then audit the Glowforge, a RoboMaster, a micro:bit, a Raspberry Pi, and one machine not in this room.

Two are deliberately awkward: the micro:bit's storage is tiny and strange, and the RoboMaster's camera feeds decisions. Where a machine does not fit, that is the interesting part.

> **✅ Checkpoint:** five machines, four jobs each, and at least one honest "I am not sure, because".

---

## 🎚️ Base and Stretch

**Base, everyone does this.**
Five machines audited with four jobs each, plus a paragraph on what the machine becomes if you remove one of its four jobs.

**Stretch, required for high school, bonus for middle school.**
Find something in this room that stores information without being a computer at all. Explain what it stores, how it survives losing power, and why it is not a computer.

---

## 📝 Deliverables

1. **Your name in bits**, screenshotted from the converter
2. **The lab audit**: five machines, four jobs each, including one from outside this room
3. **What did not fit**: at least one machine where a job was awkward to name, and why
4. **Your paragraph**: the missing job, or the stretch
5. **Reflection** (3 to 5 sentences): what did you think a computer was before today, and what changed?

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

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] No em dashes or en dashes in student-facing text
- [x] Every checkpoint is something a student can actually see
- [x] Base tier is readable by a 7th grader
- [x] No safety block needed, this lesson touches no hardware in a hazardous way.
      Day 2 walks past machines but does not operate them.
- [ ] Site version: strip "How to Submit" and the rubric before publishing
=========================================================================== -->
