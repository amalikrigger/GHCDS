<!-- ===========================================================================
TEACHER PLANNING BLOCK — delete nothing, this never renders on the site.

UNIT / FOLDER   : raspberry-pi
FILE NAME       : raspberry_pi_dashboard.md
PERIODS         : 3
FIRST TAUGHT    : T1 2026
REWRITTEN       : 2026-09-16, to the LESSON_TEMPLATE standard. Replaces the
                  4-day April 2026 version. See knowledge/decisions.md for the
                  full review of what was wrong with it.

WHAT CHANGED FROM THE OLD VERSION, AND WHY
- SD card flashing is gone. The lab Pis are already imaged with monitor
  stations, so Day 1 starts with code instead of a 15-minute apt upgrade.
- The Wi-Fi configuration step is gone. It edited
  /etc/wpa_supplicant/wpa_supplicant.conf, which Raspberry Pi OS stopped using
  in Bookworm. The Pis already join GHCDS.
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
        source ~/pihealth/bin/activate ; python3 -c "import flask, psutil"
        (if that errors, the Step 2 fallback in Day 1 is the path students take)
- [ ] Accounts or logins students need: none
- [ ] Software already on lab machines: a terminal with ssh (Day 2 only)
- [ ] Posted in the room: the Pi IP sticky-note rule, and the Ctrl+C rule
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
  Does it start with (pihealth)?
- Second terminal, server already running -> "Address already in use". Say:
  find the other window, Ctrl+C.
- Typed the IP from someone else's sticky note -> loads a classmate's page.
  This is funny once and then it is a debugging lesson about IP addresses.
- Saved index.html into ~/pi-dashboard instead of ~/pi-dashboard/static ->
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

### Step 2 — Turn on your Python workspace

Type:

```bash
source ~/pihealth/bin/activate
```

Your prompt should now start with `(pihealth)`.

**If you got an error instead**, the workspace does not exist yet. Run these three commands one at a time:

```bash
python3 -m venv ~/pihealth
```

```bash
source ~/pihealth/bin/activate
```

```bash
pip install flask psutil
```

> **What just happened?** You made a **virtual environment**, which is a clean workspace that holds the extra Python tools for one project and nothing else. Then you installed two of them: **Flask**, which lets Python run a website, and **psutil**, which lets Python read the computer's own CPU and memory numbers.

> **✅ Checkpoint:** Your prompt starts with `(pihealth)`. It will stop doing that every time you open a new Terminal window, and you will have to run the `source` line again. This catches everyone at least once.

---

### Step 3 — Make your project folder

```bash
mkdir -p ~/pi-dashboard/static && cd ~/pi-dashboard
```

You just made this:

```
pi-dashboard/
├── server.py       ← the Python that runs the server (next step)
└── static/         ← the files your server hands out
    └── index.html  ← your actual web page (Step 6)
```

The `~` means your home folder. Whatever your username is, `~` points at the right place, which is why we never type the full path.

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

The Terminal will print a few lines and then sit there looking like it is frozen. It is not frozen. It is listening.

Open **Chromium** on the Pi and go to:

```
http://localhost:5000
```

> **✅ Checkpoint:** The browser says **My Pi is a web server.** That is a real server, running on a real computer, serving a real page. It took six lines.

**To stop it:** click the Terminal window and press **Ctrl + C**. Remember this. You will need it constantly.

> **⚠️ You will also see a yellow warning** about a "development server" and not using it in production. Ignore it. It means "this server is built for learning, not for handling a million people at once," which is exactly what you are doing.

---

### 🧠 Mini Lesson — What a server actually does

A server does one thing, over and over, forever:

1. It waits.
2. Something asks it for a thing. This is a **request**.
3. It sends that thing back. This is a **response**.
4. Go to 1.

That is it. That is the whole job. When you typed `http://localhost:5000` into Chromium, the browser sent a request to your Pi. Your six lines of Python caught it, and the line `return "<h1>My Pi is a web server.</h1>"` was the response.

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
source ~/pihealth/bin/activate
cd ~/pi-dashboard
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

A name, a colon, a value, commas between them, curly braces around the whole thing. That is the entire format. Almost every app on your phone is passing JSON back and forth all day.

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
source ~/pihealth/bin/activate
cd ~/pi-dashboard
python3 server.py
```

Then open a browser on the lab computer and go to `http://YOUR-PI-IP:5000`.

You just started a server on a computer across the room and loaded its page. That is the actual job of a large number of actual people.

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

> **Nothing about the Python changes today.** The server already works. You are only replacing the page it hands out. That is how real web work usually goes: the thing underneath stays put and the thing people see gets redesigned.

### Step 1 — Start the page over

Stop your server with **Ctrl + C**. Then:

```bash
rm ~/pi-dashboard/static/index.html
```

```bash
nano ~/pi-dashboard/static/index.html
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
  * { box-sizing: border-box; }

  body {
    margin: 0;
    min-height: 100vh;
    padding: 32px 20px;
    color: #fff;
    font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
    background: linear-gradient(135deg, #0f2027, #2c5364);
  }

  h1 { margin: 0 0 4px; font-size: 28px; }
  .sub { margin: 0 0 28px; opacity: 0.7; font-size: 14px; }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 18px;
    max-width: 960px;
  }

  .card {
    padding: 20px;
    border-radius: 16px;
    border: 1px solid rgba(255, 255, 255, 0.18);
    background: rgba(255, 255, 255, 0.12);
    backdrop-filter: blur(10px);
    transition: transform 0.15s ease;
  }
  .card:hover { transform: translateY(-4px); }

  .card h2 { margin: 0 0 12px; font-size: 15px; font-weight: 600; opacity: 0.85; }

  .value { font-size: 42px; font-weight: 700; line-height: 1; }
  .unit  { font-size: 16px; font-weight: 400; opacity: 0.7; margin-left: 2px; }

  .bar {
    margin-top: 14px;
    height: 8px;
    border-radius: 999px;
    background: rgba(255, 255, 255, 0.15);
    overflow: hidden;
  }
  .fill {
    width: 0%;
    height: 100%;
    border-radius: 999px;
    background: #4ade80;
    transition: width 0.4s ease, background 0.4s ease;
  }

  .warn .fill  { background: #facc15; }
  .warn .value { color: #facc15; }
  .hot  .fill  { background: #f87171; }
  .hot  .value { color: #f87171; }
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
source ~/pihealth/bin/activate
cd ~/pi-dashboard
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

That split matters. CSS decides how things look. JavaScript decides when. Keeping those separate is most of what makes a large site possible to work on.

---

### Step 3 — Change things

Stop the server, edit `static/index.html`, save, restart, hard refresh. Repeat. You cannot break anything that a retype will not fix.

**Challenge 1 — Your colors.** Find the `linear-gradient` line and swap the two hex codes.

| Vibe | Try |
|---|---|
| Ocean | `#0093E9, #80D0C7` |
| Sunset | `#FA8BFF, #2BD2FF` |
| Forest | `#11998e, #38ef7d` |
| Near black | `#0f0f0f, #1a1a2e` |

Build your own at [coolors.co](https://coolors.co/).

**Challenge 2 — Your icons.** Swap the emoji in the `<h2>` lines. CPU could be `🧠` or `🏎️`. Temperature could be `❄️` if you are feeling optimistic.

**Challenge 3 — Your name.** Under the `<h1>`, change the `.sub` line to say whose Pi this is.

**Challenge 4 — Your thresholds.** In the `CARDS` list, change `warn` and `hot`. Set CPU's `warn` to `5` and watch the card sit in yellow permanently. Then set it back and think about why a monitoring tool that always says "warning" is worse than no monitoring tool.

**Challenge 5 — Your layout.** Change `minmax(220px, 1fr)` to `minmax(400px, 1fr)` and see what happens to the number of columns.

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
→ Look at your prompt. Does it start with `(pihealth)`? If not, run `source ~/pihealth/bin/activate`. You need this in every new Terminal window.

**"Address already in use"**
→ Your server is already running in another Terminal window. Find it and press **Ctrl + C**. If you cannot find it, run `pkill -f server.py` and start again.

**"The page says Not Found"**
→ Run `ls ~/pi-dashboard/static`. If `index.html` is not in that list, you saved it in the wrong folder.

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
→ `rm ~/pi-dashboard/server.py` and redo Step 6. This is a normal thing that normal programmers do.

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
      the pihealth venv and flask/psutil already exist
- [ ] Site version stands alone: leave out the rubric, the point values and the
      Schoology upload steps per site rule 8
=========================================================================== -->
