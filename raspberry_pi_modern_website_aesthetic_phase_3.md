# Phase 3 — Upgrade Your Dashboard (Using Thonny)

## Overview
You will replace the simple HTML page you built in Phase 1 with a modern, styled dashboard. The backend stays the same; you only change the look. The new dashboard will fetch data from your Flask `/api/stats` endpoint and update live.

## Prerequisites
- Phase 1 app is working (Flask runs, `/api/stats` returns `{ cpu, mem_percent, disk_percent, temp_c }`).
- Virtual environment is set up at `~/pihealth/` with Flask and psutil installed.
- You know how to run `system_monitor.py`.

## Steps

### 1. Open in Thonny
- On the Raspberry Pi, launch **Thonny** (Menu → Programming → Thonny)
- In Thonny, open `~/pi-health-web/system_monitor.py`.

### 2. Find the HTML Page String
Inside your code, locate the triple-quoted string assigned to `PAGE` that holds the current HTML page.

### 3. Replace HTML Content
Remove everything between the triple quotes of that HTML string.

👉 **Paste the new HTML code here in Thonny when provided.**

### 4. Save and Run
- Save the modified file (File → Save).
- Ensure Thonny is configured to use the project interpreter (`/home/pi/pihealth/bin/python3`) under **Tools → Options → Interpreter**.
- Click **Run**. The Shell should show something like `Running on http://0.0.0.0:5000`.

### 5. View & Test
- In Chromium on the Pi: open `http://localhost:5000`
- From another device: `http://raspberrypi.local:5000` or `http://<Pi-IP>:5000`
- Verify that CPU, memory, disk, and temperature show live values and refresh every ~2 seconds.
- If temperature shows `--°C` or “Unavailable”, that’s acceptable on some hardware.

### 6. Stop the Server
- In Thonny: press the **Stop** button
- If you ran from Terminal: press **Ctrl + C**

## Deliverables
1. Screenshot of the new dashboard running in a browser.
2. Screenshot of Thonny (or Terminal) showing the server running.
3. The URL you used to access the dashboard (e.g. `localhost:5000`, `raspberrypi.local:5000`, or `192.168.x.x:5000`).

## Student Checklist
- [ ] Opened `system_monitor.py` in Thonny
- [ ] Located and removed old HTML string content
- [ ] Inserted placeholder or marker for new HTML
- [ ] Saved file and ran server successfully
- [ ] Confirmed live update of all metrics
- [ ] Viewed dashboard from correct URL
- [ ] Took and submitted required screenshots
