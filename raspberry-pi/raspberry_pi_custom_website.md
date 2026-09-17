<!-- ===========================================================================
TEACHER PLANNING BLOCK — delete nothing, this never renders on the site.

UNIT / FOLDER   : raspberry-pi
FILE NAME       : raspberry_pi_custom_website.md
PERIODS         : 4
FIRST TAUGHT    : T1 2026
REWRITTEN       : 2026-09-16, to the LESSON_TEMPLATE standard.
RESTORED        : 2026-09-17. A 2026-09-16 second pass moved this file's whole
                  walkthrough out into a separate tutorial and left this one
                  with no steps for Days 2 and 3. Amali reversed it. The file
                  is back to the 2026-09-16 version with four additions: VS
                  Code, the project-named folder, the Schoology section, and
                  the walkthrough as Day 4 Step 5. Title changed to "Your First
                  Real Website" because the old one promised a site nobody
                  walks you through, which is now capstone/web_project.md.

WHO DOES THIS
Everyone, both sections. This is the walkthrough: four periods where every step
is written out and every student ends with a site of their own choosing, live on
their Pi. Prerequisite: raspberry_pi_dashboard.md. They need a Pi already
running Flask and to know what a route is.

The topic stays open, Amali's call. A student picks what the site is about and
the steps scaffold whatever they picked. What separates this from
capstone/web_project.md is scale and scaffolding, not topic freedom: here every
step is given and the scope is four periods, there nothing is given and the
scope is weeks. An oversized idea gets routed to the capstone by the "If Your
Idea Is Bigger Than Four Periods" section, which is the thing that stops a
student starting Chess on a Tuesday.

WHERE THE WORK HAPPENS
Students AUTHOR on a Mac or Windows computer in a real editor, and the Pi HOSTS.
Files move over on a jump drive on Day 4. Amali's call, and it is the right one:
nano is fine for a 40-line server and miserable for a 200-line site.

MACHINE COUNT IS THE REAL PROBLEM NOW
Lab computers as of 2026-09-16: two Macs and one Windows laptop. Three machines
cannot run a 16-student section through a four-day build. This was survivable
when the file was a track option for a handful of students. It is not, now that
everyone does it.

Options, none of them free:
- Students bring their own laptops. Days 1 to 3 need no Pi and no network, so
  any machine with a browser and a text editor works, and VS Code is free.
- Pair them. Two students per machine, one driving and one navigating, swapping
  every fifteen minutes. This is a real professional practice and it halves the
  machine need, at the cost of each student typing half as much.
- Stagger it. Half the section does Days 1 to 3 while the other half does
  something else, then swap.
- Run Days 1 to 3 as homework and use class time for Day 4 and help.
Decide before this is scheduled. It is the single thing most likely to sink the
assignment, and it is a logistics problem rather than a teaching one.

PREP THE DAY BEFORE
- [ ] Jump drives available and formatted: ____ of ____ (FAT32 or exFAT so both
      Mac and Windows and the Pi can all read them)
- [ ] VS Code open and working on both Macs and the Windows laptop
- [ ] Accounts or logins students need: none
- [ ] Each student's Pi still works from the dashboard assignment
- [ ] Test the whole build myself end to end: ____________

TIMING FOR DAY 1
- 8 min   Show three finished student sites from thinkinbits.site/projects.html
- 7 min   They write down what they are building and sketch it on paper. No
          computer yet. A student who opens an editor with no plan builds
          nothing for two periods.
- 5 min   I look at every sketch and say yes or narrow it
- 35 min  Folder, three files, skeleton HTML, open it in a browser
- 5 min   Save to jump drive, clean up

WHERE STUDENTS GET STUCK
- A student who opens the wrong editor. VS Code only. It colors the code,
  underlines an unclosed tag, and does not silently save rich text the way
  TextEdit does. That is most of why we use it.
- Image is on the Desktop and the src points at the Desktop. Works on their
  machine, breaks on the Pi. Say: everything you use lives inside your site
  folder, or it does not exist.
- Capital letters in filenames. Photo.jpg and photo.jpg are the same file on
  Mac and Windows and different files on the Pi. This one is invisible until
  Day 4 and then everything breaks at once. Say it on Day 1.
- Port 5000 is the dashboard. This site is on 8000, deliberately.

IF THEY FINISH EARLY   : The Stretch. Then a second page with working nav.
IF THEY NEED MORE TIME : Day 4 is the fixed one, since it needs the Pi and the
                         jump drive. Days 1 to 3 can stretch or move home.

ASSESSMENT
- Category  : Formal Assessments
- Points    : 25
- Schoology : due date ____________   Sections: both (MS 01YR and Comp Sci 01T1)
- May be combined with the capstone with approval. Mark it "Approved as Combo"
  on the proposal review, same as any other combo.

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🌐 Your First Real Website

### Your idea, built step by step, live at an address you can hand to anyone

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 4 class periods &nbsp;|&nbsp; **Difficulty:** Intermediate
>
> You already know how to make a Raspberry Pi serve a web page, because you did it. That one came with the code written out for you. This one is your idea. You decide what the site is, and the four days below walk you through every step of building it on a real computer with a real editor, carrying it to your Pi, and serving it. When you are done, somebody can type an address into their phone and see a thing that did not exist before you made it.

---

## 🎯 What You'll Learn

- How to build a website from nothing, with no template to fill in
- How to look things up and figure them out, which is the actual job
- How **HTML**, **CSS** and **JavaScript** split up the work across three files
- How to move a project between computers without breaking it
- How to serve your own site from your Pi on a port you choose

---

## 🧰 What You Need

- A Mac or Windows computer to build on. A lab machine or your own laptop
- A jump drive
- Your Raspberry Pi, still working from the dashboard assignment
- A phone or second device to test on
- No accounts. No downloads. Nothing to sign up for.

---

## ⚠️ The One Rule: No AI Until It Works

**Build your first working version without AI.** No ChatGPT, no Claude, no Gemini, no Copilot writing your code.

Watching somebody else solve a problem does not teach you to solve it. The fifteen minutes you spend staring at a broken layout before you work out why is where the learning actually happens, so skipping it leaves you with a site and no skill.

**What you can use the whole time:**

- [W3Schools](https://www.w3schools.com/), which has a Try It Yourself box on almost every page
- [MDN Web Docs](https://developer.mozilla.org/) for the real explanations
- YouTube tutorials, Stack Overflow answers
- Your classmates, and Mr. Krigger
- [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html), where your classmates' work is

**Once your site works and Mr. Krigger has seen it**, you can use AI to push it further: better CSS, animations, a feature you could not figure out. Two conditions. You have to say what you used it for, and **you have to be able to explain every line of it on demand.** If you cannot walk through a section of your own code, that section does not count toward your grade. This is the same standard the syllabus sets for every assignment in this class.

---

## 🤝 If Your Idea Is Bigger Than Four Periods

Some ideas do not fit in four class periods. Chess. A full game. An app with accounts. That is not a problem with the idea, it just means the idea is a capstone.

Two ways that can go:

**Build something smaller here and save the big one.** You still do these four days, because they are how you learn to build and host a site at all. Your big idea then gets weeks instead of days, and a guide of its own at **`capstone/web_project.md`**.

**Or combine them.** One build, both grades, if the idea is strong enough and you commit to it now. Bring it to Mr. Krigger and get it marked **Approved as Combo** on your proposal review, before you start building rather than after.

"Strong enough" means it does something real for somebody who is not you, and it is a genuine step past what you could already do.

---

## 💡 What Should You Build?

Your call. Here are four directions, and none of them is the right answer.

**Something for an audience.** A page that runs at a booth or an event: spin-the-wheel, a trivia round, a live high score board, a costume vote, a photo wall. A page for a team or club you are in.

**Something the lab or the school actually needs.** A 3D printer queue. A tool checkout board. A RoboMaster battery tracker so nobody grabs a dead one again. A bell schedule that is readable from across the room. Lost and found.

**Something about here.** A hurricane prep checklist your family would really use. A carnival countdown. A page for a local business you like that does not have one. Tide and beach conditions. A food map of St. Croix.

**Something that is just yours.** A portfolio. A link-in-bio page. A fan page for an artist, a game, a team. A quiz or trivia game. A countdown to something you care about. A playable game, and yes, people in this class have built Chess, Tetris, Snake, Flappy Bird and Candy Crush before you, so that bar exists and it is reachable.

> **A full game is a capstone, not four periods.** If Chess is what you want, read the section above before you pick it.

> **Go look at [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html) before you decide.** Every one of those was made by someone sitting where you are sitting.

---

# Day 1: Decide, Then Build the Skeleton

**Goal:** A folder with three files in it, and a page in your browser that already says what it is.

---

### Step 1 — Sketch it on paper first

Close the laptop. On paper, write:

1. One sentence: what is this and who is it for?
2. What are the three or four main chunks of the page, top to bottom?
3. What is the one thing on it that moves, changes, or responds when you click?

Show Mr. Krigger before you type anything. This takes five minutes and saves you two periods.

> **✅ Checkpoint:** A sketch with a sentence, a stack of sections, and one interactive thing circled.

---

### Step 2 — Make your folder

Make a folder on the Desktop, and **name it after your project**. Not `mysite`, not `project`, not `website`.

| If you are building | Call the folder |
|---|---|
| Chess | `chess` |
| A Carnival countdown | `carnival-countdown` |
| A page about your band | `stormcrew` |

Lowercase, hyphens instead of spaces. When fifteen people hand in a folder called `mysite`, nobody can find anything, including you in six months.

The examples below all say `chess`. Use your own name wherever you see it. Inside the folder, make three empty files and one folder:

```
chess/
├── index.html      ← the structure. What is on the page
├── styles.css      ← the look. Colors, fonts, spacing
├── script.js       ← the behavior. What happens when you click
└── assets/         ← images and anything else you use
```

**Two rules about filenames, and they matter more than they look:**

1. **All lowercase, no spaces.** Use `beach-photo.jpg`, never `Beach Photo.jpg`. Your Pi runs Linux, and Linux thinks `Photo.jpg` and `photo.jpg` are two different files. Mac and Windows do not. So a page that works perfectly on your laptop can break the moment it reaches the Pi, and the error will not tell you why.
2. **Everything you use lives inside your project folder.** If you drag in a photo from your Desktop, the page will find it on this computer and nowhere else. Copy the file into `assets/` first.

---

### Step 3 — Open it in VS Code

**File → Open Folder**, pick your project folder, and the whole thing appears in the sidebar.

Open the folder, not the file. VS Code works out what your project is from the folder and starts helping you: colors get a swatch beside them, a tag you have not closed gets underlined, and typing `<` offers a list of real tags.

Two things to turn on right now:

- **Word wrap:** `Alt + Z` on Windows, `Option + Z` on Mac. Long lines stop running off the screen.
- **Auto save:** **File → Auto Save**. Now you never refresh the browser and wonder why nothing changed.

> **✅ Checkpoint:** Your three files are in the VS Code sidebar and clicking one opens it.

---

### Step 4 — Write the skeleton

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
    <h1>Change this to what your site is</h1>
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

**Keep the `<head>` exactly as it is.** Those five lines set the character encoding, make the page scale correctly on phones, and connect your CSS file. Everything between `<body>` and `</body>` is yours to replace.

Put this in `styles.css` so you can prove the connection works:

```css
body {
  background: #111;
  color: #eee;
  font-family: system-ui, sans-serif;
}
```

Now **double-click `index.html`**. It opens in your browser straight off the disk. No server needed yet.

> **✅ Checkpoint:** Dark background, light text, your heading. If the background is white, your CSS is not connected: check that `styles.css` is spelled exactly right, and that it is in the same folder as `index.html`.

---

### Step 5 — Fill in your sections

Build out the chunks from your sketch. The tags that do most of the work:

| Tag | What it does |
|---|---|
| `<h1>` to `<h6>` | Headings, `h1` is the biggest. One `h1` per page |
| `<p>` | A paragraph |
| `<img src="assets/photo.jpg" alt="what it shows">` | An image. The `alt` text is what a screen reader says |
| `<a href="https://example.com">text</a>` | A link |
| `<ul>` with `<li>` inside | A bullet list |
| `<div class="card">` | A box you can style. The `class` is the name you use in CSS |
| `<button>` | Something to click |
| `<section>` | A chunk of the page |

> **Do not know how to do something?** Search it the way a developer does: put the language first. "css center a div", "html add a background image", "javascript change text on click". W3Schools first, MDN when you want the real answer.

---

### 📝 Day 1 Deliverables

- [ ] Your sketch, shown to Mr. Krigger
- [ ] Your project folder with three files, opening in a browser, dark background proving CSS is connected
- [ ] The folder copied to your jump drive before you leave

---

# Day 2: Make It Look Like Something

**Goal:** Nobody can tell it was a template.

---

Everything today happens in `styles.css`. Save, then refresh the browser. Save, refresh. That loop is the whole day.

### Step 1 — Pick your colors and your font on purpose

Generate a palette at [coolors.co](https://coolors.co/) and pick a font at [fonts.google.com](https://fonts.google.com/). Then put your colors at the top of `styles.css` with names, so you can change your whole site in one place:

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

---

### Step 2 — Space things out

Beginner sites almost always look cramped for the same three reasons. Fix all three:

```css
body { line-height: 1.6; }          /* space between lines of text */

section { margin-bottom: 48px; }    /* space between chunks */

main {
  max-width: 800px;                 /* stop text running the full screen width */
  margin: 0 auto;                   /* and center it */
}
```

That third one does more for how a page reads than any color choice. Text that runs 1400 pixels wide is exhausting to read and nobody can say why.

---

### Step 3 — Make it work on a phone

Squeeze your browser window as narrow as it goes. Whatever breaks, fix now. The usual culprits:

```css
img { max-width: 100%; height: auto; }   /* images that stay inside the screen */
```

If you have a row of boxes, this one line handles every screen size:

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 16px;
}
```

"As many columns as fit, each at least 220px wide." Three columns on a laptop, one on a phone, and you did not write a rule for either.

> **✅ Checkpoint:** Drag your window from full width down to as narrow as it goes. Nothing runs off the side. No sideways scrollbar at any width.

---

### 📝 Day 2 Deliverables

- [ ] Your own colors and font, not the defaults
- [ ] Readable at full width and at phone width
- [ ] Saved back to your jump drive

---

# Day 3: Make It Do Something

**Goal:** One thing on the page responds to a person.

---

A page that only sits there is a poster. One interactive thing makes it a site.

### Step 1 — Wire up a button

In `index.html`:

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

> **✅ Checkpoint:** Click the button, the text changes. If nothing happens, open the browser console (**F12**, then the Console tab) and read the red text. It will tell you which name it could not find.

---

### Step 2 — Build your actual interactive thing

The one you circled on your sketch. Some shapes that are within reach in one period:

| Idea | The trick to search for |
|---|---|
| Random pick (quote, fact, dare, name) | `javascript random array item` |
| Countdown to a date | `javascript countdown timer` |
| Score or tally that goes up | `javascript increment variable on click` |
| Dark mode toggle | `javascript toggle class` |
| Show and hide a panel | `javascript toggle display` |
| Filter a list of cards | `javascript filter list buttons` |
| Quiz with a score at the end | `javascript quiz score` |

---

### Step 3 — Break your own site

Before it goes on the Pi, try to break it, because someone else will.

- Click everything twice, fast
- Click things in the wrong order
- Make the window tiny
- Open it on your phone
- Hand it to the person next to you and say nothing

Fix what they find.

---

### 📝 Day 3 Deliverables

- [ ] At least one working interactive thing
- [ ] Someone else has used it and you fixed what they broke
- [ ] Saved to your jump drive

---

# Day 4: Move It to the Pi and Serve It

**Goal:** A real address, on a real server, that a real person can visit.

---

### Step 1 — Copy it over

Put your project folder on your jump drive. Plug the drive into your Pi. It shows up in the file manager.

**Drag the whole folder into your home folder.** Done. Or, from the Terminal:

```bash
cp -r /media/$USER/YOUR-DRIVE-NAME/chess ~/chess
```

Check it arrived:

```bash
ls ~/chess
```

> **✅ Checkpoint:** `ls` lists `index.html`, `styles.css`, `script.js` and `assets`. If the folder is missing or empty, the drag did not finish. Do it again and wait for it.

---

### Step 2 — Write the server

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

**Change `~/chess` on the `SITE` line to your own folder name.** That one line is the only thing in this file that is about your project. Everything else is the same for everybody.

Save: **Ctrl + O**, Enter. Exit: **Ctrl + X**.

> **Notice the port is 8000, not 5000.** Your dashboard owns 5000. Two servers cannot share a door. Now you can run both at once. Ports exist for this.

---

### Step 3 — Run it

```bash
source ~/pihealth/bin/activate
python3 ~/site_server.py
```

On the Pi, open `http://localhost:8000`.

> **✅ Checkpoint:** Your site. The one you built on a different computer, now being served by a Raspberry Pi.

---

### Step 4 — Hand someone the address

Get your Pi's IP:

```bash
hostname -I
```

Give someone the address `http://YOUR-PI-IP:8000` and watch them load it on their phone.

> **✅ Checkpoint:** Somebody who is not you, on a device that is not yours, looking at your site.

**Now check everything, on that phone, not on the Pi:**

- [ ] Every image shows up. A missing one is almost always a capital letter in a filename
- [ ] Every link goes somewhere
- [ ] Your interactive thing still works
- [ ] Nothing runs off the side of the screen

---

### 🧠 Mini Lesson — Why images break on the Pi and nowhere else

Your Mac or Windows computer is case-insensitive. It treats `Sunset.JPG` and `sunset.jpg` as the same file, so a typo in your `src` never shows up.

Linux is case-sensitive. To your Pi, those are two unrelated files, and one of them does not exist.

So your site worked perfectly for three days and broke the minute it arrived, and you did nothing wrong. Every web developer gets bitten by this difference between operating systems exactly once. Now you have had your once.

**The fix and the habit:** all lowercase, hyphens instead of spaces. `beach-photo.jpg`.

---

### Step 5 — The walkthrough

Some time on Day 4, you and Mr. Krigger sit down with your code open for about three minutes. He points at parts of it and asks what they do.

**You cannot revise for this.** It is a conversation about a thing you built, so if you built it you will be fine.

Roughly what gets asked:

- Point at a block of CSS: "what happens if I delete this?"
- Point at a function: "what calls this?"
- "Why is this file in this folder?"
- "What breaks if the Pi restarts?"
- For anything AI helped with: "change this, now, while I watch."

That last one is why the AI rule has a second condition. If you understand what you shipped, changing it live takes ten seconds.

---

### 📝 Day 4 Deliverables

- [ ] Your site loading from your Pi on somebody else's device
- [ ] Walkthrough done
- [ ] Everything on that checklist above, confirmed

---

## 🎚️ Base and Stretch

**Base — everyone does this.**

A site you designed, with at least three real sections of your own content, your own colors and font, at least one thing that responds to a click, no horizontal scrolling at phone width, served from your Pi on port 8000 and loading on a device that is not the Pi.

**Stretch — required for high school, bonus for middle school.**

**Give your site its own API.** Right now every word on your page was typed into the HTML by you. Add a route to `site_server.py` that sends back data, and have your page fetch it. That is the difference between a page on a server and an actual web app.

Add this above the last line of `site_server.py`:

```python
import random

JOKES = ["Put your own list here.", "At least three items.", "They can be anything."]


@app.route("/api/random")
def random_item():
    return {"item": random.choice(JOKES)}
```

Then in `script.js`:

```javascript
async function loadItem() {
  const response = await fetch("/api/random");
  const data = await response.json();
  document.getElementById("output").textContent = data.item;
}
```

Restart the server and check `http://YOUR-PI-IP:8000/api/random` in a browser first. **If the JSON is not there, fix that before touching the page.** Always check the server on its own before blaming the page.

**Random jokes is the worked example, so make it something your site actually needs.** A live count of how many people have visited. The Pi's uptime, so the page can say how long it has been up. A tip that changes every hour. Anything where the answer should come from the server instead of being frozen into the HTML.

---

## 📝 Deliverables

1. **Your site folder**: `index.html`, `styles.css`, `script.js`, and `assets/` if you used it
2. **`site_server.py`**
3. **The address** your site was served at, like `http://10.0.4.71:8000`
4. **Screenshot**: your site loaded on a device that is not the Pi, address bar visible
5. **Screenshot**: your project folder on the Pi, showing your files
6. **Reflection** (5 to 7 sentences). Answer all of these:
   - What did you build and who is it for?
   - What broke, and how did you work out why?
   - If you used AI after approval, what did you use it for?
   - What would you add with another week?

---

## 📸 Getting Your Work Into Schoology

Every deliverable on that list is sitting on a different machine right now. Here is how each one gets where it needs to go.

### Taking the screenshots

**On the Pi.** Press the **Print Screen** key. Depending on which version of Raspberry Pi OS your station runs, it either drops a `.png` into your home folder or opens a small capture window. If nothing happens at all, open **Menu → Accessories** and look for **Screenshot**.

**On your phone.** iPhone is **Side button + Volume Up**. Android is **Power + Volume Down**.

**On a lab computer.** Mac is **Cmd + Shift + 4**, then drag a box. Windows is **Windows + Shift + S**, then drag a box and paste it into any app to save.

> Full guide for every device: [How to Take and Submit Screenshots](../fundamentals/how_to_screenshot.md)

**Make sure the address bar is in the shot.** Your screenshot has to prove *where* the page was loaded from, not just that a page loaded. Crop it too tight to see `10.0.4.71:8000` and it proves nothing. Capture the whole browser window.

### Finding your files

Your site files are in your project folder on the Pi, and the server is one level up:

```
~/chess/index.html
~/chess/styles.css
~/chess/script.js
~/site_server.py
```

In the Pi's file manager that is **Home → your project folder**. If you cannot find them:

```bash
ls ~ ~/chess
```

### Getting all of it uploaded

**Your files and your Pi screenshot: submit from the Pi.** Everything is already on that machine, so this is the short path.

1. Open **Chromium** on the Pi
2. Go to Schoology and log in
3. Open the assignment, click **Submit Assignment**, click **Upload**
4. In the file picker, go to **Home → your project folder** and pick your files

**Your phone screenshot:** email it to yourself, AirDrop it, or put it in Google Drive and download it wherever you are submitting from. You can also log in to Schoology in your phone's browser and upload straight from the camera roll.

**If the Pi will not cooperate:** copy the folder to your jump drive, take it to a lab computer, submit from there.

**Name your files so they are readable:** `krigger-chess-index.html`, `krigger-chess-on-phone.png`. A folder of files called `Screenshot 2026-11-04 at 10.14.22.png` helps nobody, including you.

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Submit |
|---|---|
| 1 | Your site files: `index.html`, `styles.css`, `script.js` |
| 2 | `site_server.py` |
| 3 | Screenshot of your site on a device that is not the Pi |
| 4 | Screenshot of your project folder on the Pi |
| 5 | Your written reflection |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**. Do **NOT** click "Create" (Create is for text only and will not let you attach files)
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Working Site | 10 | It loads from the Pi on a device that is not the Pi. Images and links all work. Nothing runs off the screen at phone width |
| Design and Build | 5 | The structure and the design are yours, not the skeleton with the words changed. At least one working interactive thing. High school: a working API route |
| Understanding | 5 | The Day 4 walkthrough. You can explain any part of your own code on request, including anything AI touched |
| Deliverables | 5 | Files, both screenshots and the reflection, submitted on time |

**Bonus:**
- **+3 points** for a middle school student who completes the Stretch
- **+2 points** if somebody other than you actually used it for something: at a booth, in the lab, or as a real page a real person needed

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

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Static file** | A file the server hands over unchanged: an HTML page, a stylesheet, an image |
| **Port** | The door number on a computer. Your dashboard uses 5000, this site uses 8000 |
| **Route** | A line like `@app.route("/api/random")` saying which request a function answers |
| **Relative path** | A path starting from where the file is, like `assets/photo.jpg`. Works anywhere the folder goes |
| **Case sensitive** | Linux treats `Photo.jpg` and `photo.jpg` as different files. Mac and Windows do not |
| **CSS variable** | A named color or size defined once in `:root` and reused with `var(--name)` |
| **Event listener** | Code that waits for something to happen, like a click, and then runs |
| **Console** | The browser panel that shows you your JavaScript errors. **F12** |
| **Responsive** | A page that works at any screen width without a separate phone version |

---

## 💡 Troubleshooting

**"My CSS is not doing anything"**
→ Three things. Is `styles.css` in the same folder as `index.html`? Is the `<link>` line in the `<head>` spelled exactly right? Did the file save as `styles.css` and not `styles.css.txt`?

**"My browser shows the code as text instead of the page"**
→ The file is not really an `.html` file. Look at the tab name in VS Code. If it says `index.html.txt`, rename it in the sidebar.

**"My images worked on the laptop and not on the Pi"**
→ A capital letter. Check that the filename in your `src` matches the actual file exactly, letter for letter. Rename everything to lowercase and fix the `src` lines.

**"Address already in use"**
→ Something is already on that port. Your dashboard is probably on 5000. This site is on 8000. If 8000 is also taken, `pkill -f site_server.py` and start again.

**"My JavaScript does nothing"**
→ Press **F12** and read the Console. "null is not an object" means `getElementById` could not find that id, so the name in your HTML and the name in your JS do not match. Also check that `<script src="script.js"></script>` is the last thing before `</body>`.

**"The page loads but it is the old version"**
→ Hard refresh: **Ctrl + Shift + R**.

**"Nothing loads from my phone"**
→ Is the phone on GHCDS? Is the server still running on the Pi? Did you type `:8000` after the IP?

**"I cannot find my jump drive on the Pi"**
→ `ls /media/$USER/` lists what is plugged in. If it is empty, unplug the drive, plug it back in, and wait a few seconds.

**"I deleted something and now it is all broken"**
→ Your jump drive has yesterday's copy. Copy it back. This is exactly why you save to it at the end of every period.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] Every command checked against current Raspberry Pi OS behavior, 2026-09-16
- [x] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [x] No default pi/raspberry login assumed anywhere
- [x] Every path uses ~ or $USER , never /home/pi
- [x] Port 8000, so it does not collide with the dashboard on 5000
- [x] Every checkpoint is something a student can actually see
- [x] Base tier is readable by a 7th grader
- [ ] Site version stands alone: leave out the rubric, the point values and the
      Schoology upload steps per site rule 8
=========================================================================== -->
