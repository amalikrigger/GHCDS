<!-- ===========================================================================
TEACHER PLANNING BLOCK — delete nothing, this never renders on the site.

UNIT / FOLDER   : raspberry-pi
FILE NAME       : raspberry_pi_dashboard.md
PERIODS         : 3
FIRST TAUGHT    : T1 2026
REWRITTEN       : 2026-09-16, to the LESSON_TEMPLATE standard. Replaces the
                  4-day April 2026 version. See knowledge/decisions.md for the
                  full review of what was wrong with it.

THE LAB RUNS TWO OS VERSIONS
Bookworm on most stations, Trixie on some. Days 1 through 3 are deliberately
version-neutral: no GUI menu paths, no wpa_supplicant, whoami instead of an
assumed username, ~ instead of /home/pi. Every command in the body runs the
same on Bullseye, Bookworm and Trixie. Version only matters in the appendix,
which carries two separate walkthroughs, Bookworm first.

WHAT CHANGED FROM THE OLD VERSION, AND WHY
- SD card flashing moved to an appendix at the back rather than being cut. Day
  1 starts with code on an already-working Pi instead of a 15-minute apt
  upgrade, but the full from-blank-card build is still in the file for a new
  Pi, a wiped card, or another class. Students skip it unless told otherwise.
- The Wi-Fi configuration step is gone from the body. It edited
  /etc/wpa_supplicant/wpa_supplicant.conf, which Raspberry Pi OS stopped using
  in Bookworm, October 2023. The Pis already join GHCDS. The correct modern
  way to set Wi-Fi, the Imager OS customisation screen, is in the appendix.
- No default pi/raspberry login anywhere. Students run whoami. Every path uses
  ~ instead of /home/pi.
- The HTML lives in its own file from minute one instead of inside a Python
  triple-quoted string. That kills the old Day 3 "select 300 lines in Thonny
  and delete them" maneuver, and it is the same mental model the custom
  website assignment needs.
- Day 3's upgrade is delete-and-retype the HTML file. No selection surgery.
- Deliverables are files plus two screenshots plus a reflection, not eight
  screenshots.
- Base and Stretch added. The Stretch is a new stat wired end to end.

PREP THE DAY BEFORE
- [ ] Pis counted and powered at monitor stations: ____ of ____
- [ ] CONFIRM ON ONE PI, then fix this file if it differs:
        whoami                      -> username is: ____________
        cat /etc/os-release         -> OS is: ____________
        source ~/YOURNAME/venv/bin/activate ; python3 -c "import flask, psutil"
        (if that errors, the Step 2 fallback in Day 1 is the path students take)
- [ ] Accounts or logins students need: none
- [ ] Software already on lab machines: a terminal with ssh (Day 2 only)
- [ ] Posted in the room: the Pi IP sticky-note rule, and the Ctrl+C rule
- [ ] Decide whether anyone is doing the appendix (flashing from a blank card).
      If yes, that is its own period and it is mostly waiting.
- [ ] Test the whole build myself end to end: ____________

TIMING FOR DAY 1
- 5 min   Hook. Load the finished dashboard on the projector from my own Pi.
- 8 min   Together: whoami, hostname -I, activate the venv
- 12 min  Students build the 6-line hello server and load it. Everyone gets a
          win inside the first 20 minutes.
- 8 min   Mini lesson: request and response
- 20 min  Students build the real server.py and index.html, see live numbers
- 5 min   Screenshot, clean up

WHERE STUDENTS GET STUCK
- Forgot the venv -> "ModuleNotFoundError: flask". Say: look at your prompt.
  Does it start with (YOURNAME)?
- Second terminal, server already running -> "Address already in use". Say:
  find the other window, Ctrl+C.
- Typed the IP from someone else's sticky note -> loads a classmate's page.
  This is funny once and then it is a debugging lesson about IP addresses.
- Saved index.html into ~/YOURNAME/pi-dashboard instead of ~/YOURNAME/pi-dashboard/static ->
  404. Say: run ls static.
- Temperature shows -- on some models. Not a bug. Say so before they ask.

IF THEY FINISH EARLY   : Day 3 challenges 1 through 4, then the Stretch.
IF THEY NEED MORE TIME : Day 2 SSH is the cut. The dashboard still loads from a
                         phone without it, which is the part that matters.

ASSESSMENT
- Category  : Formal Assessments
- Points    : 25
- Schoology : due date ____________   Sections: both (MS 01YR and Comp Sci 01T1)
- Exit ticket quiz is a separate Schoology item: raspberry_pi_dashboard_quiz.md

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🖥️ Raspberry Pi Web Server

### Turn a computer the size of a deck of cards into a live website

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 3 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> Right now the Raspberry Pi in front of you is just a small computer. By the end of today it will be a **server**: it will have a web address, and anyone on the school network can type that address into their phone and see a page you built. By the end of the week that page will be showing the Pi's own CPU, memory, disk and temperature, updating live, and it will look good.

---

## 🎯 What You'll Learn

- What a **web server** actually is, and how to run one in six lines of code
- How a page asks a server for data using an **API**, and gets **JSON** back
- How to reach one computer from another using **SSH**
- How HTML, CSS and JavaScript split the work of a web page between them
- How to change something on the server and watch it appear in the browser

---

## 🧰 What You Need

- A Raspberry Pi at a monitor station, already set up and connected to GHCDS
- A phone, laptop or Chromebook on the same network, for Day 2
- A second computer in the lab with a terminal, for the SSH step on Day 2
- No accounts. No downloads. Nothing to sign up for.

---

## ⚠️ Before You Touch the Pi

1. **Power comes out last.** Shut the Pi down from the menu before unplugging it. Yanking the power while it is writing to the SD card is the one reliable way to destroy your work.
2. **The SD card stays in.** It is the Pi's whole hard drive. Do not pop it out to see what happens.
3. **Nothing goes on the SD card slot, the pins, or the ports except what belongs there.** The exposed pins along the edge are live.
4. **Never type a password into a file.** Not your Pi password, not the Wi-Fi password, not anything. You will be asked for a password in the terminal on Day 2. That is the only place it goes.
5. **If something goes wrong**, stop and tell Mr. Krigger. A Pi that will not boot is a ten-second fix if you say so and a lost week if you do not.

---

# Day 1: Make Your Pi a Server

**Goal:** At the start of today your Pi is a computer. At the end of today it is a website.

---

### Step 1 — Find out who you are and where you are

Open the **Terminal** on the Pi. It is the black rectangle icon on the top bar.

> **🤔 What is a Terminal?** It is a way to talk to the computer by typing instead of clicking. Same computer, same files, different door. Think of it as texting your Pi instead of tapping icons.

Type this and press Enter:

```bash
whoami
```

That prints your username on this Pi. Write it down. You will need it on Day 2.

Now type:

```bash
hostname -I
```

That prints your Pi's **IP address**, something like `10.0.4.71`. **Write it on a sticky note and put it on your monitor.** Everything on Day 2 depends on it.

> **What is an IP address?** Your network is a neighborhood and every device on it gets a house number. That is the IP address. When someone types it into a browser they are saying "take me to that house."

> **✅ Checkpoint:** You have two things written down: your username and your Pi's IP address.

---

### Before Step 2 — Claim your own folder

Everyone in both classes shares these Pis, logged in as the same account. If two people build a folder with the same name, the second person lands inside the first person's project, sees work they did not do, and overwrites it. So before you build anything, pick a name that is only yours.

**Your folder name** is your first name plus the first letter of your last name, all lowercase, no spaces. Jordan Baptiste is `jordanb`. If two of you would get the same name, one of you adds a number: `jordanb2`. Everywhere this lesson says `YOURNAME`, type your folder name. (On the site version, a box rewrites every command for you.)

> **✅ Checkpoint:** your folder name is on your sticky note, under your IP address.

**Sharing a Pi.** Run `ls ~` to see the folders already there. Four rules:

1. Only work inside your own folder. Every command in this lesson starts with `~/YOURNAME`.
2. Never open, edit or delete a folder that is not yours.
3. Your name already there and it is not your work? Add a number and use that.
4. Before you leave, stop your server with **Ctrl + C**. Only one server can use port 5000 at a time.

---

### Step 2 — Set up your Python workspace

This project needs two Python add-ons that are not installed by default. They live in a little workspace of their own called `venv`, inside your folder.

**First, check whether you already built it last time:**

```bash
ls ~/YOURNAME/venv
```

You will get one of two answers.

| What you see | What it means | What to do |
|---|---|---|
| A short list: `bin`, `include`, `lib`, `pyvenv.cfg` | The workspace is already built | Skip ahead to **Open it** |
| `No such file or directory` | It is not built yet | Do **Build it** first |

**Build it.** Two commands, one at a time. Wait for the first to finish before running the second.

```bash
mkdir -p ~/YOURNAME && python3 -m venv --prompt YOURNAME ~/YOURNAME/venv
```

```bash
~/YOURNAME/venv/bin/pip install flask psutil
```

The second one downloads for a minute and prints a lot of text. That is normal. Wait for your prompt to come back.

**Open it.** Everyone runs this, whether you just built the workspace or you built it last time:

```bash
source ~/YOURNAME/venv/bin/activate
```

> **✅ Checkpoint:** Your prompt now starts with `(YOURNAME)`, your own name. It looked like `krigger@raspberrypi:~ $` before and it looks like `(jordanb) krigger@raspberrypi:~ $` now. Someone else's name there means you opened their box: type `deactivate` and run your own `source` line.

> **What did you just build?** A **virtual environment**: a box that holds one project's extra Python tools and nothing else. Two tools went in the box. **Flask** lets Python run a website. **psutil** lets Python read the computer's own CPU, memory and temperature.
>
> Think of it like a toolbox for one job. The rest of the Pi is not affected, and if you ever wreck it you delete the folder and build a new one in thirty seconds.

> **⚠️ The thing that catches everyone.** Opening the box only lasts for that one Terminal window. Close it, open a new one, and you are back outside the box. The giveaway is `(YOURNAME)` missing from your prompt, and the symptom is `ModuleNotFoundError: No module named 'flask'`. The fix is always the same: run the `source` line again.

---

### Step 3 — Make your project folder

```bash
mkdir -p ~/YOURNAME/pi-dashboard/static && cd ~/YOURNAME/pi-dashboard
```

You just made this:

```
YOURNAME/               ← your folder, nobody else's
├── venv/               ← your Python toolbox (Step 2)
└── pi-dashboard/       ← this project
    ├── server.py       ← the Python that runs the server (next step)
    └── static/         ← the files your server hands out
        └── index.html  ← your actual web page (Step 7)
```

The `~` means the home folder of the account you are logged in as. Everyone on this Pi shares that account, which is why your work lives one level down, in `~/YOURNAME`.

---

### Step 4 — Write the smallest web server that works

```bash
nano server.py
```

> **🤔 What is `nano`?** A text editor that lives inside the Terminal. Like Notepad with no window.

Type or paste exactly this:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "<h1>My Pi is a web server.</h1>"

app.run(host="0.0.0.0", port=5000)
```

Save with **Ctrl + O**, then Enter. Exit with **Ctrl + X**.

> **Pasting into the Terminal is Ctrl + Shift + V**, not Ctrl + V. This trips up everyone once.

---

### Step 5 — Run it

```bash
python3 server.py
```

The Terminal will print a few lines and then sit there looking frozen. It has not crashed, it is listening.

Open **Chromium** on the Pi and go to:

```
http://localhost:5000
```

> **✅ Checkpoint:** The browser says **My Pi is a web server.** That is a real server, running on a real computer, serving a real page. It took six lines.

**To stop it:** click the Terminal window and press **Ctrl + C**. Remember this. You will need it constantly.

> **⚠️ You will also see a yellow warning** about a "development server" and not using it in production. Ignore it. It means "this server is built for learning, not for handling a million people at once," which is what you are doing.

---

### 🧠 Mini Lesson — What a server actually does

A server does one thing, over and over, forever:

1. It waits.
2. Something asks it for a thing. This is a **request**.
3. It sends that thing back. This is a **response**.
4. Go to 1.

Nothing else. When you typed `http://localhost:5000` into Chromium, the browser sent a request to your Pi. Your six lines of Python caught it, and the line `return "<h1>My Pi is a web server.</h1>"` was the response.

Netflix does the same thing. So does Instagram, so does your school's grade portal. They have more lines of code and more computers, but the loop is identical: wait, request, response, repeat.

The `@app.route("/")` line is the part that decides **which** request. `/` means the front page. On Day 1 you will add a second route, and the server will start answering two different questions.

---

### Step 6 — Build the real thing

Stop your server with **Ctrl + C**, then reopen the file:

```bash
nano server.py
```

Delete everything in it (hold **Ctrl + K** to cut lines until the file is empty), then type or paste this:

```python
from flask import Flask, jsonify, send_from_directory
import psutil
import subprocess
import os

STATIC = os.path.join(os.path.dirname(os.path.abspath(__file__)), "static")

app = Flask(__name__)


@app.route("/")
def home():
    return send_from_directory(STATIC, "index.html")


@app.route("/<path:filename>")
def other_files(filename):
    return send_from_directory(STATIC, filename)


def temperature_c():
    try:
        for group in psutil.sensors_temperatures().values():
            for reading in group:
                if getattr(reading, "current", None) is not None:
                    return round(float(reading.current), 1)
    except Exception:
        pass
    try:
        output = subprocess.check_output(["vcgencmd", "measure_temp"], text=True)
        return round(float(output.split("=")[1].split("'")[0]), 1)
    except Exception:
        return None


@app.route("/api/stats")
def stats():
    return jsonify({
        "cpu": psutil.cpu_percent(interval=0.2),
        "memory": psutil.virtual_memory().percent,
        "disk": psutil.disk_usage("/").percent,
        "temperature": temperature_c()
    })


app.run(host="0.0.0.0", port=5000)
```

Save: **Ctrl + O**, Enter. Exit: **Ctrl + X**.

> **What just happened?** Your server now answers three different requests:
> - `/` hands over the file `static/index.html`
> - `/api/stats` hands over four numbers, freshly measured, as text
> - anything else gets looked up in your `static` folder, which is how images and CSS files will work later

---

### Step 7 — Write the page

```bash
nano static/index.html
```

Type or paste:

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Pi Health</title>
</head>
<body>

  <h1>Raspberry Pi Health</h1>
  <p>CPU: <span id="cpu">--</span>%</p>
  <p>Memory: <span id="memory">--</span>%</p>
  <p>Disk: <span id="disk">--</span>%</p>
  <p>Temperature: <span id="temperature">--</span> C</p>

  <script>
    async function refresh() {
      const response = await fetch("/api/stats");
      const data = await response.json();
      for (const name of ["cpu", "memory", "disk", "temperature"]) {
        document.getElementById(name).textContent =
          data[name] === null ? "--" : Math.round(data[name]);
      }
    }

    refresh();
    setInterval(refresh, 2000);
  </script>

</body>
</html>
```

Save and exit. Then run it:

```bash
python3 server.py
```

Reload `http://localhost:5000` in Chromium.

> **✅ Checkpoint:** Four numbers, and they change on their own every two seconds. Open a few browser tabs and watch CPU climb. That is your Pi reporting on itself.

> **Temperature showing `--`?** Some Pi models do not report it. Everything else still works. Not your fault, not a bug.

---

### 🧠 Mini Lesson — The other way to do this (optional)

Your page lives in its own file, `static/index.html`, and your Python hands that file over when somebody asks for it.

There is a second way, and it is worth seeing once. **HTML is just text.** Python is very good at holding text. So you can put the entire page inside the Python file, as one long string, and skip having a separate file at all.

It looks like this. Three quote marks open a string that is allowed to run across many lines:

```python
from flask import Flask, render_template_string

app = Flask(__name__)

PAGE = """
<!doctype html>
<html>
  <head><title>Pi Health</title></head>
  <body>
    <h1>My page lives inside the Python file.</h1>
  </body>
</html>
"""


@app.route("/")
def home():
    return render_template_string(PAGE)


app.run(host="0.0.0.0", port=5000)
```

`render_template_string` means "here is a page, as text, send it." Compare that to your `send_from_directory`, which means "here is a filename, go find it and send it."

**Neither one is wrong. They are good at different things.**

| | One file, HTML in the string | Two files, HTML on its own |
|---|---|---|
| Number of files to keep track of | 1 | 2 |
| Editing 200 lines of HTML | Painful. You are scrolling past Python to get to it | Normal |
| Adding a stylesheet, a photo, a second page | Awkward | It already works |
| Your editor coloring the HTML correctly | No. It thinks the whole thing is one string | Yes |
| Handing the project to somebody else | Fine for something small | Fine at any size |

We used two files because your next project is a whole website with images and a stylesheet, and that is the shape it needs. A one-file server is a real and reasonable thing to build when the page is four lines long.

> **Try it if you want.** Copy your `server.py` to `server_onefile.py` first, so you still have the working one, then experiment. Nothing later in this project depends on this.

---

### 📝 Day 1 Deliverables

- [ ] Screenshot of your dashboard in Chromium on the Pi, with live numbers in it
- [ ] Your username and your Pi's IP address, written down where you will still have them on Day 2

---

# Day 2: Reach It From Anywhere on the Network

**Goal:** Prove it is a real server by using it from a computer that is not the Pi.

---

### Step 1 — Load your dashboard on your phone

Your server has to be running. If you stopped it:

```bash
source ~/YOURNAME/venv/bin/activate
cd ~/YOURNAME/pi-dashboard
python3 server.py
```

Now take out your phone, make sure it is on the GHCDS network, and type your Pi's IP address and port into the browser:

```
http://YOUR-PI-IP:5000
```

So if your sticky note says `10.0.4.71`, you type `http://10.0.4.71:5000`.

> **✅ Checkpoint:** Your Pi's dashboard, on your phone, updating live. Nothing is on the internet. Your phone asked your Pi directly, across the room.

> **Loading someone else's numbers?** You typed their IP. It happens. Check your sticky note.

---

### 🧠 Mini Lesson — Why `0.0.0.0` was the important part

Look at the last line of `server.py`:

```python
app.run(host="0.0.0.0", port=5000)
```

`0.0.0.0` means **"answer requests from anywhere on the network, not just from me."** If it said `127.0.0.1` instead, the page would work in Chromium on the Pi and your phone would get nothing.

That is also the difference between the two addresses you have now used:

| Address | What it means | Works from |
|---|---|---|
| `http://localhost:5000` | this computer, port 5000 | only the Pi itself |
| `http://10.0.4.71:5000` | the device at that house number, port 5000 | any device on GHCDS |

**Port 5000** is the door number. One computer can run many servers at once as long as each uses a different door.

---

### Step 2 — Look at the raw data

On your phone or in Chromium, go to:

```
http://YOUR-PI-IP:5000/api/stats
```

You will see something like this, and nothing else:

```json
{"cpu":12.5,"disk":31.2,"memory":24.8,"temperature":47.1}
```

Refresh it. The numbers change.

> **✅ Checkpoint:** You are looking at raw JSON. Screenshot this, you need it for your submission.

---

### 🧠 Mini Lesson — API and JSON

An **API** is a door on a server that hands back data instead of a web page.

Think about ordering food. You do not walk into the kitchen. You tell a waiter what you want, the waiter goes to the kitchen, and the waiter brings back a plate. You never see how the kitchen works and you do not need to.

`/api/stats` is the waiter. Your web page is you. The Python function `stats()` is the kitchen.

**JSON** is what is on the plate. It is just text, arranged so a program can read it:

```json
{"cpu": 12.5, "memory": 24.8}
```

A name, a colon, a value, commas between them, curly braces around the whole thing. The whole format, start to finish. Almost every app on your phone is passing JSON back and forth all day.

Now look at your page again. These three lines are the whole conversation:

```javascript
const response = await fetch("/api/stats");   // ask the waiter
const data = await response.json();           // take the plate
setInterval(refresh, 2000);                   // do it again in 2 seconds
```

---

### Step 3 — Connect to your Pi from a different computer

**SSH** lets you type commands on your Pi while sitting at a different machine. No monitor, no keyboard on the Pi at all.

Go to one of the lab computers. Open its terminal. Type this, using **your** username and **your** Pi's IP:

```bash
ssh YOUR-USERNAME@YOUR-PI-IP
```

For example:

```bash
ssh krigger@10.0.4.71
```

The first time, it will ask something like `Are you sure you want to continue connecting?` Type **yes** and press Enter. Then it asks for your Pi password. **Type it. Nothing will appear on screen while you type. That is on purpose.** Press Enter.

> **✅ Checkpoint:** Your prompt changed. It now shows your Pi's name, not the lab computer's. Every command you type from here runs on the Pi.

---

### Step 4 — Prove it

Still in the SSH window, run:

```bash
hostname
```

```bash
uptime
```

The first prints your Pi's name. The second prints how long it has been switched on. Neither of those is the computer you are sitting at.

To leave:

```bash
exit
```

---

### Step 5 — Start your server without touching the Pi

SSH back in, then:

```bash
source ~/YOURNAME/venv/bin/activate
cd ~/YOURNAME/pi-dashboard
python3 server.py
```

Then open a browser on the lab computer and go to `http://YOUR-PI-IP:5000`.

You just started a server on a computer across the room and loaded its page. Plenty of people do exactly this for a living.

> **Heads up:** when you close the SSH window, the server stops with it. That is normal. There are ways around it, and that is a good thing to ask about if you are curious.

---

### 🧠 Mini Lesson — SSH

**SSH** stands for **Secure Shell**. Two halves:

- **Shell** is the thing that reads your typed commands. The Terminal is a shell.
- **Secure** means everything you type is scrambled on the way over, so anyone watching the network sees noise.

That second half is the whole reason it exists. Before SSH, people used a tool called Telnet that sent passwords across the network in plain readable text. If you were on the same network, you could just read them.

This is how IT staff fix servers they will never physically see, how your school's tech department reaches every machine in the building from one desk, and how anyone who runs a game server does anything at all.

---

### 📝 Day 2 Deliverables

- [ ] Screenshot of your dashboard loaded on a **different device**, with the address bar showing your Pi's IP
- [ ] Screenshot of `/api/stats` showing the raw JSON

---

# Day 3: Make It Yours

**Goal:** Take the plain page and turn it into something you would actually show someone.

---

> **Nothing about the Python changes today.** The server already works. You are only replacing the page it hands out. Real web work usually goes this way, with the thing underneath staying put while the thing people see gets redesigned.

### Step 1 — Start the page over

Stop your server with **Ctrl + C**. Then:

```bash
rm ~/YOURNAME/pi-dashboard/static/index.html
```

```bash
nano ~/YOURNAME/pi-dashboard/static/index.html
```

You now have an empty file. Nothing to select, nothing to accidentally delete half of.

---

### Step 2 — Paste the new page

```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Pi Health</title>
<style>
  /* =====================================================================
     THEME BLOCK. Everything you need to restyle this whole page lives
     between these two lines. Change a value, save, restart, refresh.
     ===================================================================== */
  :root {
    --bg-top:    #0f2027;
    --bg-bottom: #2c5364;
    --text:      #ffffff;
    --muted:     rgba(255, 255, 255, 0.70);
    --card:      rgba(255, 255, 255, 0.12);
    --card-edge: rgba(255, 255, 255, 0.18);
    --track:     rgba(255, 255, 255, 0.15);
    --ok:        #4ade80;
    --warn:      #facc15;
    --hot:       #f87171;
    --round:     16px;
    --font:      system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  }
  /* ================================================================== */

  * { box-sizing: border-box; }

  body {
    margin: 0;
    min-height: 100vh;
    padding: 32px 20px;
    color: var(--text);
    font-family: var(--font);
    background: linear-gradient(135deg, var(--bg-top), var(--bg-bottom));
  }

  h1 { margin: 0 0 4px; font-size: 28px; }
  .sub { margin: 0 0 28px; color: var(--muted); font-size: 14px; }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 18px;
    max-width: 960px;
  }

  .card {
    padding: 20px;
    border-radius: var(--round);
    border: 1px solid var(--card-edge);
    background: var(--card);
    backdrop-filter: blur(10px);
    transition: transform 0.15s ease;
  }
  .card:hover { transform: translateY(-4px); }

  .card h2 { margin: 0 0 12px; font-size: 15px; font-weight: 600; color: var(--muted); }

  .value { font-size: 42px; font-weight: 700; line-height: 1; }
  .unit  { font-size: 16px; font-weight: 400; color: var(--muted); margin-left: 2px; }

  .bar {
    margin-top: 14px;
    height: 8px;
    border-radius: 999px;
    background: var(--track);
    overflow: hidden;
  }
  .fill {
    width: 0%;
    height: 100%;
    border-radius: 999px;
    background: var(--ok);
    transition: width 0.4s ease, background 0.4s ease;
  }

  .warn .fill  { background: var(--warn); }
  .warn .value { color: var(--warn); }
  .hot  .fill  { background: var(--hot); }
  .hot  .value { color: var(--hot); }
</style>
</head>
<body>

<h1>🖥️ Raspberry Pi Health</h1>
<p class="sub">Live from my Pi. Updates every 2 seconds.</p>

<div class="grid">

  <div class="card" id="card-cpu">
    <h2>⚡ CPU Usage</h2>
    <div><span class="value" id="cpu">--</span><span class="unit">%</span></div>
    <div class="bar"><div class="fill" id="bar-cpu"></div></div>
  </div>

  <div class="card" id="card-memory">
    <h2>🧠 Memory Used</h2>
    <div><span class="value" id="memory">--</span><span class="unit">%</span></div>
    <div class="bar"><div class="fill" id="bar-memory"></div></div>
  </div>

  <div class="card" id="card-disk">
    <h2>💽 Disk Used</h2>
    <div><span class="value" id="disk">--</span><span class="unit">%</span></div>
    <div class="bar"><div class="fill" id="bar-disk"></div></div>
  </div>

  <div class="card" id="card-temperature">
    <h2>🔥 Temperature</h2>
    <div><span class="value" id="temperature">--</span><span class="unit">&deg;C</span></div>
    <div class="bar"><div class="fill" id="bar-temperature"></div></div>
  </div>

</div>

<script>
  const CARDS = [
    { key: "cpu",         max: 100, warn: 50, hot: 80 },
    { key: "memory",      max: 100, warn: 60, hot: 85 },
    { key: "disk",        max: 100, warn: 70, hot: 90 },
    { key: "temperature", max: 90,  warn: 60, hot: 75 }
  ];

  async function refresh() {
    const response = await fetch("/api/stats");
    const data = await response.json();

    for (const card of CARDS) {
      const reading = data[card.key];
      const box = document.getElementById("card-" + card.key);
      const value = document.getElementById(card.key);
      const fill = document.getElementById("bar-" + card.key);

      if (reading === null || reading === undefined) {
        value.textContent = "--";
        fill.style.width = "0%";
        continue;
      }

      value.textContent = Math.round(reading);
      fill.style.width = Math.min(100, (reading / card.max) * 100) + "%";

      box.classList.remove("warn", "hot");
      if (reading >= card.hot) {
        box.classList.add("hot");
      } else if (reading >= card.warn) {
        box.classList.add("warn");
      }
    }
  }

  refresh();
  setInterval(refresh, 2000);
</script>

</body>
</html>
```

Save: **Ctrl + O**, Enter. Exit: **Ctrl + X**. Then run it:

```bash
source ~/YOURNAME/venv/bin/activate
cd ~/YOURNAME/pi-dashboard
python3 server.py
```

> **✅ Checkpoint:** A dark blue gradient, four frosted cards, big numbers, and a bar under each one that fills up and turns yellow then red as the number climbs. Hover a card and it lifts.

> **Same page as before?** Hard refresh with **Ctrl + Shift + R**. Browsers keep old copies.

---

### 🧠 Mini Lesson — The three new things you just used

**Gradient.** Instead of one flat color, a smooth blend between two:

```css
background: linear-gradient(135deg, #0f2027, #2c5364);
```

`135deg` is the angle. The two `#` codes are **hex colors**, six characters that mix red, green and blue.

**Grid.** Four cards that rearrange themselves depending on screen width:

```css
grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
```

This says "make as many columns as fit, each at least 220px wide." Drag your browser window narrower and watch four columns become two and then one. Nobody wrote a rule for phones. That one line did it. This is called **responsive design**.

**Classes as switches.** The color change is not JavaScript drawing anything. The CSS already knows what `.hot` looks like. JavaScript just adds and removes the label:

```javascript
box.classList.add("hot");
```

That split matters. CSS handles how things look, JavaScript handles when, and keeping the two apart is what lets a big site stay workable once there are thousands of lines of it.

---

### Step 3 — Make it yours

Here is the loop you will repeat for the rest of the period:

1. **Ctrl + C** in the Terminal to stop the server
2. `nano ~/YOURNAME/pi-dashboard/static/index.html`
3. Change something, **Ctrl + O**, Enter, **Ctrl + X**
4. `python3 ~/YOURNAME/pi-dashboard/server.py`
5. **Ctrl + Shift + R** in the browser

You cannot break anything here that retyping will not fix. Change one thing at a time so you know what did what.

---

### Level 1 — The theme block

Look at the top of your CSS. Everything between the two long comment lines is the theme. Change a value there and it changes everywhere on the page at once, because every rule below reads from it instead of having its own copy of the color.

| Variable | What it controls |
|---|---|
| `--bg-top` and `--bg-bottom` | The two colors the background fades between |
| `--text` | Every piece of normal text |
| `--muted` | Labels and units. Dimmer than `--text` on purpose |
| `--card` | The card's own fill. `rgba` because it is see-through |
| `--card-edge` | The thin line around each card |
| `--track` | The empty part of each bar |
| `--ok`, `--warn`, `--hot` | Green, yellow and red |
| `--round` | How rounded the corners are. `0px` is sharp, `28px` is a pill |
| `--font` | The typeface for the whole page |

Try this first, so you can see how far one variable reaches:

```css
--round: 0px;
```

Save, restart, refresh. Every card went square. You changed one number.

---

### Level 2 — Theme packs

Each of these replaces your whole `:root` block. Copy one in, restart, look at it. Then take the one you like best and start changing its numbers.

**Terminal.** Sharp corners, monospace, the look of a machine that does not care about your feelings.

```css
  :root {
    --bg-top:    #000000;
    --bg-bottom: #0a1a0a;
    --text:      #d1fae5;
    --muted:     rgba(209, 250, 229, 0.55);
    --card:      rgba(34, 197, 94, 0.07);
    --card-edge: rgba(34, 197, 94, 0.30);
    --track:     rgba(34, 197, 94, 0.15);
    --ok:        #22c55e;
    --warn:      #eab308;
    --hot:       #ef4444;
    --round:     4px;
    --font:      "Courier New", monospace;
  }
```

**Midnight.** Purple, soft, easy on the eyes in a dark room.

```css
  :root {
    --bg-top:    #16162e;
    --bg-bottom: #4a1f6b;
    --text:      #f3e8ff;
    --muted:     rgba(243, 232, 255, 0.65);
    --card:      rgba(255, 255, 255, 0.10);
    --card-edge: rgba(216, 180, 254, 0.28);
    --track:     rgba(255, 255, 255, 0.14);
    --ok:        #86efac;
    --warn:      #fde047;
    --hot:       #fb7185;
    --round:     20px;
    --font:      system-ui, sans-serif;
  }
```

**Volcano.** For a Pi that runs hot and wants you to know it.

```css
  :root {
    --bg-top:    #1c0a08;
    --bg-bottom: #57180f;
    --text:      #fff7ed;
    --muted:     rgba(255, 247, 237, 0.62);
    --card:      rgba(255, 255, 255, 0.09);
    --card-edge: rgba(255, 170, 120, 0.25);
    --track:     rgba(255, 255, 255, 0.13);
    --ok:        #7ee787;
    --warn:      #fbbf24;
    --hot:       #ff5c4d;
    --round:     14px;
    --font:      system-ui, sans-serif;
  }
```

**Sea Glass.** Teal and calm. This one looks the most like something a company would ship.

```css
  :root {
    --bg-top:    #042f2e;
    --bg-bottom: #115e59;
    --text:      #ecfeff;
    --muted:     rgba(236, 254, 255, 0.66);
    --card:      rgba(255, 255, 255, 0.11);
    --card-edge: rgba(153, 246, 228, 0.26);
    --track:     rgba(255, 255, 255, 0.14);
    --ok:        #5eead4;
    --warn:      #fcd34d;
    --hot:       #fb7185;
    --round:     18px;
    --font:      system-ui, sans-serif;
  }
```

**Slate.** Grey, quiet, professional. The boring one, and boring is sometimes correct.

```css
  :root {
    --bg-top:    #1e293b;
    --bg-bottom: #334155;
    --text:      #f1f5f9;
    --muted:     rgba(241, 245, 249, 0.60);
    --card:      rgba(255, 255, 255, 0.07);
    --card-edge: rgba(255, 255, 255, 0.14);
    --track:     rgba(255, 255, 255, 0.12);
    --ok:        #4ade80;
    --warn:      #facc15;
    --hot:       #f87171;
    --round:     10px;
    --font:      system-ui, sans-serif;
  }
```

**Paper.** A light theme. Look closely at this one: the text went dark, the cards went white, and the transparent values all flipped. Nothing outside the theme block changed.

```css
  :root {
    --bg-top:    #f8fafc;
    --bg-bottom: #dbe3ec;
    --text:      #0f172a;
    --muted:     rgba(15, 23, 42, 0.60);
    --card:      rgba(255, 255, 255, 0.75);
    --card-edge: rgba(15, 23, 42, 0.12);
    --track:     rgba(15, 23, 42, 0.10);
    --ok:        #16a34a;
    --warn:      #ca8a04;
    --hot:       #dc2626;
    --round:     14px;
    --font:      system-ui, sans-serif;
  }
```

> **🎨 Why nearly every one of these is dark.** Your page has to show green, yellow and red and have all three read clearly. Those three colors have nowhere to go on a bright orange or hot pink background, they just turn to mud. Real dashboards, the ones air traffic controllers and network engineers stare at all day, are almost always dark for this reason. If you build a bright theme anyway, check that a red card still shouts at you from across the room. If it does not, the theme is pretty and useless.

Build your own palette at [coolors.co](https://coolors.co/). Pick two close colors for the background and keep your green, yellow and red bright.

---

### Level 3 — Real upgrades

These add something that is not there yet. Do as many as you want, in any order.

#### 1. A real typeface

Free fonts from [Google Fonts](https://fonts.google.com/). Pick one, then add **one line** in your `<head>`, above `<style>`:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;700&display=swap">
```

And point the theme at it:

```css
--font: "Space Grotesk", system-ui, sans-serif;
```

Swap `Space+Grotesk` for any font name from the site, with `+` instead of spaces. Good ones for a dashboard: `Space+Grotesk`, `JetBrains+Mono`, `Outfit`, `Chivo+Mono`, `Archivo`.

> Keep `system-ui, sans-serif` on the end. It is the backup, covering the two seconds before the font arrives, or forever if the Wi-Fi is down.

---

#### 2. A background that moves

Add this at the bottom of your CSS, above `</style>`:

```css
@keyframes drift {
  0%   { background-position: 0% 50%; }
  50%  { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

body {
  background: linear-gradient(135deg, var(--bg-top), var(--bg-bottom), var(--bg-top));
  background-size: 400% 400%;
  animation: drift 18s ease infinite;
}
```

The gradient is stretched to four times the screen and then slid slowly back and forth. Change `18s` to `4s` to see it clearly, then put it back to something calm. A background that races is a background nobody can read in front of.

---

#### 3. Make the numbers glow

```css
.value {
  text-shadow: 0 0 18px currentColor;
}
```

`currentColor` means "whatever color this text already is." So the green numbers glow green, and the moment a card goes red the glow goes red too. One line, and it follows your thresholds for free.

---

#### 4. Make a hot card pulse

```css
@keyframes alarm {
  0%, 100% { box-shadow: 0 0 0 0 rgba(248, 113, 113, 0.55); }
  50%      { box-shadow: 0 0 0 14px rgba(248, 113, 113, 0); }
}

.card.hot {
  animation: alarm 1.4s ease-out infinite;
}
```

A ring pushes outward from the card and fades. It only runs on cards your JavaScript has marked `hot`, so most of the time you will never see it. Good alarms are quiet. Open six browser tabs to drive the CPU up and watch it fire.

---

#### 5. A clock in the corner

In your HTML, right under the `<h1>`:

```html
<p class="sub">Live from my Pi &middot; <span id="clock">--:--:--</span></p>
```

And at the bottom of your `<script>`, just above `</script>`:

```javascript
function tick() {
  document.getElementById("clock").textContent =
    new Date().toLocaleTimeString();
}
tick();
setInterval(tick, 1000);
```

Notice this clock is the **browser's** time, not the Pi's. It never asks the server anything. If you want the Pi's own time, that is a new key in `/api/stats`, which is the Stretch.

---

#### 6. Show when the data last arrived

Add a line under the grid in your HTML:

```html
<p class="sub" id="stamp">Waiting for the first reading.</p>
```

Then add one line inside `refresh()`, at the very end of the function, after the `for` loop closes:

```javascript
document.getElementById("stamp").textContent =
  "Last updated " + new Date().toLocaleTimeString();
```

Now you can tell the difference between "everything is fine" and "the server died three minutes ago and these numbers are stale." Every monitoring tool worth using has this, and it is one line.

---

#### 7. One big card and three small ones

Replace the `.grid` rule:

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 18px;
  max-width: 960px;
}

#card-cpu {
  grid-column: span 2;
}

#card-cpu .value {
  font-size: 72px;
}
```

CPU now takes two columns and a much bigger number, so the page has a main character instead of four things shouting equally. Put the big card on whichever stat you actually care about.

---

#### 8. A photo behind everything

Put an image in your `static` folder, then:

```css
body {
  background-image:
    linear-gradient(135deg, rgba(15, 32, 39, 0.85), rgba(44, 83, 100, 0.85)),
    url("/pi-background.jpg");
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
}
```

Two backgrounds stacked: your gradient on top, at 85% opacity, and the photo under it. Without that gradient layer the photo eats your text. Free photos at [unsplash.com](https://unsplash.com/).

> Remember the filename rule from the server: `/pi-background.jpg` has to match the real file exactly, lowercase and all. Your server hands out anything in `static`, so the path starts with a single `/`.

---

#### 9. Your own warning levels

In the `CARDS` list at the top of your JavaScript:

```javascript
{ key: "cpu", max: 100, warn: 50, hot: 80 },
```

Set `warn` to `5` and restart. The card sits in yellow permanently, forever, no matter what the Pi is doing.

An alarm that is always on is worse than no alarm, because people stop looking at it. Real engineers argue about these two numbers for hours. Pick yours on purpose and be ready to say why in your reflection.

---

#### 10. Everything else

- Swap the emoji in the `<h2>` lines. `⚡` `🧠` `💽` `🔥` `❄️` `🏎️` `📊` `🛰️`
- Put your name, or your Pi's name, in the `.sub` line
- Change `gap: 18px` to `gap: 4px` and then `gap: 40px`
- Change `translateY(-4px)` in `.card:hover` to `scale(1.04)` and hover a card
- Add `rotate(-1deg)` to `.card:hover` and decide whether you like chaos
- Delete a card you do not care about. Delete its line from `CARDS` too, or the JavaScript will look for something that is not there

---

> **Before you screenshot it.** Step back from the monitor. Can you tell in one second which number is the worst one? If every card looks equally loud, that is a design problem, not a color problem. Make one thing bigger, or make the calm cards quieter.

---

### 📝 Day 3 Deliverables

- [ ] Screenshot of your customized dashboard
- [ ] Your `server.py` and your `static/index.html` files

---

## 🎚️ Base and Stretch

**Base — everyone does this.**

A working server on your Pi, serving your own dashboard, loading on a device that is not the Pi, with at least **two visible changes that are yours**. You can explain what `/api/stats` sends back and who asks for it.

**Stretch — required for high school, bonus for middle school.**

**Add a fifth stat, wired all the way through.** Not a new color. A new number that does not exist yet, traveling from the Pi's hardware to the screen.

It takes three edits, one in each layer:

**1. Python.** In `server.py`, add a line inside the `jsonify({...})` block. Uptime, in minutes, looks like this:

```python
"uptime": round((time.time() - psutil.boot_time()) / 60)
```

You will need `import time` at the top with the other imports. Restart the server and check `http://YOUR-PI-IP:5000/api/stats`. **If your new name is not in that JSON, stop here and fix it before touching the HTML.**

**2. HTML.** Copy one of the four `<div class="card">` blocks, paste it at the end of the grid, and change all three ids to your new name.

**3. JavaScript.** Add one line to the `CARDS` list with a sensible `max`, `warn` and `hot`.

**Uptime is the worked example, so it is worth fewer points than one you find yourself.** Open the [psutil documentation](https://psutil.readthedocs.io/) and pick something else: how many processes are running, how many bytes have crossed the network, how many CPU cores are working. If you can get it out of psutil, you can put it on your page.

---

## 📝 Deliverables

1. **Your two files**: `server.py` and `static/index.html`
2. **Screenshot: your dashboard on a different device**, address bar showing your Pi's IP
3. **Screenshot: `/api/stats`** showing the raw JSON
4. **Reflection** (4 to 6 sentences). Answer all three:
   - What does `/api/stats` send back, and what asks for it?
   - How often does the page ask, and which line of code decides that?
   - What did you change, and what was the hardest part?
5. **High school, and middle school going for bonus:** name the stat you added and say which two files you had to edit to make it appear.

---

## 📸 How to Get Everything You Need to Hand In

Nothing on this list is hard, but every one of them has caught somebody. Read it before the last five minutes of class.

### Taking the screenshot

**On the Pi.** Press the **Print Screen** key. Depending on which version of Raspberry Pi OS your station is running, it either drops a `.png` straight into your home folder or opens a small capture window. If pressing it does nothing at all, open **Menu → Accessories** and look for **Screenshot**.

**On your phone.** iPhone is **Side button + Volume Up**. Android is **Power + Volume Down**.

**On a lab computer.** Mac is **Cmd + Shift + 4**, then drag a box. Windows is **Windows + Shift + S**, then drag a box, then paste it into any app and save it.

> Full guide, with more options for every device: [How to Take and Submit Screenshots](../fundamentals/how_to_screenshot.md)

**Make sure the address bar is in the shot.** Two of your screenshots have to prove *where* the page was loaded from, not just that a page loaded. If the shot is cropped so tight that nobody can see `10.0.4.71:5000` in the address bar, it does not prove anything. Capture the whole browser window.

---

### Finding your two files

They are where you made them:

```
~/YOURNAME/pi-dashboard/server.py
~/YOURNAME/pi-dashboard/static/index.html
```

In the Pi's file manager that is **Home → YOURNAME → pi-dashboard**, and `index.html` is one folder deeper, inside **static**. If you cannot find them, run this in the Terminal and it will print exactly where they are:

```bash
ls ~/YOURNAME/pi-dashboard ~/YOURNAME/pi-dashboard/static
```

---

### Getting all of it into Schoology

Pick whichever fits what you are holding.

**Your files and your Pi screenshots: submit from the Pi.** This is the short path, because everything is already on that machine.

1. Open **Chromium** on the Pi
2. Go to Schoology and log in
3. Open the assignment, click **Submit Assignment**, click **Upload**
4. When the file picker opens, go to **Home → YOURNAME → pi-dashboard** and pick `server.py`, then repeat for `static/index.html`

**Your phone screenshot: get it onto a computer first.** Email it to yourself, AirDrop it, or put it in Google Drive, then download it wherever you are submitting from. You can also just log in to Schoology in your phone's browser and upload it straight from your camera roll.

**If the Pi will not cooperate:** copy the whole `pi-dashboard` folder onto a jump drive, take it to a lab computer, and submit from there.

> **⚠️ Upload, never Create.** "Create" only accepts typed text. It will not take a file. This is the single most common way work in this class gets submitted as nothing.

**Name your files so they are readable:** `krigger-server.py`, `krigger-dashboard-on-phone.png`, `krigger-api-stats.png`. A folder of eight files called `Screenshot 2026-11-04 at 10.14.22.png` helps nobody, including you.

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Submit |
|---|---|
| 1 | `server.py` |
| 2 | `static/index.html` |
| 3 | Screenshot of your dashboard on a different device |
| 4 | Screenshot of `/api/stats` |
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
| Working Project | 10 | The server runs, the dashboard loads from a device that is not the Pi, and the numbers are live |
| Making It Yours | 5 | At least two visible changes are your own. High school: a fifth stat wired from Python through to the page |
| Understanding | 5 | The reflection explains the request, the response and the two-second timer without hand waving |
| Deliverables | 5 | Both files, both screenshots and the reflection, submitted on time |

**Bonus:**
- **+3 points** for a middle school student who completes the Stretch
- **+2 points** for a fifth stat that is not uptime, found in the psutil documentation yourself

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Server** | A computer whose job is to wait for requests and send back responses |
| **Request** | A device asking a server for something |
| **Response** | What the server sends back |
| **[Flask](https://flask.palletsprojects.com/)** | The Python tool that turns a Python file into a web server |
| **Route** | A line like `@app.route("/api/stats")` that says which request a function answers |
| **API** | A door on a server that hands back data instead of a web page |
| **[JSON](https://www.json.org/)** | A text format for data that programs can read, like `{"cpu": 45}` |
| **IP Address** | A device's house number on a network, like `10.0.4.71` |
| **Port** | The door number on that house. Ours is `5000` |
| **localhost** | A name that always means "this computer, right here" |
| **[SSH](https://www.raspberrypi.com/documentation/computers/remote-access.html)** | Secure Shell. Typing commands on one computer that run on another |
| **[HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)** | The structure of a page. What is on it |
| **[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)** | The style of a page. What it looks like |
| **[JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)** | The behavior of a page. What it does and when |
| **[DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)** | The browser's live copy of your HTML, which JavaScript can change |
| **[Virtual Environment](https://docs.python.org/3/tutorial/venv.html)** | A clean workspace holding one project's Python tools |
| **[psutil](https://psutil.readthedocs.io/)** | The Python library that reads the computer's own CPU, memory and temperature |
| **Full-Stack** | Working on both the server and the page. You did both |

---

## 💡 Troubleshooting

**"ModuleNotFoundError: No module named 'flask'"**
→ Look at your prompt. Does it start with `(YOURNAME)`? If not, run `source ~/YOURNAME/venv/bin/activate`. You need this in every new Terminal window.

**"Address already in use"**
→ Your server is already running in another Terminal window. Find it and press **Ctrl + C**. If you cannot find it, run `pkill -f YOURNAME/pi-dashboard/server.py` and start again. Never run plain `pkill -f server.py`: it stops every student's server on the Pi.

**"The page says Not Found"**
→ Run `ls ~/YOURNAME/pi-dashboard/static`. If `index.html` is not in that list, you saved it in the wrong folder.

**"My phone cannot load it"**
→ Three things, in order. Is the phone on GHCDS? Is the server still running on the Pi? Did you type `:5000` after the IP address?

**"It loads someone else's dashboard"**
→ You typed their IP. Run `hostname -I` on your Pi again and fix your sticky note.

**"Temperature shows `--`"**
→ Some Pi models do not report it. Everything else works. Leave it.

**"I changed the page and nothing happened"**
→ Stop the server (**Ctrl + C**), start it again, then hard refresh the browser with **Ctrl + Shift + R**.

**"Nothing appears when I type my password"**
→ That is deliberate. The terminal hides password characters so nobody can read them over your shoulder. Type it and press Enter.

**"I pasted into nano and it came out mangled"**
→ Paste in the Terminal is **Ctrl + Shift + V**. If the file is a mess, `rm` it and start the file over. It is faster than repairing it.

**"I broke it so badly I want to start over"**
→ `rm ~/YOURNAME/pi-dashboard/server.py` and redo Step 6. This is a normal thing that normal programmers do.

---

# Appendix: Setting Up a Pi From a Blank Card

**Skip this unless Mr. Krigger tells you to do it.** The Pis in the lab are already set up, and Day 1 assumes yours boots to a desktop. This appendix is here for the times it does not: a brand new Pi, a card that got wiped, or a class doing the whole build from scratch.

There are two walkthroughs below because the lab runs two versions of Raspberry Pi OS. **Find out which one you need before you start.** If the Pi still boots, open a Terminal and run:

```bash
cat /etc/os-release
```

Look at the `VERSION_CODENAME` line. It says either `bookworm` or `trixie`. If the card is blank and there is nothing to boot, use the Bookworm walkthrough unless you were told otherwise.

---

## Version A: Bookworm

This is the version most of the lab is running.

### A1 — Get the Imager

On any Mac or Windows computer, download and install **[Raspberry Pi Imager](https://www.raspberrypi.com/software/)**. Then put the microSD card into that computer, using an adapter if you need one.

### A2 — Choose the three things

Open Imager. It asks you three questions.

1. **Choose Device.** Pick the Pi model you are holding. It is printed on the board.
2. **Choose OS.** Bookworm is no longer the default, so it is a few clicks in: **Raspberry Pi OS (other)**, then the 64-bit Bookworm entry. Read the description before you click, it names the version.
3. **Choose Storage.** Pick your SD card.

> **⚠️ Look hard at the storage list.** Imager erases whatever you choose, completely, with no warning you can undo. If you see an external drive in that list, make very sure you are not about to pick it.

### A3 — Fill in OS customisation

Imager asks whether you want to customise before writing. **Say yes.** This is the whole reason setup is easy now. Fill in:

| Field | What to put |
|---|---|
| Hostname | Something you will recognize, like `krigger-pi` |
| Username | Your choice. Write it down. There is no default anymore |
| Password | Your choice. Write it down |
| Wireless LAN | The network name and password Mr. Krigger gives you |
| Wireless LAN country | `US` |
| Locale and time zone | Whatever the school is on |

Then open the **Services** tab and turn on **Enable SSH**, with password authentication.

> **This screen replaces three old setup steps at once.** It creates your account, joins the Wi-Fi, and turns on remote access, all before the card has ever been in a Pi. Older instructions on the internet will tell you to edit a file called `wpa_supplicant.conf` to join Wi-Fi. That has not worked since 2023. This screen is how it is done now.

> **Your password does not go in any file, ever.** You typed it here and you wrote it on paper. That is where it lives.

### A4 — Write the card

Click **Write** and wait. This takes several minutes and then verifies what it wrote, which takes several more. Leave it alone.

### A5 — First boot

Put the card in the Pi, connect the monitor, keyboard and mouse, then plug in the power last. The first boot takes longer than normal, and the Pi may restart itself once. Let it.

You should land on a desktop with a menu bar across the top.

> **✅ Checkpoint:** A desktop, and the Wi-Fi icon in the top right shows it is connected.

### A6 — Update it

Open the Terminal and run:

```bash
sudo apt update && sudo apt full-upgrade -y
```

```bash
sudo reboot
```

The first command can take fifteen minutes on a fresh card, longer if a whole class is doing it at once. This is the boring part of the job and there is no way around it.

- `sudo` means "run this as the administrator"
- `apt update` checks what new versions exist
- `full-upgrade -y` installs them, and `-y` means stop asking me to confirm
- `reboot` restarts so the updates take effect

### A7 — Confirm it is ready for Day 1

```bash
whoami
```

```bash
hostname -I
```

The first prints the username you chose in Imager. The second prints an IP address. If either one comes back empty or wrong, fix it now rather than in the middle of Day 1.

**Where things are on the Bookworm desktop**, if you need them:

| What | Where |
|---|---|
| Terminal | The black rectangle icon on the top bar |
| Thonny (Python editor) | **Menu → Programming → Thonny** |
| SSH on or off | **Menu → Preferences → Raspberry Pi Configuration → Interfaces** |
| Screenshot | **Print Screen** key |

You are ready. Go to Day 1.

---

## Version B: Trixie

Trixie is the newer Raspberry Pi OS, built on Debian 13. Some of the lab machines run it.

### B1 — Everything in A1 through A4 is the same

Same Imager, same three questions, same customisation screen, same Write button. **One difference:** at **Choose OS**, Trixie is the default now, so it is the plain **Raspberry Pi OS (64-bit)** entry at the top. You do not need to go into "other".

Do steps **A1 through A4** exactly as written above, with that one change.

### B2 — First boot

Same as A5. Card in, monitor and keyboard connected, power last, wait through a slow first boot.

The desktop looks different from Bookworm. It has been redrawn, so the icons and the wallpaper will not match what the student next to you is looking at. Nothing about this project changes because of it.

### B3 — Update it

Identical to A6:

```bash
sudo apt update && sudo apt full-upgrade -y
```

```bash
sudo reboot
```

### B4 — Confirm it is ready for Day 1

Identical to A7. Run `whoami` and `hostname -I` and write both down.

**Where things are on the Trixie desktop:**

| What | Where |
|---|---|
| Terminal | The black rectangle icon on the top bar, same as before |
| Thonny (Python editor) | **Menu → Programming → Thonny** |
| SSH on or off | **Menu → Preferences → Raspberry Pi Configuration → Interfaces** |
| Screenshot | **Print Screen**. If nothing happens, **Menu → Accessories → Screenshot** |

> **If a menu is not where this table says it is**, the desktop got rearranged in an update. Say so and Mr. Krigger will fix this table. Everything you do at the Terminal works identically on both versions, and that is a large part of why this project lives at the Terminal.

You are ready. Go to Day 1.

---

## What is actually different between the two

Short answer, for the curious: almost nothing you will touch.

| | Bookworm | Trixie |
|---|---|---|
| Debian version underneath | 12 | 13 |
| Which one Imager offers first | Under "other" | The default |
| How the desktop looks | Older look | Redrawn |
| Terminal, Python, Flask, SSH, `whoami`, `hostname -I` | Identical | Identical |
| Wi-Fi setup | NetworkManager | NetworkManager |
| Default `pi` / `raspberry` login | None | None |

Every command in Days 1 through 3 runs the same on both, and that was deliberate. Commands stay stable for decades while menus get redesigned every couple of years, so the commands are the part worth learning.

---

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] Every command checked against current Raspberry Pi OS behavior, 2026-09-16
- [x] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [x] No default pi/raspberry login assumed anywhere
- [x] Every path uses ~ , never /home/pi
- [x] Every checkpoint is something a student can actually see
- [x] Base tier is readable by a 7th grader
- [x] Safety block present
- [ ] CONFIRM ON A REAL LAB PI before teaching: username, OS version, whether
      the Pis share one login (the per-student ~/YOURNAME folders assume they do)
- [ ] CONFIRM THE TRIXIE MENU PATHS in Appendix B on an actual Trixie station.
      The Bookworm ones are known good. The Trixie table was written from the
      documented layout, not from standing in front of one.
- [ ] Site version stands alone: leave out the rubric, the point values and the
      Schoology upload steps per site rule 8
=========================================================================== -->
