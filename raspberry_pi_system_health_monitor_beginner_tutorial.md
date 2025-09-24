# Raspberry Pi “System Monitor” Web Server — Beginner Tutorial

Welcome, makers! In this project, you’ll transform a Raspberry Pi into a mini web server that displays **live system health**: CPU %, memory use, disk usage, and temperature. You’ll learn exactly **what to do and why** as you go. By the end you’ll open a webpage (from your Pi!) that proudly says: **“You have successfully finished.”**

> **Difficulty:** Beginner\
> **Time:** \~60–90 minutes\
> **You’ll build:** A local website that updates your Pi’s health stats\
> **No SSH needed:** You will use the Pi with a monitor, keyboard, and mouse.

---

## 0) What You Need

1. Raspberry Pi (any modern model) + microSD card (≥16 GB)
2. Power supply, **HDMI cable, monitor, keyboard, and mouse** (we’ll work directly on the Pi)
3. Wi‑Fi or Ethernet
4. (Optional) Another device on the same network (laptop/phone/Chromebook) to view the site

> **Why these items?** The Pi is a small computer. We’ll connect it directly to a screen and use a keyboard/mouse so beginners don’t need remote tools like SSH.

---

## 1) Flash the Latest Raspberry Pi OS

1. On any computer, install **Raspberry Pi Imager**: [https://www.raspberrypi.com/software/](https://www.raspberrypi.com/software/)
2. Insert the microSD card into that computer.
3. Open Raspberry Pi Imager → **Choose OS → Raspberry Pi OS (64‑bit)**.
4. **Choose Storage →** your microSD.
5. (Optional) Click the **gear ⚙️** icon to preset Wi‑Fi, locale/timezone, or a password if desired. (SSH is **not** required for this project.)
6. Click **Write**. When finished, put the card into the Pi, connect monitor/keyboard/mouse, and power on.
7. Complete the first‑boot setup wizard on the Pi (language, Wi‑Fi, update popup, etc.).

> **Why flash an OS?** The Pi needs an operating system (like Windows or macOS for a PC). Raspberry Pi OS includes a desktop, web browser, and the tools we’ll need.

---

## 2) First Boot & Update (on the Pi)

1. On the Pi desktop, open **Terminal** (black icon on the top bar or in the menu).
2. Run the update command:

```bash
$ sudo apt update && sudo apt -y full-upgrade && sudo reboot
```

3. The Pi will reboot. Log back into the desktop when it finishes.

> **Why update?** Updates give you security fixes and the newest software so everything runs smoothly.

---

## 3) Install Project Tools (on the Pi)

We’ll use **Python + Flask** (a tiny web server) and **psutil** (to read system stats).

1. Open **Terminal** and run:

```bash
$ sudo apt -y install python3-pip python3-venv
$ python3 -m venv ~/pihealth
$ source ~/pihealth/bin/activate
$ pip install flask psutil
```

> **What did we just do?**\
> • `python3-venv` lets us create a **virtual environment** (`~/pihealth`)—a clean place for project packages.\
> • `source ~/pihealth/bin/activate` turns it on (your prompt will show `(pihealth)`).\
> • `Flask` lets Python answer web requests, and `psutil` reads CPU, memory, disk, and temperature data.

---

## 4) Build the Web App

We’ll make one simple version of the app now, named \`\`.

### 4A) Make a project folder

```bash
$ mkdir -p ~/pi-health-web && cd ~/pi-health-web
```

> **Why a folder?** This keeps all files for the project in one place so they’re easy to find.

---

### 4B) Write the Program: `system_monitor.py`

**Goal:** Display CPU, memory, disk, and temperature in a simple page that auto‑refreshes every 2 seconds.

1. In **Terminal** on the Pi:

```bash
$ cd ~/pi-health-web
$ nano system_monitor.py
```

2. Paste the code below. Then press **Ctrl + O**, **Enter** to save, and **Ctrl + X** to exit Nano.

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
      body{font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial; margin:16px; line-height:1.5}
      h1{margin:0 0 8px}
      .muted{color:#555}
      .card{border:1px solid #ddd; border-radius:10px; padding:12px; max-width:520px}
      .done{margin-top:12px; display:inline-block; padding:8px 10px; border:1px solid #ddd; border-radius:8px}
      .mono{font-family:ui-monospace, SFMono-Regular, Menlo, Consolas, monospace}
    </style>
  </head>
  <body>
    <h1>Raspberry Pi Health Monitor</h1>
    <div class="muted">Auto-refreshes every 2 seconds</div>
    <div class="card">
      <div><strong>CPU Usage:</strong> <span id="cpu">--</span>%</div>
      <div><strong>Memory Used:</strong> <span id="mem">--</span>%</div>
      <div><strong>Disk Used (/):</strong> <span id="disk">--</span>%</div>
      <div><strong>Temperature:</strong> <span id="temp">--</span> °C</div>
      <div class="done mono">You have successfully finished.</div>
    </div>

    <script>
      async function loadStats(){
        try{
          const r = await fetch('/api/stats');
          const s = await r.json();
          document.getElementById('cpu').textContent = Math.round(s.cpu);
          document.getElementById('mem').textContent = Math.round(s.mem_percent);
          document.getElementById('disk').textContent = Math.round(s.disk_percent);
          document.getElementById('temp').textContent = s.temp_c === null ? '--' : s.temp_c.toFixed(1);
        }catch(e){ console.error(e); }
      }
      loadStats();
      setInterval(loadStats, 2000);
    </script>
  </body>
</html>
"""


def get_temperature_c():
    """Try psutil, then vcgencmd. Return None if not available."""
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
    # host=0.0.0.0 makes the site visible to other devices on your network
    try:
        app.run(host="0.0.0.0", port=5000)
    except KeyboardInterrupt:
        # Allows clean exit when you press Ctrl+C in Terminal
        pass
```

3. **Run the server** (make sure your virtual environment is active—your prompt should start with `(pihealth)`). If not, run `source ~/pihealth/bin/activate` first.

```bash
$ cd ~/pi-health-web
$ python3 system_monitor.py
```

4. Open **Chromium** on the **Pi itself** and visit:

```
http://localhost:5000
```

You should see a simple page with the four stats updating and a success message.

> **How to stop the server:** Click the Terminal window that’s running the server, then press **Ctrl + C**. That sends a stop signal so Python exits cleanly.

---

### 4C) Learn Your Pi’s IP Address (so you can use `http://IP:5000`)

Sometimes `raspberrypi.local` doesn’t work on every device, or you might prefer to type the **IP address** directly (like `http://192.168.1.50:5000`). Here’s how to find it.

**Method 1 — From the desktop (no commands):**

1. Click the **network icon** (two arrows or Wi‑Fi symbol) on the top‑right of the Pi desktop.
2. Choose **Connection Information** (or similar).
3. Look for **IP Address**. It will look like `192.168.x.x` or `10.x.x.x`.

**Method 2 — With a quick command:**

1. Open **Terminal** on the Pi.
2. Run:

```bash
$ hostname -I
```

3. Copy the address that looks like `192.168.*.*` or `10.*.*.*`.

Now try these in a browser on the Pi **or** another device on the same network:

```
http://raspberrypi.local:5000
http://YOUR.IP.ADDRESS.HERE:5000   (example: http://192.168.1.50:5000)
```

> **What’s the difference?**\
> • `localhost` works only on the same computer that’s running the server.\
> • `raspberrypi.local` is the Pi’s **hostname** announced over the network (mDNS).\
> • The **IP address** is the numeric location of the Pi on your network. All three point to the same server on **port 5000**.

---

## What You Accomplished

- Installed Raspberry Pi OS and updated the system
- Set up a Python virtual environment and installed packages
- Wrote and ran a simple web server showing CPU, memory, disk, and temperature
- Learned how to stop and restart the server
- Accessed your page via **localhost**, **raspberrypi.local**, and the Pi’s **IP address**

