# 🌐 Build & Host Your Own Website on the Raspberry Pi

### Your Pi, your rules — build whatever you want

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 2-3 class periods &nbsp;|&nbsp; **Difficulty:** Beginner–Intermediate
>
> You built a guided dashboard. Now it's your turn to create something from scratch. Design your own website and host it on your Raspberry Pi — a real site that other people on your network can visit.

---

## 🎯 What You'll Learn

- How to build a website from scratch using HTML, CSS, and JavaScript
- How to research and learn new techniques on your own (a critical developer skill)
- How to host a website on a Raspberry Pi using Flask
- How to enhance your work with AI tools — after you've built the foundation yourself

---

## ⚠️ Important Rule: No AI Tools Until Approved

**You must build your first version WITHOUT using AI tools** (no ChatGPT, no Copilot, no Claude, no Gemini for code generation).

Why? Because the goal is for YOU to learn. If AI writes your code, you learn nothing. Struggling, Googling, and figuring things out is how real developers build skills.

**What you CAN use:**
- [W3Schools](https://www.w3schools.com/) — tutorials and examples
- [MDN Web Docs](https://developer.mozilla.org/) — detailed references
- YouTube tutorials
- Stack Overflow answers
- Your classmates and your teacher
- Code examples from the resources section below

**Once your website is working and approved by your teacher**, you can then use AI tools to enhance it — add animations, improve the design, add features, etc. But the foundation must be yours.

---

## 🤝 Capstone Combo Option

If you have a strong enough idea, you can **combine this project with your capstone**. For example, you could build a website that also connects to a Raspberry Pi sensor, controls a robot, or displays data from an API. Talk to your teacher about your idea — if it's ambitious enough, it counts for both assignments.

---

## 💡 What Should You Build?

Anything you want! Here are ideas, but don't limit yourself:

- A fan page for your favorite artist, game, or show
- A "link in bio" page (like Linktree) with your socials
- A personal portfolio showing off your work
- An interactive quiz or trivia game
- A countdown timer to an event
- A page about something you care about (sports, music, cars, fashion)
- A game (your classmates have built Chess, Tetris, Snake, Flappy Bird, Candy Crush, and more — check out [thinkinbits.site/projects](https://www.thinkinbits.site/projects.html) to see what's possible)

---

## Part A — Create Your Webpage

### Step 1 — Set Up Your Project Folder

Open Terminal on your Pi:

```bash
mkdir -p ~/my-webpage
cd ~/my-webpage
```

### Step 2 — Create Your Files

```bash
touch index.html styles.css script.js
mkdir -p assets
```

Your folder structure:
```
my-webpage/
├── index.html      ← your page structure
├── styles.css      ← your visual design
├── script.js       ← your interactive behavior
└── assets/         ← images and other files
```

### Step 3 — Start with This Template

Open `index.html` in Thonny, Nano, or VS Code and paste this starter:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Page</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <h1>Welcome to My Page</h1>
  <p>This is my website, hosted on a Raspberry Pi!</p>

  <!-- Add your content here -->

  <script src="script.js"></script>
</body>
</html>
```

> **This is just a starting point.** Replace everything between `<body>` and `</body>` with your own content. The only things you should keep are the `<head>` section (it sets up fonts, mobile scaling, and links your CSS/JS files).

### Step 4 — Build Your Page

Use **Cmd+F / Ctrl+F** in your editor to find and change things quickly. Here are the HTML tags you'll use most:

| Tag | What It Does | Example |
|---|---|---|
| `<h1>` to `<h6>` | Headings (h1 = biggest) | `<h1>My Site</h1>` |
| `<p>` | Paragraph of text | `<p>Welcome!</p>` |
| `<img>` | Image | `<img src="assets/photo.jpg">` |
| `<a>` | Link | `<a href="https://google.com">Click here</a>` |
| `<ul>` + `<li>` | Bullet list | `<ul><li>Item 1</li></ul>` |
| `<div>` | Container/box | `<div class="card">...</div>` |
| `<button>` | Clickable button | `<button>Click me</button>` |

> **Don't know how to do something?** Google it. Try searches like "how to center a div CSS" or "how to add a background image HTML." Check W3Schools first — they have copy-paste examples for almost everything.

---

## Part B — Set Up Your Server

### Step 1 — Create the Server File

```bash
cd ~
nano my_site.py
```

Paste this:

```python
from flask import Flask, send_from_directory

app = Flask(__name__)

WEB_DIR = "/home/pi/my-webpage"

@app.route("/")
def index():
    return send_from_directory(WEB_DIR, "index.html")

@app.route("/<path:filename>")
def serve_files(filename):
    return send_from_directory(WEB_DIR, filename)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

Save: **Ctrl + O**, Enter, **Ctrl + X**.

> **What does this do?** When someone visits your Pi's address, this Python server finds your `index.html` and sends it to their browser. The second route handles CSS, JavaScript, and image files automatically.

### Step 2 — Run It

```bash
source ~/pihealth/bin/activate
python3 my_site.py
```

Open a browser and go to `http://localhost:5000` (on the Pi) or `http://YOUR-PI-IP:5000` (from another device).

> **✅ Checkpoint:** Your webpage loads in the browser. If you used the starter template, you'll see "Welcome to My Page."

---

## Part C — Enhancement Phase (After Approval)

Once your teacher approves your first version, you can use AI tools to level it up:

- Ask AI to improve your CSS (better colors, layout, animations)
- Add interactive features with JavaScript
- Make it responsive (looks good on phone and desktop)
- Add a dark mode toggle
- Improve accessibility

> **The rule:** You must understand what the AI-generated code does. If you can't explain a section of your code, it doesn't count. Your teacher may ask you to walk through it.

---

## 📚 Helpful Resources

### Quick References
- **[W3Schools](https://www.w3schools.com/)** — Beginner-friendly, "Try It Yourself" on every example
- **[MDN Web Docs](https://developer.mozilla.org/)** — More detailed explanations

### Interactive Courses
- **[freeCodeCamp — Responsive Web Design](https://www.freecodecamp.org/learn/responsive-web-design/)** — Free, self-paced
- **[Codecademy — Learn HTML](https://www.codecademy.com/learn/learn-html)** — Interactive browser lessons

### Video Tutorials
- **[HTML & CSS Full Course — Traversy Media](https://www.youtube.com/watch?v=UB1O30fR-EE)**
- **[HTML Crash Course for Beginners](https://www.youtube.com/watch?v=FazgJVnrVuI)**

### Design Tools
- **[Coolors.co](https://coolors.co/)** — Generate color palettes
- **[Google Fonts](https://fonts.google.com/)** — Free fonts
- **[Unsplash](https://unsplash.com/)** — Free images

### Inspiration
- **[thinkinbits.site/projects](https://www.thinkinbits.site/projects.html)** — See what your classmates built last trimester

---

## 📝 Deliverables

1. The URL where your page is hosted (e.g., `http://YOUR-PI-IP:5000/`)
2. Screenshot of your webpage loaded in a browser on the Pi
3. Screenshot of your webpage loaded from a different device (phone, laptop, or Chromebook) on the GHCDS network
4. Screenshot of your project folder showing your files
5. A short reflection (3-5 sentences): What did you build? What was the hardest part? What would you add with more time?

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | Your webpage loaded in a browser on the Pi |
| 2 | Your webpage loaded from a different device (phone, laptop, or Chromebook) on the GHCDS network |
| 3 | Your project folder showing your files |
| 4 | Your written reflection (3–5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"** — do **NOT** click "Create" (Create is for text only and won't let you attach files)
4. Select your screenshot files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Hosting | 5 | Webpage loads successfully from Flask on the Pi |
| Structure | 5 | Files are organized, page uses proper HTML |
| Design | 5 | Clear layout, readable text, visual effort |
| Creativity | 5 | Shows originality — not just the starter template unchanged |
| Submission | 5 | URL, screenshots, and reflection submitted |

---

## 💡 Troubleshooting

**"My CSS isn't working"**
→ Check that `styles.css` is in the same folder as `index.html` and that your HTML has `<link rel="stylesheet" href="styles.css">` in the `<head>`.

**"My images don't show up"**
→ Make sure the image file is in your project folder. Check that the filename in your HTML matches exactly — `Photo.jpg` and `photo.jpg` are different on Linux.

**"ModuleNotFoundError: No module named 'flask'"**
→ Run `source ~/pihealth/bin/activate` first.

**"I changed my page but the browser shows the old version"**
→ Hard refresh: **Ctrl + Shift + R**.

**"Address already in use"**
→ Your dashboard server is still running on port 5000. Stop it with **Ctrl + C** in that terminal first.
