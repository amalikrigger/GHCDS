<!-- ===========================================================================
TEACHER NOTE, never renders on the site.

Exit ticket for raspberry_pi_dashboard.md. Rewritten 2026-09-16 alongside the
lesson rewrite. The old version asked about a gradient and a PAGE variable that
no longer exist in the lesson.

- 10 points, 1 per question. Separate Schoology item from the 25-point
  assignment, matching the Digital Safety precedent.
- Same paper for both sections. Q9 and Q10 are the ones that separate students
  who understood the system from students who followed the steps.
- Give it at the end of Day 3, 10 minutes, closed laptop.
- Q5 is the question worth reading aloud if half the class misses it. Every
  student who cannot get their dashboard onto a phone next time has missed Q5.
=========================================================================== -->

# 🖥️ Raspberry Pi Web Server, Exit Ticket

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

**10 points, 1 per question.** Closed laptop. If you are stuck, write what you do know. A half right answer beats a blank.

---

### Multiple Choice (circle one)

**1. What is a server's actual job?**

A) To store photos and videos

B) To wait for requests and send back responses

C) To connect a computer to Wi-Fi

D) To make web pages look good

---

**2. In your project, what does Flask do?**

A) Reads the Pi's CPU temperature

B) Styles the page with colors and fonts

C) Lets Python answer requests from a browser

D) Copies files between computers

---

**3. Which one controls how the page LOOKS?**

A) Python

B) HTML

C) CSS

D) JavaScript

---

**4. Your `server.py` has this line. What does it do?**

```python
@app.route("/api/stats")
```

A) Creates a folder called `api`

B) Says which request the function under it answers

C) Sends the stats to a website on the internet

D) Installs the psutil library

---

**5. Your dashboard works in Chromium on the Pi but your friend's phone gets nothing. Which line is the one that decides whether other devices can reach it?**

A) `setInterval(refresh, 2000);`

B) `app.run(host="0.0.0.0", port=5000)`

C) `import psutil`

D) `<title>Pi Health</title>`

---

**6. What does SSH let you do?**

A) Make a website load faster

B) Type commands on one computer that run on a different computer

C) Protect the Pi from viruses

D) Show the Pi's health stats

---

### Short Answer

**7. Name the three languages every web page uses, and describe each in ONE word.**

| Language | One word |
|---|---|
| _________________ | _________________ |
| _________________ | _________________ |
| _________________ | _________________ |

---

**8. You visited `/api/stats` in a browser and saw this:**

```json
{"cpu":12.5,"disk":31.2,"memory":24.8,"temperature":47.1}
```

What is this format called, and why does the page get numbers like this instead of a normal web page?

______________________________________________________________________________

______________________________________________________________________________

---

**9. Explain the difference between `localhost:5000` and `10.0.4.71:5000`. When would you use each one?**

______________________________________________________________________________

______________________________________________________________________________

---

**10. Your project is two files: `server.py` and `static/index.html`. Say what each one is responsible for, and name one thing you would have to change in BOTH files to add a new stat to your dashboard.**

______________________________________________________________________________

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

**1. B.** Wait for requests and send back responses. Anything mentioning "wait" and "send back" gets the point.

**2. C.** Lets Python answer requests from a browser.

**3. C.** CSS.

**4. B.** It says which request the function under it answers. "It's the address" or "it decides what happens when you go to /api/stats" both get the point.

**5. B.** `app.run(host="0.0.0.0", port=5000)`. The `0.0.0.0` is what makes the server answer devices other than itself.

**6. B.** Type commands on one computer that run on a different computer.

**7.** HTML = structure, CSS = style, JavaScript = behavior. Accept skeleton / looks / actions and anything clearly equivalent.

**8.** It is **JSON**. The page asks `/api/stats` for *data*, not for a page. JavaScript already built the page once and now only needs fresh numbers to drop into it, so sending the whole page again every two seconds would be wasted work. Full credit for naming JSON plus any version of "the page only needs the numbers."

**9.** `localhost:5000` means "this computer, port 5000," so it only works while you are sitting at the Pi. `10.0.4.71:5000` is the Pi's address on the network, so any device on GHCDS can use it. Use localhost when you are on the Pi, the IP when you are on anything else.

**10.** `server.py` is the server: it measures the stats and hands out the files. `static/index.html` is the page: it displays things and asks for the numbers.

To add a new stat you would change **both**:
- in `server.py`, add the new value to what `/api/stats` sends back
- in `index.html`, add a card to show it, and add it to the `CARDS` list in the JavaScript

Full credit needs one specific change in each file. A student who says "add it to the Python" and "add it to the HTML" without saying what has the right idea and gets the point.

**Common wrong answer worth a minute of class time:** students who say you only have to change the HTML. Ask them where the number would come from.
