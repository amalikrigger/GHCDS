# 🖥️ Raspberry Pi Health Dashboard — Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

**Directions:** Answer each question to the best of your ability. This is not graded for perfection — it's to check what you learned!

---

### Multiple Choice (circle one)

**1. What does a web server do?**

A) Edits photos and videos

B) Sends web pages and data to devices that request them

C) Blocks websites from loading

D) Installs apps on your phone

---

**2. In our project, what does Flask do?**

A) Reads the Pi's CPU temperature

B) Styles the web page with colors and fonts

C) Lets Python serve web pages and respond to browser requests

D) Connects the Pi to Wi-Fi

---

**3. Which language controls how a web page LOOKS (colors, fonts, layout)?**

A) Python

B) HTML

C) CSS

D) JavaScript

---

**4. What does `document.getElementById("cpu")` do in JavaScript?**

A) Creates a new HTML element called "cpu"

B) Deletes the element with id "cpu"

C) Finds the HTML element with the id "cpu" so you can change it

D) Sends data to the Python server

---

**5. What does SSH stand for, and why is it useful?**

A) Super Simple Hosting — it makes websites load faster

B) Secure Shell — it lets you control your Pi from another computer without a monitor

C) System Status Hub — it shows your Pi's health stats

D) Safe Software Hub — it protects your Pi from viruses

---

### Short Answer

**6. Name the 3 languages that every website uses, and describe what each one does in ONE word.**

| Language | One-word description |
|---|---|
| _________________ | _________________ |
| _________________ | _________________ |
| _________________ | _________________ |

---

**7. Look at this CSS code:**

```css
background: linear-gradient(135deg, #667eea, #764ba2);
```

What does this line do? What do `#667eea` and `#764ba2` represent?

______________________________________________________________________________

______________________________________________________________________________

---

**8. In our project, the dashboard auto-updates every 2 seconds. Which language makes that happen, and what function is responsible?**

______________________________________________________________________________

---

**9. What is an API? Explain it like you're talking to a friend who has never coded before.**

______________________________________________________________________________

______________________________________________________________________________

---

**10. What is the difference between `localhost:5000` and `192.168.1.50:5000`? When would you use each one?**

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B** — Sends web pages and data to devices that request them

2. **C** — Lets Python serve web pages and respond to browser requests

3. **C** — CSS

4. **C** — Finds the HTML element with the id "cpu" so you can change it

5. **B** — Secure Shell — it lets you control your Pi from another computer without a monitor

6. HTML = Structure, CSS = Style, JavaScript = Behavior

7. It creates a gradient (smooth blend) background going from blue (`#667eea`) to purple (`#764ba2`) at a 135-degree angle. The `#` codes are hex colors — 6-character codes that define specific colors.

8. JavaScript. The `setInterval(refresh, 2000)` function calls `refresh()` every 2000 milliseconds (2 seconds), which fetches new data from the API and updates the page.

9. An API is like a waiter at a restaurant. You (the web page) place an order, the API carries it to the kitchen (the server), and the kitchen sends back the food (data). In our project, the JavaScript calls `/api/stats` and Python sends back the CPU, memory, disk, and temperature numbers.

10. `localhost:5000` only works on the Pi itself — it means "this computer, port 5000." `192.168.1.50:5000` is the Pi's IP address on the network, so ANY device on the same Wi-Fi can use it to see the dashboard. Use localhost when you're on the Pi; use the IP address when you're on a different device.
