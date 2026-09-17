<!-- ===========================================================================
TEACHER PLANNING BLOCK — delete nothing, this never renders on the site.

UNIT / FOLDER   : capstone
FILE NAME       : web_project.md
PERIODS         : Block 3 build time, 5 or more depending on the student
FIRST TAUGHT    : T1 2026
CREATED         : 2026-09-17

WHAT THIS IS
Optional. Every student does a capstone. This is the guide for the ones who
choose to build something that runs in a browser: a game, an app, a tool, a
site. It is not a new graded item and it is not a requirement. It is the how-to
that sits beside capstone_proposal.md and capstone_project.md, the way the
robotics track has its own material. A student going the fabrication, robotics
or media route never opens this file.

WHY IT EXISTS
Amali's call, 2026-09-17. raspberry-pi/raspberry_pi_custom_website.md walks
every student through building one site start to finish. This file is the
second build, the one that is theirs, where nobody walks them through anything.
The two are deliberately different jobs and were briefly collapsed into one,
which did not work.

PREREQUISITE
raspberry-pi/raspberry_pi_custom_website.md. They have already built and hosted
a site once with instructions in front of them. Everything here assumes that.

GRADING
Graded by the existing capstone rubric, 100 points across It works 35, Skills
integration 25, Explains it 25, Creativity and ambition 15. If the student is
doing this as the standalone 25-point custom site instead, that assignment's
own rubric applies and this file is just extra guidance.

THE THING THAT WILL GO WRONG
Scope. Every single time. A student pitches Chess and has a board that does not
move by week three. The mitigations are in the file: a hard vertical-slice
requirement in week one, and a named fallback they agree to in advance.

FOLLOWING A TUTORIAL IS ALLOWED, WITH A CONDITION
Amali's call. A student building Chess may follow a YouTube or written Chess
tutorial. The condition is that they finish with something the tutorial did not
build, and they can explain the parts they typed. Otherwise the capstone is a
transcription exercise. The check is the same walkthrough as the custom site.

CHECKPOINTS TO ACTUALLY RUN
- End of week 1: the vertical slice runs, or we cut scope that day
- Mid Block 3: it survives somebody else using it
- Before the showcase: it is hosted and loads on a phone
=========================================================================== -->

# 🚀 Capstone: Build It for the Web

### Your idea, nobody's instructions, running at an address you can hand to anyone

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** Block 3 build time &nbsp;|&nbsp; **Difficulty:** It is up to you
>
> Everybody in this class does a capstone. This page is for the ones who want theirs to run in a browser. You have already built a site once with every step written out for you, so this is the one where nobody writes the steps: you pick the thing, you work out how to build it, and you ship it. If you have ever wanted to make a game, a tool, or an app that other people can actually open, here is where you do it.

---

## 🤔 Is This Your Capstone?

Your capstone can go several directions. Robotics and competition. Product and fabrication, on the laser cutter or the printers. Media and documentation. Or this one, software, where the thing you build runs in a browser.

**Pick this one if** you liked building your website more than you expected to, or you already have something in your head that you wish existed and it is a game, a tool, a page or an app.

**Do not pick this one** because it sounds easier. It is not. Ask anybody who has tried to make Chess work.

You are not locked in until your proposal is approved, so if you are torn, talk to Mr. Krigger before you commit.

---

## 🎯 What You'll Learn

- How to take an idea from a sentence to a working thing, which is harder than any single piece of code in it
- How to cut scope, the skill that decides whether a project ships or dies
- How to teach yourself something specific from a tutorial without ending up with code you cannot read
- How to keep a project alive over several weeks instead of one afternoon

---

## 🧰 What You Need

- **A finished custom website assignment.** This one assumes you have already built and hosted a site once
- VS Code on one of the Macs or the Windows laptop
- A jump drive
- Your Raspberry Pi, still running
- An approved capstone proposal saying this is what you are doing

---

## 💡 What Counts

Anything that runs in a browser and does something.

**Games.** Students in this class have built Chess, Tetris, Snake, Flappy Bird and Candy Crush. Go look at [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html). Those were built by people sitting where you are sitting.

**Tools.** A thing that does a job somebody actually has. A printer queue for the lab. A study timer. A grade calculator. A tide and conditions page. A hurricane prep checklist your family would use.

**Sites with something behind them.** A page that talks to your Pi. A scoreboard that survives a refresh. A page that pulls live data from somewhere.

**The bar for a capstone**, as opposed to a regular assignment: it does something real for somebody who is not you, and it is a genuine step past what you could already do in September. A page with your name and three photos on it is a fine assignment and not a capstone.

---

## 🛣️ Two Routes, Both Legitimate

**From scratch.** You know roughly how to build it and you want to work it out yourself. Slower at the start, and you will understand every line.

**Following a tutorial.** You want to build Chess, so you find a Chess tutorial and follow it. This is a real way to learn and professionals do it constantly.

**If you take the tutorial route, two conditions.**

1. **Finish somewhere the tutorial did not.** Add a feature, change how it works, restyle it completely, make it do something the video never mentioned. A capstone that ends exactly where a YouTube video ends is a transcription, not a project.
2. **You can explain what you typed.** Same walkthrough as last time. Mr. Krigger will point at parts of your code and ask what they do.

Tell Mr. Krigger which tutorial you are following on day one, so he can tell you if it is teaching you something from 2013.

> **Where to look:** [W3Schools](https://www.w3schools.com/) for a quick example, [MDN](https://developer.mozilla.org/) for the real explanation, [freeCodeCamp](https://www.freecodecamp.org/learn/responsive-web-design/) for a full course. For a specific build, search the thing plus "javascript tutorial" and pick one with a date on it.

---

## ⚠️ The AI Rule

Same as every assignment in this class, and it matters more here because the project is bigger.

**No AI until your first working version exists and Mr. Krigger has seen it.** After that you can use it to push further, with two conditions: you say what you used it for, and you can explain every line of it on demand.

On a capstone there is a third thing worth saying plainly. The capstone rubric gives 25 points for explaining your work and 15 for creativity and ambition. Neither of those can be generated. A project that was mostly typed by a machine scores badly on 40 of the 100 points before anybody looks at whether it runs.

---

# Week 1: Slice It

**Goal:** The smallest version of your project that actually runs.

---

### Step 1 — Name the vertical slice

A **vertical slice** is one thin piece of the finished thing, working end to end.

| Project | The slice | Not the slice |
|---|---|---|
| Chess | A board that draws, and one pawn you can move one square | All the pieces with legal move rules |
| A study timer | A countdown that starts, runs and stops | Presets, history, sound, settings |
| A printer queue | A list you can add one job to | Login, editing, deleting, dates |
| A trivia game | One question, one answer, one right or wrong | Categories, scores, a leaderboard |

The slice is not the easy part. It is the **whole path**, made narrow: something on screen, something you can do to it, something that happens back.

Write your slice down in one sentence. Show Mr. Krigger.

> **✅ Checkpoint:** A one-sentence slice, approved.

---

### Step 2 — Name your fallback now

Write down the version of your project you would be satisfied with if everything took twice as long as you think it will.

You are writing this now, while you are calm, because the day you need it you will not want to. Nearly every project runs long. Deciding in advance what you would cut is the difference between a finished smaller thing and an unfinished bigger one.

> **✅ Checkpoint:** A fallback version written down, agreed with Mr. Krigger.

---

### Step 3 — Build the slice

Folder named after the project. VS Code. Same shape you used last time:

```
chess/
├── index.html
├── styles.css
├── script.js
└── assets/
```

Then build the slice and nothing else. Not the menu. Not the colors. Not the sound effects. The slice.

> **✅ Checkpoint, end of week 1:** Your slice runs. Somebody else can do the one thing it does.

> **If the slice is not running at the end of week 1, that is information, not failure.** It means the project is bigger than the time. Go to your fallback that day, while there is still time for the fallback to be good.

---

# Weeks 2 and 3: Build It

**Goal:** From one thing that works to the thing you pitched.

---

No steps here. It is your project and nobody knows what it needs except you. What follows is how to work, not what to work on.

### Add one thing at a time, and keep it running

Working, change one thing, working, change one thing. If you change five things and it breaks you have five suspects. Keep a copy of the last version that worked, on your jump drive, every single period.

### Read the console every time something is wrong

**F12**, Console tab. It tells you what went wrong and roughly where. Guessing is slower than reading.

### Get somebody to use it every week

Not at the end. Every week. Hand them the laptop and say nothing, and write down where they get stuck. You cannot see your own project the way a stranger does, and by week three you will not even be able to remember trying.

### Check phone width every period

Drag the window narrow before you leave. A layout that collapses at 390px is cheap to fix today and expensive to fix the week of the showcase.

### Keep a short log

Two lines a period: what you did, what broke. When you write the explanation for the capstone rubric, this log is where that writing comes from, and reconstructing three weeks from memory is much worse than reading it.

> **✅ Checkpoint, mid Block 3:** Somebody else has used it and you have fixed what they found.

---

# Week 4: Ship It

**Goal:** A real address, and the words to explain what you built.

---

### Step 1 — Host it on your Pi

Exactly what you did last time. Jump drive to the Pi, `site_server.py` pointed at your folder, port 8000, then `hostname -I` for the address.

If you have forgotten a step, the walkthrough is in `raspberry-pi/raspberry_pi_custom_website.md`, Day 4. Looking up something you have done before is not cheating, it is Tuesday.

> **✅ Checkpoint:** Somebody loads it on their phone from across the room.

---

### Step 2 — Check it the way a stranger would

- [ ] Every image loads. A missing one is almost always a capital letter in a filename
- [ ] Every link goes somewhere
- [ ] It works on a phone
- [ ] A person who has never seen it knows what to do within a few seconds
- [ ] The console is clean

---

### Step 3 — Write the explanation

The capstone asks for a written document, and it is worth 25 of the 100 points. Cover:

- **What it does.** Plain words. No jargon you would have to explain
- **How it works.** The main pieces and how they fit together
- **Which skills you used**, and where. Name the file and roughly where in it
- **What went wrong** and how you worked it out. This section is the most interesting one and students always write the least here. A problem you solved is worth more than a feature that went smoothly
- **What you would add** with another month

---

### Step 4 — The walkthrough

Three minutes with your code open. Mr. Krigger points, you explain. Same as last time, higher bar, because this one is yours.

For anything AI touched: expect to change it live, while he watches.

---

## 🎚️ Base and Stretch

**Base — every capstone on this route.**

Your project runs, does what you pitched or what your fallback pitched, is hosted on your Pi and loads on a device that is not the Pi. You wrote the explanation. You can walk through your own code.

**Stretch — required for high school, bonus for middle school.**

**Something the browser cannot do on its own.** Your project has to reach past a single HTML page. Pick one:

- **Your own API route.** Add a route to `site_server.py` and have your page fetch it: a score that survives a refresh, a visit counter, live data from the Pi
- **State that persists.** The page remembers something after a reload, using `localStorage` or your server
- **Real data from somewhere else.** A public API you fetch from and display, chosen with Mr. Krigger since not all of them are appropriate or free
- **Your Pi's own hardware.** Your page reads or controls something physical through the Pi

---

## 📝 Deliverables

Everything the capstone already asks for, plus these:

1. **Your project folder**, all files
2. **`site_server.py`**
3. **The address** it was served at
4. **Screenshot** of it running on a device that is not the Pi, with the address bar visible
5. **Your written explanation**, the five sections above
6. **If you followed a tutorial:** which one, a link, and a paragraph on what you built that it did not

---

## 📋 How This Is Graded

By the capstone rubric, 100 points:

| Category | Points | What that means here |
|---|---|---|
| It works | 35 | It runs, it is hosted, somebody else can use it without you standing there |
| Skills integration | 25 | Two or more skills genuinely combined, or one pushed to real depth. HTML, CSS and JavaScript together counts if the JavaScript is doing real work |
| Explains it | 25 | The written document, plus the walkthrough |
| Creativity and ambition | 15 | Did you reach. A safe project done perfectly and an ambitious one that mostly works can score the same here |

> **Not doing this as your capstone?** You do not have to. Build something smaller as the standalone 25-point custom website instead, and then that assignment's rubric applies and this file is just extra help.

---

## 💡 Troubleshooting

**"I have no idea what to build"**
→ Go through [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html) and find the one you wish you had made. Build a different version of that. Nobody starts from nothing.

**"My project is too big and I know it"**
→ Good, that is the useful realization and most people have it too late. Go to your fallback. Today, not next week.

**"The tutorial I am following does something I do not understand"**
→ Stop and look up that one thing before you type more. A tutorial you are copying without understanding is building you a project you cannot defend.

**"It worked yesterday and now it does not"**
→ What changed? If you cannot say, that is the actual problem. Copy back the working version from your jump drive and redo the change one piece at a time.

**"I am stuck and I do not know what to search"**
→ Describe what you want in the plainest words you have, put the language first, and search that. "javascript make a square move when i press arrow keys" finds the answer.

**"It works on my laptop but not on the Pi"**
→ A capital letter in a filename, nearly every time. See the mini lesson in the custom website assignment, Day 4.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] No em dashes or other AI-sounding tells
- [x] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [x] Assumes the custom website assignment is already done
- [x] Tutorial route allowed, with the finish-past-it condition
- [x] Scope control is the spine: vertical slice, named fallback, week 1 gate
- [x] Graded by the existing capstone rubric, no new point values invented
- [ ] Add a card to the capstone section of the site if this gets published
=========================================================================== -->
