# 🌐 Phase 4: Build & Host Your Own Webpage on the Raspberry Pi

### Your Pi, your rules — build whatever you want

> **Time:** 2 class periods &nbsp;|&nbsp; **Difficulty:** Beginner–Intermediate
>
> In the last few days, you built someone else’s dashboard. Now it’s your turn to create something from scratch. You’ll design your own webpage and host it on your Pi — a real website that other people on your network can visit.

---

## 🎯 Objective

Create your own custom webpage using any editor or IDE of your choice, then host it using your Raspberry Pi’s Flask server. This phase gives you creative freedom to design anything from a portfolio or fan page to a fun experiment. The key requirement is that your page must be hosted and viewable on your Pi.

---

## 💡 Why This Matters

You’re moving from following guided code to **creating your own project**. That’s a huge step — it’s the difference between following a recipe and cooking your own meal.

Every website you visit — Instagram, YouTube, Google — started as someone’s idea that they turned into HTML, CSS, and JavaScript. That’s exactly what you’re about to do.

This will give you hands-on experience with HTML, CSS, and JavaScript, while learning how to serve and host static files from your own server.

**Not sure what to build? Here are some ideas:**
- A fan page for your favorite artist, game, or show
- A "link in bio" page (like Linktree) with your socials
- A personal portfolio showing off your work
- A quiz or interactive page
- A countdown timer to an event
- A page about something you’re passionate about (sports, music, cars, fashion, etc.)

---

## Part A — Create Your Webpage

### Step 1 — Set Up Your Project Folder

First, let's create a home for your webpage files. Open Terminal and run:

```bash
mkdir -p ~/my-webpage
```

> **What does this do?** It creates a new folder called `my-webpage` in your home directory. The `-p` flag means "don't give me an error if it already exists."

---

### Step 2 — Create Your HTML File

Move into your new folder and create the main file:

```bash
cd ~/my-webpage
nano index.html
```

> **Why `index.html`?** Every website has a file called `index.html` — it's the "front door." When someone visits your site, the server automatically looks for this file first. It's a web convention, like how every book has a cover page.

Here's a **starter template** you can paste in to get going. You don't have to use this — it's just a starting point if you're not sure where to begin:

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

Save with **Ctrl + O**, **Enter**, then exit with **Ctrl + X**.

> **🤔 What are those `<meta>` tags?** They give the browser info about your page. `charset="UTF-8"` lets you use emojis and special characters. The `viewport` one makes your page look right on phones. You don't need to memorize these — just include them at the top.

---

### Step 3 — (Optional) Add CSS and JavaScript Files

If you want to keep your code organized (like the pros do), create separate files for styling and interactivity:

```bash
touch styles.css script.js
```

> **What does `touch` do?** It creates empty files. Now you can write your CSS in `styles.css` and your JavaScript in `script.js`, and they'll automatically connect to your HTML because of the `<link>` and `<script>` tags in the template above.

You can also create a folder for images:

```bash
mkdir -p assets
```

Put any images you want to use in the `assets/` folder, then reference them in your HTML like this:

```html
<img src="assets/my-photo.jpg" alt="Description of image">
```

---

### Step 4 — Choose Your Editor

Use whatever editor feels most comfortable:

| Editor | Best For | How to Open |
|---|---|---|
| **[Thonny](https://thonny.org/)** | Already on your Pi, simple to use | Menu → Programming → Thonny |
| **Nano** | Quick edits in the Terminal | `nano filename.html` |
| **[VS Code](https://code.visualstudio.com/)** | More features, great for bigger projects | Install from website or `sudo apt install code` |
| **Online editors** | Working from another computer | [Replit](https://replit.com/), [CodeSandbox](https://codesandbox.io/), [CodePen](https://codepen.io/) |

> **💡 Tip:** If you use an online editor to design your page, you'll still need to copy the files onto your Pi to host them. The easiest way is to copy-paste the code into Nano or Thonny on the Pi.

---

## Part B — Set Up Your Server

> **🔄 Quick Reminder:** In the dashboard project, your Python file had the HTML built right into it. This time, your HTML is in a separate file — so the Python server just needs to know where to find it and serve it up. This is actually how most real websites work.

### Step 1 — Create the Server File

Open Terminal and run:

```bash
cd ~
nano my_site.py
```

Paste the following code:

```python
from flask import Flask, send_from_directory

app = Flask(__name__)

WEB_DIR = "/home/pi/my-webpage"  # Path to your webpage folder

@app.route("/")
def index():
    return send_from_directory(WEB_DIR, "index.html")

@app.route("/<path:filename>")
def serve_files(filename):
    return send_from_directory(WEB_DIR, filename)

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

Save: **Ctrl + O**, **Enter**. Exit: **Ctrl + X**.

> **What does this code do?** Let’s break it down:
> - `WEB_DIR` tells Python where your webpage files live
> - The first `@app.route("/")` says: "When someone visits the homepage, send them `index.html`"
> - The second `@app.route("/<path:filename>")` says: "When someone requests any other file (like `styles.css` or an image), find it in the same folder and send it"
> - `host="0.0.0.0"` means "let anyone on the network visit, not just this computer"
> - `port=5000` is like a door number — your website lives at door 5000

---

### Step 2 — Activate Your Virtual Environment and Start the Server

Remember the virtual environment from the dashboard project? You need to activate it first:

```bash
source ~/pihealth/bin/activate
cd ~
python3 my_site.py
```

> **⚠️ Common Mistake:** If you get `ModuleNotFoundError: No module named ‘flask’`, you forgot to activate the virtual environment. Run the `source` command above first.

---

### Step 3 — View Your Site

Open a browser and go to one of these:

| Where You Are | URL to Use |
|---|---|
| On the Pi itself | `http://localhost:5000` |
| On another device (same Wi-Fi) | `http://YOUR-PI-IP-ADDRESS:5000` |

> **💡 Forgot your Pi’s IP?** Run `hostname -I` in Terminal to find it.

> **✅ Checkpoint:** You should see your webpage loaded in the browser. If you used the starter template, you’ll see "Welcome to My Page" in big text.

---

## Part C — Make It Yours

Now comes the fun part — actually designing your page. Here are features you can add, from easiest to most advanced:

### 🟢 Easy (just HTML)
- A header with your name or page title
- Paragraphs about yourself or your topic
- A list of your favorite things (`<ul>` and `<li>` tags)
- Links to other websites (`<a href="...">`)
- Images (`<img src="...">`)

### 🟡 Medium (HTML + CSS)
- A hero section with a big image and caption
- Cards or sections for content (e.g., About, Gallery, Contact)
- Custom colors, fonts, and spacing
- Responsive design (looks good on phone and laptop)

### 🔴 Advanced (HTML + CSS + JavaScript)
- A button that does something when clicked
- A dark mode toggle
- A quiz or interactive game
- Animations or transitions
- A live clock or countdown timer

> **💡 Don't know how to do something?** That's totally normal — and it's exactly how real developers work. Here's what to do:
> 1. Google it! Try searches like "how to add an image in HTML" or "how to make a button change color CSS"
> 2. Check the resources section below — W3Schools has copy-paste examples for almost everything
> 3. Ask your teacher or a classmate
>
> Professional developers Google things *constantly*. It's not cheating — it's the job.

---

## 📚 Helpful Resources

Don't try to memorize everything — use these as references when you need them. Bookmark the ones you find useful.

### 🔤 Quick References (look things up fast)
- **[W3Schools](https://www.w3schools.com/)** — Beginner-friendly tutorials with a "Try It Yourself" button on every example. Great for HTML, CSS, and JavaScript.
- **[MDN Web Docs](https://developer.mozilla.org/)** — More detailed explanations from Mozilla (the people who make Firefox). Good when you want to understand *why* something works.

### 🎓 Interactive Courses (learn step-by-step)
- **[freeCodeCamp — Responsive Web Design](https://www.freecodecamp.org/learn/responsive-web-design/)** — Free, self-paced course that teaches HTML and CSS from scratch
- **[Codecademy — Learn HTML](https://www.codecademy.com/learn/learn-html)** — Interactive lessons where you write code in your browser

### 🎥 Video Tutorials (watch and follow along)
- **[HTML & CSS Full Course for Beginners — Traversy Media](https://www.youtube.com/watch?v=UB1O30fR-EE)** — Clear, well-paced walkthrough
- **[HTML Crash Course for Absolute Beginners](https://www.youtube.com/watch?v=FazgJVnrVuI)** — Quick intro if you just need the basics

### 🎨 Design Inspiration & Tools
- **[Coolors.co](https://coolors.co/)** — Generate beautiful color palettes for your site
- **[Google Fonts](https://fonts.google.com/)** — Free fonts you can add to your page
- **[Unsplash](https://unsplash.com/)** — Free high-quality images you can use

---

## 📝 Deliverables

1. The URL where your page is hosted (e.g., `http://YOUR-PI-IP:5000/`)
2. At least two screenshots:
   - Your webpage running in a browser
   - Your project folder showing `index.html` and other files
3. A short reflection (3–5 sentences): What did you build? What was fun? What would you add if you had more time?

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I’m Looking For |
|---|---|---|
| Hosting | 5 | Webpage loads successfully from Flask on the Pi |
| Structure | 5 | Files are organized, page uses proper HTML tags |
| Design | 5 | Clear layout, readable text, some attention to visuals |
| Creativity | 5 | Shows effort and originality — not just the starter template unchanged |
| Submission | 5 | Correct URL, screenshots, and reflection included |

---

## 💡 Troubleshooting

**"My page shows up blank"**
→ Make sure your `index.html` has actual content between the `<body>` tags. Open the file and check.

**"My CSS isn’t working"**
→ Check three things: (1) Is your `styles.css` file in the same folder as `index.html`? (2) Does your HTML have `<link rel="stylesheet" href="styles.css">` in the `<head>`? (3) Did you save both files?

**"My images don’t show up"**
→ Make sure the image file is in your `~/my-webpage/` folder (or `~/my-webpage/assets/`). Check that the filename in your HTML matches *exactly* — including capitalization. `Photo.jpg` and `photo.jpg` are different files on Linux.

**"I changed my page but the browser still shows the old version"**
→ Hard-refresh with **Ctrl + Shift + R**. Browsers cache (save) old versions of pages to load faster.

**"ModuleNotFoundError: No module named ‘flask’"**
→ You need to activate the virtual environment first: `source ~/pihealth/bin/activate`

**"Address already in use"**
→ Your dashboard server (or another instance) is already running on port 5000. Stop it with **Ctrl + C** in that Terminal window first.

**"I want to start over"**
→ No problem! Run `rm ~/my-webpage/index.html` and then `nano ~/my-webpage/index.html` to create a fresh file. Your server file (`my_site.py`) doesn’t need to change.

---

## 💪 Tips for Success

- **Save before you refresh.** Always save your files (Ctrl+S in Thonny, Ctrl+O in Nano) before refreshing the browser.
- **Make small changes.** Change one thing, save, refresh, see what happened. Don’t change 20 things at once — you won’t know what broke.
- **Use your browser’s developer tools.** Right-click on your page and choose "Inspect" to see what’s going on under the hood. This is what professional developers use every day.
- **Restart Flask after changing Python routes.** If you only changed HTML/CSS/JS, you just need to refresh the browser. But if you changed `my_site.py`, you need to stop (Ctrl+C) and restart the server.
- **It’s okay to borrow ideas.** Look at websites you like and try to figure out how they did something. View their source code (Ctrl+U in most browsers). That’s how most developers learned.

