# ⚡ Vibe Coding: Build Apps with AI

### Use AI as your coding partner — not your replacement

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 2-3 class periods &nbsp;|&nbsp; **Difficulty:** Beginner–Intermediate
>
> "Vibe coding" means describing what you want to build in plain English and letting AI help you write the code. It's how a growing number of professional developers work — and it's a skill you can start learning right now. In this project, you'll use Claude Code or GitHub Copilot to build a real project from a simple idea.

---

## 🎯 What You'll Learn

- What **vibe coding** is and why it matters in the modern tech industry
- How to use **Claude Code** (terminal) or **GitHub Copilot** (VS Code) to build projects
- How to write **effective prompts** that get better results from AI
- How to **review, understand, and debug** AI-generated code
- The difference between letting AI help you and letting AI replace you

---

## 🧰 What You Need

- **VS Code** with **GitHub Copilot** extension (if using Copilot)
- OR a terminal with **Claude Code** installed (you set this up earlier in the course)
- A project idea (we'll provide some)

---

## Part 1: What is Vibe Coding?

### The Old Way vs. The New Way

**The old way:** You think about what you want to build. You open a blank file. You type every line of code from memory or by searching Stack Overflow. You debug for hours.

**The new way (vibe coding):** You describe what you want in plain English. AI generates the code. You review it, test it, and guide the AI to improve it. You still need to understand what the code does — but you don't have to write every line from scratch.

### Why This Matters

This isn't about being lazy — it's about being efficient. Here's the reality:

- Companies are hiring developers who can use AI tools effectively
- Senior engineers at Google, Meta, and Anthropic use AI coding tools daily
- The skill isn't "can you write code from memory" — it's "can you build things that work"
- Understanding code is MORE important than ever because you need to evaluate what AI gives you

> **Think of it like this:** A calculator doesn't replace understanding math — it makes you faster. AI doesn't replace understanding code — it makes you faster. But if you can't check the calculator's answer, you'll make mistakes you don't catch.

---

## Part 2: Prompt Engineering — How to Talk to AI

The quality of what AI gives you depends entirely on how you ask. Vague prompts get vague results. Specific prompts get working code.

### Bad Prompts vs. Good Prompts

**❌ Bad:** "Make a website"
AI has no idea what kind. You'll get something generic and useless.

**✅ Good:** "Create a single-page HTML/CSS/JS website that's a personal portfolio. It should have a dark theme, a header with my name, a section listing 3 projects with titles and descriptions, and a contact section with my email. Make it responsive for mobile."

**❌ Bad:** "Fix my code"
AI doesn't know what's wrong or what you expected.

**✅ Good:** "This Python function should return the sum of all even numbers in a list, but it's returning the sum of all numbers. Here's the code: [paste code]. What's wrong and how do I fix it?"

---

### The Anatomy of a Great Prompt

A great prompt includes:

1. **What** you want to build (the end result)
2. **Tech stack** (what languages/tools to use)
3. **Details** (features, style, behavior)
4. **Constraints** (what to avoid, keep it simple, etc.)

**Template:**
```
Build a [WHAT] using [TECH STACK].
It should [FEATURES].
Make it [STYLE/CONSTRAINTS].
```

**Example:**
```
Build a countdown timer using HTML, CSS, and JavaScript.
It should let the user type in a date and show days, hours, minutes,
and seconds counting down. When it reaches zero, show a celebration
message. Make it look modern with a dark background and large numbers.
Keep it in a single HTML file.
```

---

### Prompt Techniques That Get Better Results

**Be iterative — build up, don't dump:**
```
Step 1: "Create a basic HTML page with a centered heading"
Step 2: "Now add a grid of 6 cards below the heading"
Step 3: "Style the cards with shadows and hover effects"
Step 4: "Make each card clickable — show a popup with more info"
```

This gets better results than one massive prompt because you can check each step.

**Ask AI to explain:**
```
"Explain every section of the code you just wrote. What does each part do?"
```

**Ask AI to improve:**
```
"This works but the code is messy. Refactor it to be cleaner and add comments."
```

**Ask AI to add features:**
```
"Now add a dark mode toggle button that switches between light and dark themes."
```

**Ask AI to fix specific problems:**
```
"When I click the button nothing happens. The console shows 'Uncaught TypeError: Cannot read property of null'. Here's my code: [paste]. What's wrong?"
```

---

## Part 3: Hands-On — Build Something

### Using Claude Code

If you have Claude Code installed (from earlier in the course), open your terminal:

```bash
mkdir vibe-project && cd vibe-project
claude
```

Then tell Claude what you want to build. It will create files, write code, and run commands directly on your computer.

### Using GitHub Copilot in VS Code

1. Install the **GitHub Copilot** extension in VS Code
2. Sign in with your GitHub account
3. Open a new file and start typing a comment describing what you want:

```javascript
// Create a function that takes a list of numbers
// and returns only the even ones, sorted from smallest to largest
```

Copilot will suggest code as you type. Press **Tab** to accept, or keep typing to get different suggestions.

You can also open **Copilot Chat** (sidebar) and have a conversation, similar to Claude Code.

---

### Example Project Ideas

Pick one of these or come up with your own:

**🟢 Beginner:**

| Project | Prompt to Start With |
|---|---|
| **Personal Portfolio** | "Create a single-page portfolio website with a dark theme, my name in a big header, a grid of project cards, and a contact section. HTML/CSS/JS in one file." |
| **Quiz App** | "Build a trivia quiz with 10 questions about [topic]. Show one question at a time, track score, and show results at the end. HTML/CSS/JS." |
| **Countdown Timer** | "Build a countdown timer to [date]. Show days, hours, minutes, seconds. Dark theme, big numbers. One HTML file." |
| **Random Quote Generator** | "Build a page that shows a random inspirational quote and changes when you click a button. Style it nicely. Include at least 20 quotes." |

**🟡 Intermediate:**

| Project | Prompt to Start With |
|---|---|
| **Weather Dashboard** | "Build a weather app that uses the OpenWeatherMap API to show current weather for a city the user types in. Show temperature, description, and an icon." |
| **Todo List** | "Build a to-do list app where you can add tasks, mark them complete, and delete them. Save tasks to localStorage so they persist. Clean modern design." |
| **Drawing App** | "Build a simple drawing app using HTML Canvas. Let users pick colors, brush sizes, and have a clear button. Make it work on both mouse and touch." |
| **Music Visualizer** | "Build an audio visualizer using the Web Audio API. Let users upload an MP3 and show animated bars that react to the music." |

**🔴 Advanced:**

| Project | Prompt to Start With |
|---|---|
| **Multiplayer Game** | "Build a 2-player Pong game using HTML Canvas. Arrow keys for player 1, W/S for player 2. Track scores." |
| **Markdown Editor** | "Build a split-screen markdown editor. Left side is a text area, right side shows the rendered HTML preview. Update in real-time." |
| **Expense Tracker** | "Build an expense tracker that lets you add expenses with a category, amount, and date. Show a pie chart of spending by category using Chart.js." |

---

## Part 4: The Rules of Vibe Coding

### You MUST Understand the Code

After AI generates code, you should be able to answer:
- What does this function do?
- Why is this variable here?
- What happens if I change this number?
- What would break if I removed this line?

If you can't answer these questions, you haven't learned — you've just copied. **Your teacher may ask you to walk through your code and explain it.**

### The 70/30 Rule

A good workflow is roughly:
- **70% AI-assisted** — Let AI write the boilerplate, generate layouts, handle repetitive code
- **30% you** — Review everything, make design decisions, fix bugs AI missed, customize, understand

### Always Test

AI code often has bugs. Always:
1. Run the code
2. Test edge cases (what happens with empty input? what happens with really long text?)
3. Try to break it on purpose
4. Fix what's broken (you can ask AI to help debug too)

---

## 📝 Deliverables

1. **Your finished project** — the actual working code (push to GitHub or submit as ZIP)
2. **A screenshot** of your AI conversation showing at least 5 back-and-forth messages where you guided the AI
3. **Code walkthrough** — pick 3 sections of your code and explain what each does (in your own words, not AI's explanation)
4. **Reflection** (3-5 sentences): What was the hardest part about working WITH AI? Did it do anything wrong that you had to fix? What would you build next?

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Working Project | 10 | The project runs and does what it's supposed to do |
| Prompt Quality | 5 | Your AI conversation shows thoughtful, specific prompts — not just "make me a thing" |
| Code Understanding | 5 | You can explain what your code does in your own words |
| Reflection | 5 | Honest reflection about the process, challenges, and what you learned |

**Bonus:**
- **+3 points** for building an intermediate or advanced project
- **+2 points** for going through multiple iterations with AI (improving the project over several rounds)

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Vibe Coding** | Describing what you want in plain English and using AI to help write the code |
| **Prompt** | The text instruction you give to an AI tool |
| **Prompt Engineering** | The skill of writing prompts that get better, more useful AI responses |
| **Iterate** | Building in cycles — start simple, improve, test, improve again |
| **Boilerplate** | Repetitive standard code that's the same in every project (AI is great for this) |
| **Refactor** | Rewriting code to be cleaner without changing what it does |
| **Edge Case** | An unusual input that might break your code (empty text, huge numbers, etc.) |
| **GitHub Copilot** | AI coding assistant built into VS Code that suggests code as you type |
| **Claude Code** | Anthropic's AI coding tool that runs in your terminal and can create/edit files |

---

## 💡 Troubleshooting

**"Claude Code isn't installed"**
→ Run `curl -fsSL https://claude.ai/install.sh | bash` in your terminal. You need a Pro, Max, or Team account.

**"GitHub Copilot isn't working"**
→ Make sure you're signed into GitHub in VS Code and have an active Copilot subscription (free for students with GitHub Education).

**"AI generated code but it doesn't work"**
→ That's normal! Read the error message, paste it back to AI with context: "I got this error: [error]. Here's the code: [code]. What's wrong?"

**"I don't know what to build"**
→ Pick from the project ideas table above. Start with a beginner project — you can always level up to something harder.

**"AI keeps giving me the wrong thing"**
→ Your prompt might be too vague. Add more detail: what tech stack, what features, what it should look like, what to avoid.
