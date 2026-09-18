<!-- ===========================================================================
TEACHER PLANNING BLOCK — delete nothing, this never renders on the site.

UNIT / FOLDER   : capstone
FILE NAME       : web_project.md
PERIODS         : Week 1 is 4 taught periods (build + host a working slice).
                  Weeks 2-4 are open Block 3 build time, length depends on the
                  student.
FIRST TAUGHT    : T1 2026
CREATED         : 2026-09-17
MERGED          : 2026-09-18. raspberry-pi/raspberry_pi_custom_website.md
                  ("Your First Real Website") is retired as its own 25-pt
                  assignment. Amali's call: only raspberry_pi_dashboard.md is
                  a mandatory grade out of the Pi unit. Every student already
                  gets real HTML/CSS exposure by restyling the dashboard, with
                  the theme packs and upgrade list built into that file. A
                  full from-scratch site is now something a student does only
                  if they choose it as their capstone, since doing both a
                  taught website unit and a separate capstone in one trimester
                  does not fit against everything else on the calendar. The
                  walkthrough's four taught days move into this file's Week 1,
                  so a student picking this route still gets every step
                  written out for the mechanics, then loses the scaffolding
                  once they are building their own idea. raspberry-pi/
                  raspberry_pi_custom_website.md still exists in git history
                  at commit 7097920 if any of its wording is ever needed again.

WHAT THIS IS
Optional. Every student does a capstone. This is the guide for the ones who
choose to build something that runs in a browser: a game, an app, a tool, a
site. It is not a separate graded item, it IS the capstone for that route. A
student going the fabrication, robotics or media route never opens this file.

WHY IT EXISTS
Two jobs used to live in two files: a taught walkthrough everyone did, and an
unguided capstone route a few students chose. Collapsed into one 2026-09-18
because keeping both cost more class time than the unit could afford. This
file now does both jobs itself: Week 1 teaches the mechanics the same way the
old walkthrough did, Weeks 2 through 4 are the old capstone route, applied to
the student's own idea from the start rather than a throwaway topic.

PREREQUISITE
raspberry_pi_dashboard.md only. They need a Pi already running Flask, to know
what a route is, and to have edited the dashboard's CSS once. This file is
their first full site build, not their second.

GRADING
Graded entirely by the existing capstone rubric, 100 points across It works 35,
Skills integration 25, Explains it 25, Creativity and ambition 15. No new point
values invented. There is no standalone grade path anymore.

THE THING THAT WILL GO WRONG
Scope. Every single time. A student pitches Chess and has a board that does not
move by week three. The mitigations are in the file: a hard vertical-slice
requirement in week one, and a named fallback they agree to in advance.

FOLLOWING A TUTORIAL IS ALLOWED, WITH A CONDITION
Amali's call. A student building Chess may follow a YouTube or written Chess
tutorial. The condition is that they finish with something the tutorial did not
build, and they can explain the parts they typed. Otherwise the capstone is a
transcription exercise. The check is the Day 4 / Week 4 walkthrough.

MACHINE COUNT
Lab computers as of 2026-09-16: two Macs and one Windows laptop. This file
spreads the build over weeks and only pulls in students who chose this route,
which is the thing that makes three machines workable where it was not for a
whole-section, four-day walkthrough. Amali is handling scheduling around this
herself.

CHECKPOINTS TO ACTUALLY RUN
- End of Week 1 (end of the four taught periods): the vertical slice runs, or
  we cut scope that day and move to the fallback
- Mid Block 3: it survives somebody else using it
- Before the showcase: it is hosted and loads on a phone

PREP THE DAY BEFORE WEEK 1 STARTS
- [ ] Jump drives available and formatted: ____ of ____ (FAT32 or exFAT so both
      Mac and Windows and the Pi can all read them)
- [ ] VS Code open and working on both Macs and the Windows laptop
- [ ] Each student's Pi still works from the dashboard assignment
- [ ] Test the whole build myself end to end: ____________

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🚀 Capstone: Build It for the Web

### Learn to build and host a real site, then use it to ship the thing that's actually yours

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 4 taught periods, then open build weeks &nbsp;|&nbsp; **Difficulty:** Starts guided, ends up to you
>
> Everybody in this class does a capstone. This page is for the ones who want theirs to run in a browser: a game, an app, a tool, a site. You do not need to have built a full website before. The first four periods teach you how, using your own idea from day one. After that, nobody writes the steps: you build it out, cut scope when you need to, and ship it at a real address.

---

## 🤔 Is This Your Capstone?

Your capstone can go several directions. Robotics and competition. Product and fabrication, on the laser cutter or the printers. Media and documentation. Or this one, software, where the thing you build runs in a browser.

**Pick this one if** you liked restyling your dashboard more than you expected to, or you already have something in your head that you wish existed and it is a game, a tool, a page or an app.

**Do not pick this one** because it sounds easier. It is not. Ask anybody who has tried to make Chess work.

You are not locked in until your proposal is approved, so if you are torn, talk to Mr. Krigger before you commit.

---

## 🎯 What You'll Learn

- How **HTML**, **CSS** and **JavaScript** split up the work across three files
- How to build a website from nothing, with no template to fill in
- How to move a project between computers without breaking it, and serve it from your Pi
- How to take an idea from a sentence to a working thing, which is harder than any single piece of code in it
- How to cut scope, the skill that decides whether a project ships or dies
- How to teach yourself something specific from a tutorial without ending up with code you cannot read
- How to keep a project alive over several weeks instead of one afternoon

---

## 🧰 What You Need

- A Mac or Windows computer to build on. A lab machine or your own laptop
- A jump drive
- Your Raspberry Pi, still working from the dashboard assignment
- A phone or second device to test on
- An approved capstone proposal saying this is what you are doing
- No accounts. No downloads. Nothing to sign up for.

---

## ⚠️ The AI Rule

Same as every assignment in this class, and it matters more here because the project is bigger.

**Build your first working version without AI.** No ChatGPT, no Claude, no Gemini, no Copilot writing your code. Watching somebody else solve a problem does not teach you to solve it. The fifteen minutes you spend staring at a broken layout before you work out why is where the learning actually happens.

**What you can use the whole time:**

- [W3Schools](https://www.w3schools.com/), which has a Try It Yourself box on almost every page
- [MDN Web Docs](https://developer.mozilla.org/) for the real explanations
- [freeCodeCamp Responsive Web Design](https://www.freecodecamp.org/learn/responsive-web-design/), free and self paced
- YouTube tutorials, Stack Overflow answers
- Your classmates, and Mr. Krigger
- [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html), where your classmates' work is

**Once your first working version exists and Mr. Krigger has seen it**, you can use AI to push further: better CSS, animations, a feature you could not figure out. Two conditions. You have to say what you used it for, and **you have to be able to explain every line of it on demand.** If you cannot walk through a section of your own code, that section does not count toward your grade.

One more thing worth saying plainly: the capstone rubric gives 25 points for explaining your work and 15 for creativity and ambition. Neither of those can be generated. A project that was mostly typed by a machine scores badly on 40 of the 100 points before anybody looks at whether it runs.

---

## 💡 What Counts

Anything that runs in a browser and does something.

**Something for an audience.** A page that runs at a booth or an event: spin-the-wheel, a trivia round, a live high score board, a costume vote, a photo wall.

**Something the lab or the school actually needs.** A printer queue for the lab. A tool checkout board. A RoboMaster battery tracker so nobody grabs a dead one again. A bell schedule that is readable from across the room.

**Something about here.** A hurricane prep checklist your family would really use. A carnival countdown. A page for a local business you like that does not have one. Tide and beach conditions. A food map of St. Croix.

**Games.** Students in this class have built Chess, Tetris, Snake, Flappy Bird and Candy Crush. Go look at [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html). Those were built by people sitting where you are sitting.

**Sites with something behind them.** A page that talks to your Pi. A scoreboard that survives a refresh. A page that pulls live data from somewhere.

**The bar for a capstone:** it does something real for somebody who is not you, and it is a genuine step past what you could already do in September. A page with your name and three photos on it is a fine assignment and not a capstone.

> **A full game is real work, not an afternoon.** Read the vertical slice section below before you pick Chess.

---

## 🛣️ Two Routes, Both Legitimate

**From scratch.** You know roughly how to build it and you want to work it out yourself. Slower at the start, and you will understand every line.

**Following a tutorial.** You want to build Chess, so you find a Chess tutorial and follow it. This is a real way to learn and professionals do it constantly.

**If you take the tutorial route, two conditions.**

1. **Finish somewhere the tutorial did not.** Add a feature, change how it works, restyle it completely, make it do something the video never mentioned. A capstone that ends exactly where a YouTube video ends is a transcription, not a project.
2. **You can explain what you typed.** Same walkthrough as everyone else gets. Mr. Krigger will point at parts of your code and ask what they do.

Tell Mr. Krigger which tutorial you are following before you start, so he can tell you if it is teaching you something from 2013.

---

# Week 1: Learn It, Then Build Your Slice

**Goal:** A folder with three files in it, a page in your browser, and by the end of the week, the smallest version of your idea running end to end.

---

### Day 1 — Sketch it, slice it, build the skeleton

Close the laptop. On paper, write:

1. One sentence: what is this and who is it for?
2. What are the three or four main chunks of the page, top to bottom?
3. What is the one thing on it that moves, changes, or responds when you click?

Then name your **vertical slice**: one thin piece of the finished thing, working end to end. Not the easy part, the *whole path*, made narrow: something on screen, something you can do to it, something that happens back.

| Project | The slice | Not the slice |
|---|---|---|
| Chess | A board that draws, and one pawn you can move one square | All the pieces with legal move rules |
| A study timer | A countdown that starts, runs and stops | Presets, history, sound, settings |
| A printer queue | A list you can add one job to | Login, editing, deleting, dates |
| A trivia game | One question, one answer, one right or wrong | Categories, scores, a leaderboard |

Then write down your **fallback**: the version of your project you would be satisfied with if everything took twice as long as you think it will. You are writing this now, while you are calm, because the day you need it you will not want to.

Show Mr. Krigger your sketch, your slice, and your fallback before you type anything.

> **✅ Checkpoint:** A sentence, a stack of sections, a one-sentence slice, and a fallback, all approved.

**Make your folder** on the Desktop, and **name it after your project**. Not `mysite`, not `project`.

| If you are building | Call the folder |
|---|---|
| Chess | `chess` |
| A tide and conditions page | `tide-check` |
| A printer queue | `print-queue` |

Lowercase, hyphens instead of spaces. Inside it, make three empty files and one folder:

```
chess/
├── index.html      ← the structure. What is on the page
├── styles.css      ← the look. Colors, fonts, spacing
├── script.js       ← the behavior. What happens when you click
└── assets/         ← images and anything else you use
```

**Two rules about filenames, and they matter more than they look:**

1. **All lowercase, no spaces.** `beach-photo.jpg`, never `Beach Photo.jpg`. Your Pi runs Linux, and Linux thinks `Photo.jpg` and `photo.jpg` are two different files. Mac and Windows do not, so a page that works perfectly on your laptop can break the moment it reaches the Pi.
2. **Everything you use lives inside your project folder.** Copy any image into `assets/` first. A file pulled straight from your Desktop will find it on this computer and nowhere else.

**Open it in VS Code.** File → Open Folder, pick your project folder. Turn on two things:

- **Word wrap:** `Alt + Z` on Windows, `Option + Z` on Mac
- **Auto save:** File → Auto Save

Put this in `index.html`:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Change This Title</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <header>
    <h1>Change this to what your project is</h1>
    <p>One sentence saying what it does.</p>
  </header>

  <main>
    <section>
      <h2>Section one</h2>
      <p>Replace all of this.</p>
    </section>
  </main>

  <footer>
    <p>Built by YOUR NAME, served from a Raspberry Pi.</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
```

**Keep the `<head>` exactly as it is.** Those five lines set the character encoding, make the page scale correctly on phones, and connect your CSS file.

Put this in `styles.css` to prove the connection works:

```css
body {
  background: #111;
  color: #eee;
  font-family: system-ui, sans-serif;
}
```

Double-click `index.html`. It opens in your browser straight off the disk, no server needed yet.

> **✅ Checkpoint:** Dark background, light text, your heading. White background means your CSS is not connected: check the filename and that it is in the same folder as `index.html`.

**Where students get stuck on Day 1:**
- A student who opens the wrong editor. VS Code only. It colors the code, underlines an unclosed tag, and does not silently save rich text the way TextEdit does.
- An image on the Desktop with the `src` pointing at the Desktop. Works on this computer, breaks on the Pi. Everything you use lives inside your project folder.

📝 **Day 1 done when:** sketch, slice, and fallback shown to Mr. Krigger; folder with three files opening in a browser with dark background; folder copied to your jump drive.

---

### Day 2 — Make it look like something

Everything today happens in `styles.css`. Save, refresh the browser, repeat.

**Colors and font, on purpose.** Generate a palette at [coolors.co](https://coolors.co/) and pick a font at [fonts.google.com](https://fonts.google.com/). Put your colors at the top as variables, so you can change your whole site in one place:

```css
:root {
  --bg: #0f1020;
  --text: #f2f2f2;
  --accent: #ff5d73;
}

body {
  margin: 0;
  padding: 24px;
  background: var(--bg);
  color: var(--text);
  font-family: system-ui, sans-serif;
  line-height: 1.6;
}

h1 { color: var(--accent); }
```

`--bg` is a variable. `var(--bg)` means "whatever that is set to." Change it once at the top and every place that uses it changes with it.

**Space things out.** Beginner sites almost always look cramped for the same three reasons:

```css
body { line-height: 1.6; }          /* space between lines of text */
section { margin-bottom: 48px; }    /* space between chunks */
main {
  max-width: 800px;                 /* stop text running the full screen width */
  margin: 0 auto;                   /* and center it */
}
```

**Make it work on a phone.** Squeeze your browser window as narrow as it goes and fix what breaks:

```css
img { max-width: 100%; height: auto; }
```

For a row of boxes, this one line handles every screen size:

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}
```

> **✅ Checkpoint:** Drag your window from full width down to as narrow as it goes. Nothing runs off the side, no sideways scrollbar at any width.

📝 **Day 2 done when:** your own colors and font, not the defaults; readable at full width and phone width; saved to your jump drive.

---

### Day 3 — Build your slice's interactive piece

A page that only sits there is a poster. This is the day your slice starts doing something.

**Learn the mechanism first.** In `index.html`:

```html
<button id="go">Click me</button>
<p id="output">Nothing yet.</p>
```

In `script.js`:

```javascript
const button = document.getElementById("go");
const output = document.getElementById("output");

button.addEventListener("click", function () {
  output.textContent = "You clicked it.";
});
```

Three lines, three ideas:

1. `getElementById` finds a thing on the page by its `id`
2. `addEventListener("click", ...)` says "when this gets clicked, run this"
3. `.textContent = ...` changes what it says

Almost everything interactive on the web is some version of those three.

**Learn to read the console before you need it.** The console is not just for when something breaks — it is how you find out *what* broke and *where*. Open it now: **F12** (or right-click the page → Inspect → Console tab).

Type this directly into the console and press Enter:

```javascript
document.getElementById("go")
```

It prints the button element back to you. The console is a live line into your page — you can ask it questions any time, not only when something crashes.

Now break something on purpose. In `script.js`, misspell the id — change `"go"` to `"gox"` — and click the button. The console shows something like:

```
Uncaught TypeError: Cannot read properties of null (reading 'addEventListener')
    at script.js:4
```

Read it in this order:

1. **`script.js:4`** — which file, which line. Click it and the browser jumps you straight there.
2. **`TypeError`** — the *kind* of mistake. This one means "I tried to use something that is not the type I expected."
3. **`Cannot read properties of null`** — `getElementById` came back empty-handed. No element had that id, so it handed back `null`, and `null` has no `.addEventListener` to call.

Wrong id → `null` → crash on the next line. That chain is the single most common bug in this unit. Once you can read it, you fix it in ten seconds instead of guessing for ten minutes.

A few other shapes worth recognizing:

| You'll see | It usually means |
|---|---|
| `ReferenceError: x is not defined` | You used a variable before creating it, or typo'd its name |
| `Uncaught SyntaxError: ...` | A typo in the code itself — a missing `}` or `)`, usually just above the line it names |
| `Cannot read properties of undefined` | Same idea as `null` above, one step removed — you are reaching *into* something that does not exist yet |
| Yellow text, not red | A warning — the page still runs, but something is off |
| Plain black text, no file:line | Your own `console.log(...)` output, not an error |

Fix your id back to `"go"` before you move on.

> **✅ Checkpoint:** Click the button, the text changes. If nothing happens, open the console, find the red line, and read it top to bottom using the steps above before you ask anyone for help.

**Now build your actual slice**, the one you named on Day 1. Some shapes and what to search for:

| Idea | The trick to search for |
|---|---|
| A piece that moves on click or keypress | `javascript move element on click` |
| Random pick (quote, fact, dare, name) | `javascript random array item` |
| Countdown to a date | `javascript countdown timer` |
| Score or tally that goes up | `javascript increment variable on click` |
| Filter a list of cards | `javascript filter list buttons` |
| Quiz with a score at the end | `javascript quiz score` |

**Break your own slice** before it goes further: click everything twice fast, click things out of order, make the window tiny, open it on your phone, hand it to the person next to you and say nothing. Fix what they find.

📝 **Day 3 done when:** your vertical slice does the one thing it is supposed to do; someone else has used it and you fixed what broke.

---

### Day 4 — Host it on your Pi

**Copy it over.** Jump drive into your Pi, drag the whole folder into your home folder, or from the Terminal:

```bash
cp -r /media/$USER/YOUR-DRIVE-NAME/chess ~/chess
ls ~/chess
```

> **✅ Checkpoint:** `ls` lists `index.html`, `styles.css`, `script.js`, `assets`.

**Write the server.**

```bash
nano ~/site_server.py
```

```python
from flask import Flask, send_from_directory
import os

SITE = os.path.expanduser("~/chess")

app = Flask(__name__)


@app.route("/")
def home():
    return send_from_directory(SITE, "index.html")


@app.route("/<path:filename>")
def other_files(filename):
    return send_from_directory(SITE, filename)


app.run(host="0.0.0.0", port=8000)
```

**Change `~/chess` on the `SITE` line to your own folder name.** Everything else is the same for everybody. Save: **Ctrl + O**, Enter. Exit: **Ctrl + X**.

> **Notice the port is 8000, not 5000.** Your dashboard owns 5000. Two servers cannot share a door, and now you can run both at once.

**Run it.**

```bash
source ~/pihealth/bin/activate
python3 ~/site_server.py
```

Check `http://localhost:8000` on the Pi first, then get your Pi's address:

```bash
hostname -I
```

Give someone `http://YOUR-PI-IP:8000` and watch them load it on their phone.

> **✅ Checkpoint, end of Week 1:** Your slice, running, loaded by somebody else on a device that is not the Pi. **If it is not running today, that is information, not failure.** Go to your fallback today, while there is still time for the fallback to be good.

**Check on that phone, not on the Pi:**
- [ ] Every image shows up
- [ ] Every link goes somewhere
- [ ] Your slice still works
- [ ] Nothing runs off the side of the screen

### 🧠 Why images break on the Pi and nowhere else

Your Mac or Windows computer is case-insensitive: it treats `Sunset.JPG` and `sunset.jpg` as the same file, so a typo in your `src` never shows up. Linux is case-sensitive, so to your Pi those are two unrelated files and one of them does not exist. Your site worked for three days and broke the minute it arrived, and you did nothing wrong. Every web developer gets bitten by this exactly once. Now you have had your once. The fix and the habit: all lowercase, hyphens instead of spaces.

---

# Weeks 2 and 3: Build It Out

**Goal:** From your slice to the thing you actually pitched.

---

No steps here. It is your project and nobody knows what it needs except you. What follows is how to work, not what to work on.

**Add one thing at a time, and keep it running.** Working, change one thing, working, change one thing. If you change five things and it breaks you have five suspects. Keep a copy of the last version that worked, on your jump drive, every single period.

**Read the console every time something is wrong.** F12, Console tab. It tells you what went wrong and roughly where. Guessing is slower than reading.

**Get somebody to use it every week.** Not at the end. Hand them the laptop and say nothing, and write down where they get stuck. You cannot see your own project the way a stranger does, and by week three you will not even remember trying.

**Check phone width every period.** Drag the window narrow before you leave. A layout that collapses at 390px is cheap to fix today and expensive to fix the week of the showcase.

**Keep a short log.** Two lines a period: what you did, what broke. When you write the explanation for the capstone rubric, this log is where that writing comes from.

> **✅ Checkpoint, mid Block 3:** Somebody else has used it and you have fixed what they found.

**If you took the tutorial route:** by now you should be past where the tutorial left off. If you are still typing what the video says with nothing of your own added, stop and add something before you go further.

---

# Week 4: Ship It

**Goal:** A real address, and the words to explain what you built.

---

### Step 1 — Check it the way a stranger would

- [ ] Every image loads. A missing one is almost always a capital letter in a filename
- [ ] Every link goes somewhere
- [ ] It works on a phone
- [ ] A person who has never seen it knows what to do within a few seconds
- [ ] The console is clean

### Step 2 — Write the explanation

The capstone asks for a written document, worth 25 of the 100 points. Cover:

- **What it does.** Plain words, no jargon you would have to explain
- **How it works.** The main pieces and how they fit together
- **Which skills you used**, and where. Name the file and roughly where in it
- **What went wrong** and how you worked it out. This section is the most interesting one and students always write the least here. A problem you solved is worth more than a feature that went smoothly
- **What you would add** with another month
- **If you followed a tutorial:** which one, a link, and a paragraph on what you built that it did not

### Step 3 — The walkthrough

Three minutes with your code open. Mr. Krigger points, you explain.

- Point at a block of CSS: "what happens if I delete this?"
- Point at a function: "what calls this?"
- "Why is this file in this folder?"
- "What breaks if the Pi restarts?"
- For anything AI touched: "change this, now, while I watch."

**You cannot revise for this.** It is a conversation about a thing you built, so if you built it you will be fine.

---

## 🎚️ Base and Stretch

**Base — every capstone on this route.**

Your slice grew into your project. It runs, does what you pitched or what your fallback pitched, is hosted on your Pi, and loads on a device that is not the Pi. Your own colors and structure, not a template with the words changed. No horizontal scrolling at phone width. You wrote the explanation and can walk through your own code.

**Stretch — required for high school, bonus for middle school.**

Something the browser cannot do on its own. Pick one:

- **Your own API route.** Add a route to `site_server.py` and have your page fetch it: a score that survives a refresh, a visit counter, live data from the Pi.

```python
import random

ITEMS = ["Put your own list here.", "At least three items.", "They can be anything."]


@app.route("/api/random")
def random_item():
    return {"item": random.choice(ITEMS)}
```

  Then in `script.js`, `fetch("/api/random")` and use the result. Check the route on its own in a browser tab first, before touching the page.

- **State that persists.** The page remembers something after a reload, using `localStorage` or your server.
- **Real data from somewhere else.** A public API you fetch from and display, chosen with Mr. Krigger since not all of them are appropriate or free.
- **Your Pi's own hardware.** Your page reads or controls something physical through the Pi.

---

## 📸 Getting Your Work Ready

### Taking the screenshots

**On the Pi.** Press **Print Screen**. If nothing happens, open **Menu → Accessories** and look for **Screenshot**.

**On your phone.** iPhone is **Side button + Volume Up**. Android is **Power + Volume Down**.

**On a lab computer.** Mac is **Cmd + Shift + 4**, then drag a box. Windows is **Windows + Shift + S**, then drag a box and paste it into any app to save.

> Full guide for every device: [How to Take and Submit Screenshots](../fundamentals/how_to_screenshot.md)

**Make sure the address bar is in the shot.** Your screenshot has to prove *where* the page was loaded from, not just that a page loaded.

### Getting it uploaded

**Your files and your Pi screenshot: submit from the Pi.** Open Chromium on the Pi, log in to Schoology, open the assignment, Submit Assignment → Upload, and browse to your project folder.

**Your phone screenshot:** email it to yourself, AirDrop it, or log in to Schoology in your phone's browser and upload straight from the camera roll.

**If the Pi will not cooperate:** copy the folder to your jump drive, take it to a lab computer, submit from there.

**Name your files so they are readable:** `krigger-chess-index.html`, `krigger-chess-on-phone.png`.

---

## 📝 Deliverables

1. **Your working code** — the whole project folder, every file it needs to run (`index.html`, `style.css`, `script.js`, anything else it depends on)
2. **`site_server.py`** — the script that hosted it
3. **The address** it was served at, like `http://10.0.4.71:8000`
4. **Screenshot** of it running on a device that is not the Pi, address bar visible
5. **Screenshot** of your project folder on the Pi
6. **Your written explanation**, the five sections above
7. **If you followed a tutorial:** which one, a link, and what you built that it did not

Submissions with a written explanation but no working code, or code but no explanation, are incomplete — both parts are required.

---

## 📋 How This Is Graded

By the capstone rubric, 100 points:

| Category | Points | What that means here |
|---|---|---|
| It works | 35 | It runs, it is hosted, somebody else can use it without you standing there |
| Skills integration | 25 | Two or more skills genuinely combined, or one pushed to real depth. HTML, CSS and JavaScript together counts if the JavaScript is doing real work |
| Explains it | 25 | The written document, plus the walkthrough |
| Creativity and ambition | 15 | Did you reach. A safe project done perfectly and an ambitious one that mostly works can score the same here |

**Bonus:** **+3 points** for a middle school student who completes the Stretch.

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Vertical slice** | One thin piece of the finished thing, working end to end |
| **Fallback** | The smaller version of your project you agree to build if the real one runs long |
| **Static file** | A file the server hands over unchanged: an HTML page, a stylesheet, an image |
| **Port** | The door number on a computer. Your dashboard uses 5000, this project uses 8000 |
| **Route** | A line like `@app.route("/api/random")` saying which request a function answers |
| **Relative path** | A path starting from where the file is, like `assets/photo.jpg`. Works anywhere the folder goes |
| **Case sensitive** | Linux treats `Photo.jpg` and `photo.jpg` as different files. Mac and Windows do not |
| **CSS variable** | A named color or size defined once in `:root` and reused with `var(--name)` |
| **Event listener** | Code that waits for something to happen, like a click, and then runs |
| **Console** | The browser panel that shows your JavaScript errors. **F12** |
| **Responsive** | A page that works at any screen width without a separate phone version |

---

## 📚 Where to Look Things Up

| | |
|---|---|
| [W3Schools](https://www.w3schools.com/) | Start here. Try It Yourself box on almost every page |
| [MDN Web Docs](https://developer.mozilla.org/) | The real explanation, when W3Schools is not enough |
| [freeCodeCamp Responsive Web Design](https://www.freecodecamp.org/learn/responsive-web-design/) | Free, self paced, from zero |
| [Coolors](https://coolors.co/) | Color palettes |
| [Google Fonts](https://fonts.google.com/) | Free fonts |
| [Unsplash](https://unsplash.com/) | Free photos you are allowed to use |
| [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html) | What your classmates built |

---

## 💡 Troubleshooting

**"My CSS is not doing anything"**
→ Is `styles.css` in the same folder as `index.html`? Is the `<link>` line in the `<head>` spelled exactly right? Did the file save as `styles.css` and not `styles.css.txt`?

**"My browser shows the code as text instead of the page"**
→ The file is not really an `.html` file. Look at the tab name in VS Code. If it says `index.html.txt`, rename it in the sidebar.

**"My images worked on the laptop and not on the Pi"**
→ A capital letter. Check the filename in your `src` matches the actual file exactly, letter for letter. Rename everything to lowercase.

**"Address already in use"**
→ Something is already on that port. Your dashboard is probably on 5000, this project is on 8000. If 8000 is also taken, `pkill -f site_server.py` and start again.

**"My JavaScript does nothing"**
→ Press F12 and read the Console. "null is not an object" means `getElementById` could not find that id, so the name in your HTML and the name in your JS do not match. Also check `<script src="script.js"></script>` is the last thing before `</body>`.

**"The page loads but it is the old version"**
→ Hard refresh: **Ctrl + Shift + R**.

**"Nothing loads from my phone"**
→ Is the phone on GHCDS? Is the server still running on the Pi? Did you type `:8000` after the IP?

**"I cannot find my jump drive on the Pi"**
→ `ls /media/$USER/` lists what is plugged in. If it is empty, unplug and replug, then wait a few seconds.

**"I deleted something and now it is all broken"**
→ Your jump drive has yesterday's copy. This is exactly why you save to it at the end of every period.

**"I have no idea what to build"**
→ Go through [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html) and find the one you wish you had made. Build a different version of that. Nobody starts from nothing.

**"My project is too big and I know it"**
→ Good, that is the useful realization and most people have it too late. Go to your fallback. Today, not next week.

**"The tutorial I am following does something I do not understand"**
→ Stop and look up that one thing before you type more. A tutorial you are copying without understanding is building you a project you cannot defend.

**"It worked yesterday and now it does not"**
→ What changed? If you cannot say, that is the actual problem. Copy back the working version from your jump drive and redo the change one piece at a time.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] No em dashes or other AI-sounding tells
- [x] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [x] No default pi/raspberry login assumed anywhere, every path uses ~ or $USER
- [x] Port 8000, so it does not collide with the dashboard on 5000
- [x] Merges the walkthrough's taught days (was raspberry_pi_custom_website.md)
      with the capstone route's scope-control spine, per Amali 2026-09-18
- [x] Tutorial route allowed, with the finish-past-it condition
- [x] Scope control is the spine: vertical slice, named fallback, week 1 gate
- [x] Graded entirely by the existing capstone rubric, no new point values
- [ ] Update the site page (cs/capstone/web-project/) to match this merge
- [ ] Remove the retired cs/raspberry-pi/first-website/ page and its grid card
=========================================================================== -->
