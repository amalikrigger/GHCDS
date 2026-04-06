# 🖥️ Raspberry Pi Health Dashboard

### Build a live system monitor from scratch — then make it look amazing

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 4 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> By the end of this project, you'll have a Raspberry Pi running a website that shows its CPU, memory, disk, and temperature — live — with a professional-looking dashboard you built yourself. Other devices on your network can visit it too.

---

## 🎯 What You'll Learn

- How to set up a Raspberry Pi from scratch
- What a **web server** is and how to run one
- Basics of **Python**, **HTML**, **CSS**, and **JavaScript**
- How to connect to your Pi remotely using **SSH**
- How to read system stats with code

---

## 💡 Why Should You Care?

Every app on your phone, every website you visit, every online game you play — they all run on **servers**. Netflix has servers. Instagram has servers. Even your school's Wi-Fi has a server managing it.

In this project, **you're building your own server.** Your Raspberry Pi will run a live website that anyone on your network can visit — just like a real website, except you built it and you control it.

This isn't just a school project. These are the same skills used by:
- **Software engineers** at companies like Google, Apple, and Netflix
- **Cybersecurity analysts** who monitor systems for threats
- **IT professionals** who keep networks and servers running
- **Game developers** who run multiplayer game servers

Even if you're not planning a career in tech, understanding how the internet actually works gives you a huge advantage in almost any field.

---

## 🧰 What You Need

- [Raspberry Pi](https://www.raspberrypi.com/) (any modern model) + microSD card (16 GB or bigger)
- Power supply + HDMI cable + monitor + keyboard + mouse
- Wi-Fi or Ethernet connection
- Another device on the same network (laptop, phone, or Chromebook) — optional but fun

---

# Day 1: Set Up Your Pi + Run Your First Server

**Goal:** Go from a blank SD card to a working web page on your Pi.

---

### Step 1 — Flash the Operating System

The Raspberry Pi is a tiny computer, but it has no operating system out of the box. We need to install one.

1. On any computer, download and install **[Raspberry Pi Imager](https://www.raspberrypi.com/software/)**
2. Plug your microSD card into that computer
3. Open Raspberry Pi Imager
4. Click **Choose OS** → pick **Raspberry Pi OS (64-bit)**
5. Click **Choose Storage** → pick your microSD card
6. *(Optional)* Click the **gear ⚙️** icon to pre-set your Wi-Fi name and password
7. Click **Write** and wait for it to finish
8. Put the microSD card into your Pi, plug in the monitor/keyboard/mouse, and power it on
9. Follow the on-screen setup wizard (language, Wi-Fi, etc.)

> 📖 **Need more help?** See the official [Raspberry Pi Getting Started Guide](https://www.raspberrypi.com/documentation/computers/getting-started.html)

> **✅ Checkpoint:** You should see the Raspberry Pi desktop on your monitor.

---

### Step 2 — Update Your Pi

Updates keep your Pi secure and make sure everything works.

> **🤔 What is a Terminal?** The Terminal is a way to talk to your computer by typing commands instead of clicking buttons. It might look intimidating at first (like something from a hacker movie), but it's actually just a different way to do the same things you do with your mouse. Think of it like texting your computer instead of tapping on icons. Every command you type tells the computer to do one specific thing.

1. Click the **Terminal** icon on the top bar (it looks like a black rectangle)
2. Type this command and press Enter:

```bash
sudo apt update && sudo apt -y full-upgrade && sudo reboot
```

3. Your Pi will restart. Wait for it to come back to the desktop.

> **What just happened?** Let's break that long command down piece by piece:
> - `sudo` = "Super User DO" — it means "run this as the administrator." Your Pi won't let you install things without this, just like how your phone asks for a password before installing apps.
> - `apt update` = Check online for any available updates (like checking the App Store for updates)
> - `&&` = "and then do this next thing" — it chains commands together
> - `apt -y full-upgrade` = Download and install all updates. The `-y` means "yes, do it without asking me to confirm each one"
> - `sudo reboot` = Restart the computer so the updates take effect
>
> **⏳ This step can take 5–15 minutes.** That's normal — just let it run. Go get a snack.

---

### Step 3 — Install the Tools We Need

> **🌍 Real-World Connection:** Almost every major website and app uses these same tools. Instagram's backend was built with Python. Flask is used by companies like Pinterest and LinkedIn for parts of their websites. You're learning the same technology the pros use.

We're going to use **[Python](https://www.python.org/)** (a programming language) to run a mini web server. We need two add-ons:
- **[Flask](https://flask.palletsprojects.com/)** — lets Python serve web pages
- **[psutil](https://psutil.readthedocs.io/)** — lets Python read CPU, memory, and temperature info

1. Open **Terminal** and type these commands one at a time:

```bash
sudo apt -y install python3-pip python3-venv
```

```bash
python3 -m venv ~/pihealth
```

```bash
source ~/pihealth/bin/activate
```

```bash
pip install flask psutil
```

> **What just happened?**
> - We installed tools for Python packages
> - We created a **[virtual environment](https://docs.python.org/3/tutorial/venv.html)** — think of it like a clean workspace just for this project
> - We activated it (your terminal prompt now starts with `(pihealth)`)
> - We installed Flask and psutil inside that workspace

> **✅ Checkpoint:** Your terminal prompt should show `(pihealth)` at the beginning.

---

### Step 4 — Create Your Project Folder

```bash
mkdir -p ~/pi-health-web && cd ~/pi-health-web
```

This creates a folder called `pi-health-web` and moves you into it.

---

### Step 5 — Write Your First Web Server

Now the fun part. We're going to create one Python file that does everything: reads your Pi's stats and shows them on a web page.

1. Open the file in the text editor:

> **🤔 What is `nano`?** Nano is a simple text editor that runs inside the Terminal. It's like Notepad, but it lives in the Terminal instead of opening a separate window. Don't worry — we'll switch to a friendlier editor (Thonny) on Day 3.

```bash
nano system_monitor.py
```

2. **Copy and paste this entire code block** into the editor:

```python
from flask import Flask, jsonify, render_template_string
import psutil
import subprocess

app = Flask(__name__)

PAGE = """
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Pi Health Monitor</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
      body {
        font-family: Arial, sans-serif;
        margin: 20px;
        background-color: #f0f0f0;
      }
      h1 {
        color: #333;
      }
      .card {
        background: white;
        border-radius: 10px;
        padding: 20px;
        max-width: 400px;
        box-shadow: 0 2px 8px rgba(0,0,0,0.1);
      }
      .stat {
        font-size: 18px;
        margin: 10px 0;
      }
      .label {
        font-weight: bold;
      }
      .success {
        margin-top: 20px;
        padding: 10px;
        background: #d4edda;
        border-radius: 8px;
        color: #155724;
        font-family: monospace;
      }
    </style>
  </head>
  <body>
    <h1>Raspberry Pi Health Monitor</h1>
    <p>This page updates every 2 seconds.</p>
    <div class="card">
      <div class="stat"><span class="label">CPU Usage:</span> <span id="cpu">--</span>%</div>
      <div class="stat"><span class="label">Memory Used:</span> <span id="mem">--</span>%</div>
      <div class="stat"><span class="label">Disk Used:</span> <span id="disk">--</span>%</div>
      <div class="stat"><span class="label">Temperature:</span> <span id="temp">--</span> °C</div>
      <div class="success">✅ You have successfully finished Day 1!</div>
    </div>

    <script>
      async function loadStats() {
        try {
          const response = await fetch('/api/stats');
          const data = await response.json();
          document.getElementById('cpu').textContent = Math.round(data.cpu);
          document.getElementById('mem').textContent = Math.round(data.mem_percent);
          document.getElementById('disk').textContent = Math.round(data.disk_percent);
          document.getElementById('temp').textContent =
            data.temp_c === null ? '--' : data.temp_c.toFixed(1);
        } catch (e) {
          console.error(e);
        }
      }
      loadStats();
      setInterval(loadStats, 2000);
    </script>
  </body>
</html>
"""


def get_temperature_c():
    """Try to read the Pi's temperature."""
    try:
        temps = psutil.sensors_temperatures()
        for entries in temps.values():
            for e in entries:
                if getattr(e, 'current', None) is not None:
                    return float(e.current)
    except Exception:
        pass
    try:
        out = subprocess.check_output(["vcgencmd", "measure_temp"], text=True)
        if "temp=" in out:
            return float(out.split("=")[1].split("'")[0])
    except Exception:
        pass
    return None


@app.route("/")
def index():
    return render_template_string(PAGE)


@app.route("/api/stats")
def stats():
    cpu = psutil.cpu_percent(interval=0.2)
    vm = psutil.virtual_memory()
    du = psutil.disk_usage('/')
    temp_c = get_temperature_c()
    return jsonify({
        "cpu": cpu,
        "mem_percent": vm.percent,
        "disk_percent": du.percent,
        "temp_c": temp_c
    })


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

3. Save the file: press **Ctrl + O**, then **Enter**
4. Exit the editor: press **Ctrl + X**

> **What just happened?** You created a Python program that does two things:
> - When someone visits your Pi's web page, it sends them the HTML (the page layout)
> - The page calls `/api/stats` every 2 seconds to get fresh CPU, memory, disk, and temperature numbers
> - The JavaScript on the page updates the numbers without refreshing

> **🌍 Real-World Connection:** This is exactly how apps like Weather or Stocks on your phone work. The app (like your web page) calls a server (like your Python code) every few seconds asking "what's the latest data?" and then updates what you see on screen. You just built that same pattern from scratch.

---

### 🌐 Mini Lesson — The 3 Languages of Every Website

Every website you've ever visited is built with three languages working together. You just used all three in the code you pasted:

**[HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) = The Structure (skeleton)**
HTML uses **tags** like `<h1>`, `<div>`, and `<span>` to define *what* is on the page. Look at this line from your code:

```html
<h1>Raspberry Pi Health Monitor</h1>
```

The `<h1>` tag means "this is a big heading." The text between the opening tag `<h1>` and the closing tag `</h1>` is what shows up on screen. Other tags you used: `<div>` (a container/box), `<p>` (a paragraph), `<span>` (a small piece of text inside a line).

**[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) = The Style (clothes and makeup)**
CSS controls how things *look* — colors, sizes, spacing, fonts. Look at this block from your code:

```css
.card {
  background: white;
  border-radius: 10px;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}
```

This says: "Anything with `class="card"` should have a white background, rounded corners (`border-radius`), spacing inside (`padding`), and a subtle shadow." Try changing `white` to `lightblue` later and see what happens!

**[JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript) = The Behavior (the brain)**
JavaScript makes the page *do things*. Look at this line:

```javascript
setInterval(loadStats, 2000);
```

This tells the browser: "Run the `loadStats` function every 2000 milliseconds (2 seconds)." That's why your numbers update automatically without you refreshing the page.

> **Think of it this way:** HTML is like building a house (walls, rooms, doors). CSS is painting it and choosing furniture. JavaScript is the electricity that makes things move and respond.

---

### Step 6 — Run It!

Make sure your virtual environment is active (you should see `(pihealth)` in your prompt). If not, run:

```bash
source ~/pihealth/bin/activate
```

Then start the server:

```bash
cd ~/pi-health-web
python3 system_monitor.py
```

Open **Chromium** (the web browser on your Pi) and go to:

```
http://localhost:5000
```

> **✅ Checkpoint:** You should see a white card with CPU, Memory, Disk, and Temperature updating live, plus a green "You have successfully finished Day 1!" message.

**To stop the server:** Click on the Terminal window and press **Ctrl + C**.

---

### 📝 Day 1 Deliverables

1. Screenshot of your health monitor page running in the browser
2. Screenshot of the Terminal showing the server is running

---

# Day 2: Connect to Your Pi Remotely with SSH

**Goal:** Control your Pi from another computer — no monitor needed.

---

### What is SSH?

Imagine you could pick up your phone, type a command, and control a computer that's in another room — or another country. That's **SSH** (Secure Shell).

It lets you type commands on your Pi from a different computer, as if you were sitting right in front of it. No monitor, no keyboard, no mouse needed — just a Wi-Fi connection.

**This is how the real world works:**
- IT professionals fix servers in data centers without being in the building
- NASA engineers send commands to computers on the International Space Station
- Game server admins manage Minecraft and Discord servers from their laptops
- Your school's IT department manages every computer in the building from one desk

After today, you'll be able to control your Pi from your phone or laptop. That's a real superpower.

> 📖 **Want to go deeper?** [Raspberry Pi Remote Access Documentation](https://www.raspberrypi.com/documentation/computers/remote-access.html)

---

### Step 1 — Enable SSH on Your Pi

1. On your Pi, click the **Raspberry Pi menu** (top-left) → **Preferences** → **Raspberry Pi Configuration**
2. Click the **Interfaces** tab
3. Find **SSH** and click **Enable**
4. Click **OK**

Or if you prefer the terminal:

```bash
sudo raspi-config
```

Go to **Interface Options → SSH → Enable**, then exit.

---

### Step 2 — Connect to the GHCDS Classroom Wi-Fi

Your Pi needs to auto-connect to the classroom network every time it boots up.

1. Open Terminal and type:

```bash
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

2. Add this block at the bottom of the file (if it's not already there):

```
network={
  ssid="GHCDS"
  key_mgmt=NONE
}
```

3. Save: **Ctrl + O**, **Enter**
4. Exit: **Ctrl + X**
5. Reboot to confirm it reconnects automatically:

```bash
sudo reboot
```

> **What just happened?** You told your Pi the name of your classroom Wi-Fi network. Now every time the Pi turns on, it will automatically connect to `GHCDS` without you having to click anything.

---

### Step 3 — Find Your Pi's IP Address

Once your Pi is back on and connected to Wi-Fi, open Terminal and run:

```bash
hostname -I
```

This prints your Pi's **IP address** — something like `192.168.1.50`. **Write this number down.** You'll need it in a minute.

> **What's an IP address?** Think of your Wi-Fi network like a neighborhood. Every device (your phone, your laptop, the Pi) gets its own house number so they can find each other. That number is the IP address. When you type it into a browser, you're basically saying "take me to that house."

---

### Step 4 — SSH In from Another Computer

On a **different computer** connected to the same Wi-Fi:

**On Mac or Chromebook:** Open Terminal and type:

```bash
ssh pi@YOUR-PI-IP-ADDRESS
```

For example:

```bash
ssh pi@192.168.1.50
```

**On Windows:** Open PowerShell or Command Prompt and type the same command.

It will ask for a password. Type the password you set during Pi setup (the default is `raspberry`).

> **What just happened?** You're now controlling your Pi from another computer. Everything you type runs on the Pi, not on the computer in front of you.

---

### Step 5 — Prove It Works

While connected via SSH, run:

```bash
uname -a
```

This shows system info from the Pi. You should see "Linux raspberrypi" in the output.

To leave the SSH session:

```bash
exit
```

---

### Step 6 — Start Your Server Remotely (Bonus)

Now that you know SSH, you can start your health monitor without touching the Pi:

```bash
ssh pi@YOUR-PI-IP-ADDRESS
source ~/pihealth/bin/activate
cd ~/pi-health-web
python3 system_monitor.py
```

Then on your laptop's browser, go to:

```
http://YOUR-PI-IP-ADDRESS:5000
```

Your dashboard loads — from a server you started remotely. That's real engineering.

> **✅ Checkpoint:** You can see your Pi's health dashboard in a browser on a different device.

---

### 📝 Day 2 Deliverables

1. Screenshot of your Terminal showing a successful SSH login
2. The IP address or hostname you used to connect
3. Screenshot of `uname -a` output while connected via SSH

---

# Day 3: Make Your Dashboard Look Professional

**Goal:** Replace the plain page with a modern, animated dashboard — and understand the code.

---

> **🎮 Think about it:** Have you ever noticed how some websites look old and boring, while others look sleek and modern? The difference is usually just CSS — the *exact same data* displayed with better styling. That's what you're about to do. Same Pi, same stats, totally different vibe.

### What's Changing?

Right now your dashboard works, but it looks basic. We're going to upgrade the **HTML and CSS only** — the Python backend stays exactly the same. This is how real web development works: you can completely change how a site looks without changing how it works.

---

### Step 1 — Open Your File in Thonny

**[Thonny](https://thonny.org/)** is a beginner-friendly code editor that's already installed on your Pi. It has a normal window with menus, so it's much easier than editing in the terminal.

1. On your Pi desktop, click **Menu** (top-left raspberry icon) → **Programming** → **Thonny**
2. In Thonny, click **File → Open**
3. Navigate to `/home/pi/pi-health-web/` (or wherever your project folder is)
4. Open **`system_monitor.py`**

You should see your Python code from Day 1 in the editor window.

---

### Step 2 — Select and Delete the Old HTML

1. Find the line that says `PAGE = """`
2. Click right before the `P` in `PAGE`
3. Scroll down until you find the matching closing `"""`  (it's after all the HTML and before `def get_temperature_c():`)
4. Hold **Shift** and click right after that closing `"""`
5. Everything between should now be highlighted in blue
6. Press **Delete** or **Backspace**

> **What just happened?** You removed the old simple HTML page. Now we'll paste in the upgraded version.

---

### Step 3 — Paste the New Dashboard

Click where the old `PAGE` block was (your cursor should be on a blank line before `def get_temperature_c():`).

> **😅 Don't panic!** This is a lot of code, but you don't need to understand every single line right now. You're going to paste it, see it work, and then we'll walk through the important parts together. Professional developers copy and paste code all the time — the skill is knowing *what* the code does, not memorizing it.

**Copy everything in the box below and paste it into Thonny** (Ctrl+V or Edit → Paste):

```python
PAGE = """
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Pi Health Dashboard</title>
  <style>
    /* --- BASE STYLES --- */
    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: Arial, Helvetica, sans-serif;
      background: linear-gradient(135deg, #667eea, #764ba2);
      min-height: 100vh;
      padding: 20px;
      color: white;
    }

    h1 {
      text-align: center;
      font-size: 2em;
      margin-bottom: 5px;
    }

    .subtitle {
      text-align: center;
      opacity: 0.8;
      margin-bottom: 30px;
      font-size: 0.9em;
    }

    /* --- CARD GRID --- */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
      max-width: 1000px;
      margin: 0 auto 30px;
    }

    .card {
      background: rgba(255, 255, 255, 0.15);
      border: 1px solid rgba(255, 255, 255, 0.25);
      border-radius: 16px;
      padding: 24px;
      text-align: center;
      backdrop-filter: blur(10px);
      transition: transform 0.2s;
    }

    .card:hover {
      transform: translateY(-4px);
    }

    .card h3 {
      font-size: 1em;
      margin-bottom: 12px;
      opacity: 0.9;
    }

    /* --- CIRCULAR PROGRESS --- */
    .circle-wrap {
      width: 120px;
      height: 120px;
      margin: 0 auto 12px;
      position: relative;
    }

    .circle-wrap svg {
      width: 120px;
      height: 120px;
    }

    .circle-bg {
      fill: none;
      stroke: rgba(255,255,255,0.15);
      stroke-width: 8;
    }

    .circle-fill {
      fill: none;
      stroke-width: 8;
      stroke-linecap: round;
      transform: rotate(-90deg);
      transform-origin: center;
      transition: stroke-dasharray 0.5s ease;
    }

    .circle-text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 1.5em;
      font-weight: bold;
    }

    /* --- TEMPERATURE BAR --- */
    .temp-value {
      font-size: 2.2em;
      font-weight: bold;
      margin-bottom: 10px;
    }

    .temp-bar-bg {
      width: 100%;
      height: 10px;
      background: rgba(255,255,255,0.2);
      border-radius: 5px;
      overflow: hidden;
      margin-bottom: 10px;
    }

    .temp-bar-fill {
      height: 100%;
      border-radius: 5px;
      transition: width 0.5s ease, background 0.5s ease;
    }

    /* --- STATUS LABEL --- */
    .status {
      font-size: 0.9em;
      font-weight: 600;
    }

    .ok { color: #6ee7b7; }
    .warn { color: #fcd34d; }
    .bad { color: #fca5a5; }

    /* --- FOOTER STATUS BAR --- */
    .status-bar {
      max-width: 1000px;
      margin: 0 auto;
      background: rgba(255,255,255,0.1);
      border-radius: 12px;
      padding: 14px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.85em;
    }

    .live-dot {
      width: 8px;
      height: 8px;
      background: #6ee7b7;
      border-radius: 50%;
      display: inline-block;
      margin-right: 8px;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.4; }
    }
  </style>
</head>
<body>

  <h1>Raspberry Pi Health Dashboard</h1>
  <p class="subtitle">Live stats · updates every 2 seconds</p>

  <div class="grid">

    <!-- CPU Card -->
    <div class="card">
      <h3>🔲 CPU Usage</h3>
      <div class="circle-wrap">
        <svg viewBox="0 0 120 120">
          <circle class="circle-bg" cx="60" cy="60" r="50"/>
          <circle class="circle-fill" id="cpu-ring" cx="60" cy="60" r="50"
                  stroke="#6ee7b7" stroke-dasharray="0 314"/>
        </svg>
        <div class="circle-text" id="cpu-val">--%</div>
      </div>
      <div class="status" id="cpu-status">--</div>
    </div>

    <!-- Memory Card -->
    <div class="card">
      <h3>💾 Memory Used</h3>
      <div class="circle-wrap">
        <svg viewBox="0 0 120 120">
          <circle class="circle-bg" cx="60" cy="60" r="50"/>
          <circle class="circle-fill" id="mem-ring" cx="60" cy="60" r="50"
                  stroke="#a78bfa" stroke-dasharray="0 314"/>
        </svg>
        <div class="circle-text" id="mem-val">--%</div>
      </div>
      <div class="status" id="mem-status">--</div>
    </div>

    <!-- Disk Card -->
    <div class="card">
      <h3>💿 Disk Used</h3>
      <div class="circle-wrap">
        <svg viewBox="0 0 120 120">
          <circle class="circle-bg" cx="60" cy="60" r="50"/>
          <circle class="circle-fill" id="disk-ring" cx="60" cy="60" r="50"
                  stroke="#22d3ee" stroke-dasharray="0 314"/>
        </svg>
        <div class="circle-text" id="disk-val">--%</div>
      </div>
      <div class="status" id="disk-status">--</div>
    </div>

    <!-- Temperature Card -->
    <div class="card">
      <h3>🌡️ Temperature</h3>
      <div class="temp-value" id="temp-val">--°C</div>
      <div class="temp-bar-bg">
        <div class="temp-bar-fill" id="temp-bar" style="width:0%"></div>
      </div>
      <div class="status" id="temp-status">--</div>
    </div>

  </div>

  <div class="status-bar">
    <div><span class="live-dot"></span> System Online</div>
    <div>Last updated: <span id="timestamp">--</span></div>
  </div>

  <script>
    // The circumference of our SVG circle (2 × π × radius 50)
    const C = 2 * Math.PI * 50;  // ≈ 314

    function setRing(id, pct, color) {
      var el = document.getElementById(id);
      el.style.strokeDasharray = (pct / 100) * C + " " + C;
      el.style.stroke = color;
    }

    function pick(val, lo, hi) {
      // Returns "ok", "warn", or "bad" based on thresholds
      if (val < lo) return "ok";
      if (val < hi) return "warn";
      return "bad";
    }

    function label(level) {
      if (level === "ok") return "Normal";
      if (level === "warn") return "Warning";
      return "Critical";
    }

    async function refresh() {
      try {
        var r = await fetch("/api/stats");
        var d = await r.json();

        var cpu = Math.round(d.cpu);
        var mem = Math.round(d.mem_percent);
        var disk = Math.round(d.disk_percent);
        var temp = d.temp_c;

        // CPU
        var cpuLvl = pick(cpu, 30, 70);
        setRing("cpu-ring", cpu, cpuLvl === "ok" ? "#6ee7b7" : cpuLvl === "warn" ? "#fcd34d" : "#fca5a5");
        document.getElementById("cpu-val").textContent = cpu + "%";
        document.getElementById("cpu-status").textContent = label(cpuLvl);
        document.getElementById("cpu-status").className = "status " + cpuLvl;

        // Memory
        var memLvl = pick(mem, 60, 80);
        setRing("mem-ring", mem, memLvl === "ok" ? "#a78bfa" : memLvl === "warn" ? "#fcd34d" : "#fca5a5");
        document.getElementById("mem-val").textContent = mem + "%";
        document.getElementById("mem-status").textContent = label(memLvl);
        document.getElementById("mem-status").className = "status " + memLvl;

        // Disk
        var diskLvl = pick(disk, 70, 85);
        setRing("disk-ring", disk, diskLvl === "ok" ? "#22d3ee" : diskLvl === "warn" ? "#fcd34d" : "#fca5a5");
        document.getElementById("disk-val").textContent = disk + "%";
        document.getElementById("disk-status").textContent = label(diskLvl);
        document.getElementById("disk-status").className = "status " + diskLvl;

        // Temperature
        if (temp === null || temp === undefined) {
          document.getElementById("temp-val").textContent = "--°C";
          document.getElementById("temp-bar").style.width = "0%";
          document.getElementById("temp-status").textContent = "Unavailable";
        } else {
          temp = Number(temp);
          document.getElementById("temp-val").textContent = temp.toFixed(1) + "°C";
          var pct = Math.max(0, Math.min(100, (temp - 20) * 1.5));
          document.getElementById("temp-bar").style.width = pct + "%";
          var tLvl = pick(temp, 45, 60);
          document.getElementById("temp-bar").style.background =
            tLvl === "ok" ? "#22d3ee" : tLvl === "warn" ? "#fcd34d" : "#fca5a5";
          document.getElementById("temp-status").textContent = label(tLvl);
          document.getElementById("temp-status").className = "status " + tLvl;
        }

        document.getElementById("timestamp").textContent = new Date().toLocaleTimeString();
      } catch (e) {
        console.error(e);
      }
    }

    refresh();
    setInterval(refresh, 2000);
  </script>

</body>
</html>
"""
```

4. Save the file: **File → Save** (or **Ctrl + S**)

> **✅ Checkpoint:** Your code should now have the new `PAGE = """..."""` block with all the fancy HTML, and the Python functions below it should be untouched.

---

### Step 4 — Understanding What You Just Pasted

That was a lot of code! Let's break down the new skills you just leveled up on.

---

**🔵 CSS You Learned — Making Things Look Good**

**[Gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/gradient/linear-gradient)** — Instead of a flat color, you used a smooth blend between two colors:

```css
background: linear-gradient(135deg, #667eea, #764ba2);
```

The `135deg` is the angle of the blend. `#667eea` (blue) fades into `#764ba2` (purple). Every color on the web has a **hex code** — a 6-character code that mixes red, green, and blue.

**[CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)** — You arranged the 4 cards in a responsive row:

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}
```

This says: "Make as many columns as will fit, each at least 220px wide, with 20px space between them." Resize your browser window and watch the cards rearrange — that's **[responsive design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)**.

**Glassmorphism** — That frosted glass effect on the cards:

```css
background: rgba(255, 255, 255, 0.15);
backdrop-filter: blur(10px);
```

`rgba` is a color with transparency (the `0.15` means 15% visible). [`backdrop-filter: blur`](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter) blurs whatever is behind the card. This is a trendy design style used by Apple and many modern apps.

**[Hover animations](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)** — Cards move up slightly when you hover over them:

```css
.card:hover {
  transform: translateY(-4px);
}
```

The `:hover` part means "when the mouse is over this element." `translateY(-4px)` shifts it up by 4 pixels.

---

**🟡 JavaScript You Learned — Making Things Dynamic**

**[Fetching data from an API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API):**

```javascript
var r = await fetch("/api/stats");
var d = await r.json();
```

This calls your Python server's `/api/stats` endpoint and converts the response from [JSON](https://www.json.org/) (a data format) into a JavaScript object you can use.

**Changing the page without refreshing:**

```javascript
document.getElementById("cpu-val").textContent = cpu + "%";
```

`document.getElementById` finds an HTML element by its `id`, and `.textContent` changes what text it displays. This is called **[DOM manipulation](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)** — the DOM is the browser's live version of your HTML.

**[SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) circles for progress rings:**

```javascript
el.style.strokeDasharray = (pct / 100) * C + " " + C;
```

SVG (Scalable Vector Graphics) lets you draw shapes with code. The progress rings are circles where `strokeDasharray` controls how much of the circle is "filled in" vs invisible. Math meets art!

---

> **The big picture:** Your project now uses **4 languages working together**: Python (server/data), HTML (structure), CSS (style), and JavaScript (behavior). That's a real full-stack web application.

---

### Step 5 — Run and Admire

**Option A — Run from Thonny:**
1. In Thonny, go to **Tools → Options → Interpreter**
2. Set the interpreter to **`/home/pi/pihealth/bin/python3`**
3. Click **OK**, then click the green **Run** button (▶)

**Option B — Run from Terminal:**

```bash
source ~/pihealth/bin/activate
cd ~/pi-health-web
python3 system_monitor.py
```

Open your browser to `http://localhost:5000`

> **✅ Checkpoint:** You should see a purple gradient background with 4 frosted-glass cards showing live stats with animated circular progress rings.

Try viewing it from another device too:

```
http://YOUR-PI-IP-ADDRESS:5000
```

---

### 📝 Day 3 Deliverables

1. Screenshot of your new dashboard running in the browser
2. Screenshot of your Terminal or Thonny showing the server running
3. The URL you used to access it

---

# Day 4: Explore and Customize

**Goal:** Make the dashboard your own. Change colors, add features, break stuff and fix it.

---

> **🏆 You've already done the hard part.** Everything from here is about playing and experimenting. There are no wrong answers — if you break something, just undo your change and try again. Real developers spend most of their time experimenting just like this.

### Challenge 1 — Change the Background Colors

Find this line in the CSS:

```css
background: linear-gradient(135deg, #667eea, #764ba2);
```

Try changing the two hex colors. Here are some combos to try:

| Vibe | Code |
|---|---|
| Ocean | `#0093E9, #80D0C7` |
| Sunset | `#FA8BFF, #2BD2FF` |
| Forest | `#11998e, #38ef7d` |
| Dark mode | `#0f0f0f, #1a1a2e` |

---

### Challenge 2 — Change the Card Emoji Icons

Find lines like `<h3>🔲 CPU Usage</h3>` and swap the emoji:

- CPU: try `⚡` or `🧠`
- Memory: try `📊` or `🗄️`
- Disk: try `💽` or `📁`
- Temperature: try `🔥` or `❄️`

---

### Challenge 3 — Add Your Name

After the `<h1>` tag, add:

```html
<p class="subtitle">Built by [YOUR NAME] 🚀</p>
```

---

### Challenge 4 — Change the Warning Thresholds

In the JavaScript, find the `pick()` calls:

```javascript
var cpuLvl = pick(cpu, 30, 70);
```

The two numbers are the thresholds. CPU below 30 = green, 30–70 = yellow, above 70 = red. Try adjusting them and watch the colors change.

---

### Challenge 5 (Advanced) — Add Uptime

In `system_monitor.py`, find the `stats()` function. Add one more line of data:

```python
import time  # Add this at the top of the file with the other imports

# Inside the stats() function, add:
"uptime_minutes": round((time.time() - psutil.boot_time()) / 60)
```

Then in the HTML, add a new card or line that displays it using JavaScript.

---

### 📝 Day 4 Deliverables

1. Screenshot of your customized dashboard (different colors, your name, etc.)
2. A short reflection (3–5 sentences): What did you change? What was the hardest part? What would you add if you had more time?

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Setup & Server | 5 | Pi is set up, server runs, page loads |
| SSH Connection | 5 | Successfully connected remotely, screenshots prove it |
| Dashboard Upgrade | 5 | Modern dashboard is running with live data |
| Customization | 5 | Made at least 2 visible changes to the design |
| Deliverables | 5 | All screenshots and reflections submitted |

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Server** | A computer that serves content to other devices |
| **[Flask](https://flask.palletsprojects.com/)** | A Python tool for building web servers |
| **API** | A way for programs to talk to each other (our page talks to Python via `/api/stats`) |
| **[JSON](https://www.json.org/)** | A text format for sending data between programs — looks like `{"cpu": 45}` |
| **[SSH](https://www.raspberrypi.com/documentation/computers/remote-access.html)** | Secure Shell — remote access to another computer's terminal |
| **IP Address** | A device's number on a network (like `192.168.1.50`) |
| **[HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)** | The structure/skeleton of a web page — uses tags like `<div>`, `<h1>`, `<p>` |
| **[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)** | The styling — colors, fonts, layout, animations |
| **[JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)** | The behavior — makes the page interactive and dynamic |
| **[DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)** | Document Object Model — the browser's live version of your HTML that JavaScript can change |
| **Hex Color** | A 6-character code for colors, like `#667eea` (blue) or `#ff0000` (red) |
| **[CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)** | A layout system that arranges elements in rows and columns |
| **[Responsive Design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)** | A page that looks good on any screen size (phone, tablet, laptop) |
| **[SVG](https://developer.mozilla.org/en-US/docs/Web/SVG)** | Scalable Vector Graphics — drawing shapes (like our progress circles) with code |
| **[Virtual Environment](https://docs.python.org/3/tutorial/venv.html)** | An isolated workspace for Python packages |
| **[psutil](https://psutil.readthedocs.io/)** | A Python library that reads system stats |
| **Full-Stack** | Working with both the server (backend) and the web page (frontend) |

---

## 💡 Troubleshooting

**"I can't see `(pihealth)` in my terminal"**
→ Run `source ~/pihealth/bin/activate`

**"The page won't load from another device"**
→ Make sure both devices are on the same Wi-Fi. Use `hostname -I` on the Pi to get the correct IP.

**"Temperature shows -- or Unavailable"**
→ That's normal on some Pi models. Everything else should still work.

**"I made a change but the page looks the same"**
→ Stop the server (Ctrl+C), restart it, and hard-refresh the browser (Ctrl+Shift+R).

**"I get 'command not found' when I try to run something"**
→ You probably forgot to activate the virtual environment. Run `source ~/pihealth/bin/activate` first. You need to do this every time you open a new Terminal window.

**"I get 'Address already in use' when starting the server"**
→ Your server is already running in another Terminal window. Find that window and press Ctrl+C to stop it first, then try again.

**"The code won't paste into Nano"**
→ In the Terminal, paste is usually **Ctrl+Shift+V** (not Ctrl+V). Or right-click and choose Paste.

**"I accidentally messed up the code and nothing works"**
→ Don't worry — that happens to every programmer! You can always delete the file and start over:
→ `rm ~/pi-health-web/system_monitor.py` then redo Step 5.
