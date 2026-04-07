# 🤖 Build Your Own AI Chatbot

### Create a chatbot powered by Google's Gemini AI — then give it any personality you want

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** 4 class periods &nbsp;|&nbsp; **Difficulty:** Intermediate
>
> You'll build a working AI chatbot that runs in your browser. It uses a real AI (Google Gemini) to have conversations. By the end, you'll transform it into any kind of bot you can imagine — a study buddy, a joke machine, a career coach, or anything else.

---

## 🎯 What You'll Learn

- How **AI chatbots** actually work behind the scenes
- What an **API** is and how to use one (Google Gemini)
- How to build a **backend server** with Node.js
- How to connect a **frontend** (HTML/CSS/JS) to a backend
- How **system instructions** control an AI's personality

---

## 🧰 What You Need

- **VS Code** installed on your computer
- **Node.js** (v18 or higher) — download from [nodejs.org](https://nodejs.org)
- A **Google account** to get a free Gemini API key
- A web browser (Chrome recommended)

---

## 🔍 Pro Tip: The Find Tool

Use **Cmd+F** (Mac) or **Ctrl+F** (Windows) to search for any code you need to find or change. You'll use this a lot!

---

# Day 1: Set Up the Project + Get Your API Key

**Goal:** Create the project, install the tools, and get your AI key.

---

### Step 1 — Create the Project

Open VS Code. Open the Terminal (**View → Terminal**). Type these commands one at a time:

```bash
mkdir ai-chatbot && cd ai-chatbot
```

```bash
npm init -y
```

```bash
npm install express cors dotenv node-fetch
```

```bash
npm install --save-dev nodemon
```

> **What just happened?**
> - You created a folder called `ai-chatbot` and moved into it
> - `npm init -y` created a `package.json` file (your project's settings)
> - You installed 4 tools your project needs:
>   - **express** — runs your web server
>   - **cors** — lets your web page talk to your server
>   - **dotenv** — keeps your API key secret
>   - **node-fetch** — lets your server call the Gemini AI
> - **nodemon** — auto-restarts your server when you save changes

---

### Step 2 — Create the File Structure

Still in the terminal:

```bash
mkdir public
```

Now create these files. You can do this in the terminal OR in VS Code's file explorer (right-click → New File):

- `index.js` (in the main folder)
- `.env` (in the main folder)
- `.gitignore` (in the main folder)
- `public/index.html`
- `public/style.css`
- `public/script.js`

Your project should look like this:

```
ai-chatbot/
├── index.js
├── .env
├── .gitignore
├── package.json
└── public/
    ├── index.html
    ├── style.css
    └── script.js
```

> **✅ Checkpoint:** You should see `node_modules/` folder and `package.json` in your project. The files you just created are empty — that's fine for now.

---

### Step 3 — Set Up package.json

Open `package.json` and **replace everything** with this:

```json
{
  "name": "ai-chatbot",
  "version": "1.0.0",
  "description": "AI-powered chatbot using Google Gemini",
  "type": "module",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js --ext js,html,css,json"
  },
  "dependencies": {
    "express": "^5.1.0",
    "cors": "^2.8.5",
    "dotenv": "^16.5.0",
    "node-fetch": "^3.3.2"
  },
  "devDependencies": {
    "nodemon": "^3.1.10"
  }
}
```

> **What's important here?** The `"type": "module"` line tells Node.js to use modern JavaScript. The `"dev"` script runs your server with nodemon, which auto-restarts when you save changes — so you never have to stop and restart manually.

---

### Step 4 — Set Up .gitignore

Open `.gitignore` and paste:

```
node_modules
.env
```

> **Why?** `node_modules` is huge and can be regenerated. `.env` contains your secret API key — never share it.

---

### Step 5 — Get Your Gemini API Key

An **API key** is like a password that lets your app talk to Google's AI. Here's how to get one:

1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Sign in with your Google account
3. Click **"Get API Key"** in the left sidebar
4. Click **"Create API Key"**
5. Choose **"Create API key in new project"**
6. **Copy the key** (it looks like `AIzaSyC...`)

Now open your `.env` file and paste:

```
GEMINI_API_KEY=PASTE_YOUR_KEY_HERE
PORT=3000
```

Replace `PASTE_YOUR_KEY_HERE` with the key you just copied.

> **⚠️ Important:** Treat this key like a password. Never share it, screenshot it, or put it on GitHub.

> **✅ Checkpoint:** Your `.env` file has your API key in it, and `.gitignore` contains `.env`.

---

### 📝 Day 1 Deliverables

1. Screenshot of your VS Code showing the project file structure
2. Confirmation that your `.env` file has the API key (don't screenshot the key itself!)

---

# Day 2: Build the Server + Frontend

**Goal:** Write the backend server, build the chat interface, and see your chatbot work.

---

### Step 1 — Build the Backend Server

Open `index.js` and paste this entire file:

```javascript
import express from "express";
import cors from "cors";
import dotenv from "dotenv";
import fetch from "node-fetch";

dotenv.config();

const app = express();
const PORT = process.env.PORT || 3000;
const GEMINI_API_KEY = process.env.GEMINI_API_KEY;

app.use(cors());
app.use(express.json());
app.use(express.static("public"));

// This is the AI's personality — change this to change how it behaves!
const SYSTEM_INSTRUCTION_TEXT =
  "You are a compassionate and supportive assistant. Respond kindly and offer practical, brief tips. Keep responses concise, typically 1-3 sentences. If a user mentions wanting to harm themselves or others, encourage them to talk to a trusted adult, counselor, or call emergency services.";

// This handles messages from the chat
app.post("/api/chat", async (req, res) => {
  if (!GEMINI_API_KEY) {
    return res.status(500).json({ error: "API Key not configured. Check your .env file." });
  }

  try {
    const { conversationHistory } = req.body || {};

    if (!conversationHistory || !Array.isArray(conversationHistory)) {
      return res.status(400).json({ error: "Missing conversationHistory in request." });
    }

    const API_URL = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent?key=${GEMINI_API_KEY}`;

    const payload = {
      system_instruction: { parts: [{ text: SYSTEM_INSTRUCTION_TEXT }] },
      contents: conversationHistory,
    };

    const rsp = await fetch(API_URL, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(payload),
    });

    const data = await rsp.json();

    if (!rsp.ok) {
      return res.status(rsp.status).json({ error: data.error?.message || "Error from Gemini API." });
    }

    return res.json(data);
  } catch (err) {
    console.error("Error:", err);
    return res.status(500).json({ error: "Server error connecting to Gemini." });
  }
});

app.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
  console.log(`API Key configured: ${GEMINI_API_KEY ? "Yes" : "No"}`);
});
```

> **What just happened?** You built a web server that does three things:
> 1. Serves your web page files (from the `public/` folder)
> 2. Receives messages from the chat interface
> 3. Sends them to Google's Gemini AI and returns the response
>
> The `SYSTEM_INSTRUCTION_TEXT` is the most important line — it tells the AI how to behave. We'll change this on Day 4 to create completely different chatbots!

---

### Step 2 — Build the HTML

Open `public/index.html` and paste:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>AI Chatbot</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="chat-container">
      <div class="header">
        <h2>AI Chatbot</h2>
        <p>Ask me anything — I'm here to help.</p>
      </div>

      <div id="messages"></div>

      <div class="disclaimer">
        <strong>Note:</strong> This is an AI chatbot for educational purposes.
        It is not a substitute for professional advice. If you need real help,
        talk to a trusted adult or counselor.
      </div>

      <div class="input-area">
        <input id="userInput" type="text" placeholder="Type a message..." />
        <button id="sendBtn">Send</button>
      </div>
    </div>
    <script src="script.js"></script>
  </body>
</html>
```

---

### Step 3 — Build the CSS

Open `public/style.css` and paste:

```css
* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: Arial, Helvetica, sans-serif;
  background: #f4f6f8;
  min-height: 100vh;
  display: grid;
  place-items: center;
  padding: 20px;
}

.chat-container {
  background: #fff;
  width: 100%;
  max-width: 480px;
  height: 640px;
  border-radius: 12px;
  box-shadow: 0 8px 28px rgba(0,0,0,0.12);
  display: flex;
  flex-direction: column;
  overflow: hidden;
}

.header {
  background: #283593;
  color: #fff;
  padding: 18px;
  text-align: center;
}

.header h2 { font-size: 1.25rem; margin-bottom: 4px; }
.header p { font-size: 0.85rem; opacity: 0.9; }

#messages {
  flex: 1;
  padding: 16px;
  overflow-y: auto;
  background: #fafafa;
}

.message { margin-bottom: 12px; display: flow-root; }

.message p {
  display: inline-block;
  padding: 10px 14px;
  border-radius: 16px;
  max-width: 80%;
  line-height: 1.4;
  word-wrap: break-word;
}

.message.user { text-align: right; }
.message.user p {
  background: #283593;
  color: #fff;
  margin-left: auto;
  border-radius: 16px 16px 4px 16px;
}

.message.bot p {
  background: #e9ecef;
  color: #222;
  border-radius: 16px 16px 16px 4px;
}

.message.typing p {
  background: #f1f3f4;
  color: #666;
  font-style: italic;
}

.disclaimer {
  background: #fff8e1;
  color: #5d4037;
  border-top: 1px solid #ffe082;
  padding: 8px 12px;
  font-size: 12px;
  line-height: 1.4;
}

.input-area {
  display: flex;
  border-top: 1px solid #e0e0e0;
}

#userInput {
  flex: 1;
  padding: 14px;
  border: none;
  outline: none;
  font-size: 14px;
}

#sendBtn {
  padding: 0 16px;
  margin: 8px;
  border: none;
  background: #283593;
  color: #fff;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
}

#sendBtn:hover { background: #1a237e; }
#sendBtn:disabled { opacity: 0.6; cursor: not-allowed; }
```

---

### Step 4 — Build the JavaScript

Open `public/script.js` and paste:

```javascript
"use strict";

const sendBtn = document.getElementById("sendBtn");
const userInput = document.getElementById("userInput");
const messagesContainer = document.getElementById("messages");

let conversationHistory = [];
let typingIndicator = null;

// Create a chat bubble
function createMessage(text, role, isTyping = false) {
  const wrap = document.createElement("div");
  const cssClass = role === "user" ? "user" : "bot";
  wrap.className = "message " + cssClass + (isTyping ? " typing" : "");

  const p = document.createElement("p");
  p.textContent = text;
  wrap.appendChild(p);
  return wrap;
}

// Add a message to the chat and scroll down
function addToChat(el) {
  messagesContainer.appendChild(el);
  messagesContainer.scrollTop = messagesContainer.scrollHeight;
}

// Show "typing..." while waiting for AI
function showTyping() {
  if (typingIndicator) typingIndicator.remove();
  typingIndicator = createMessage("typing...", "model", true);
  addToChat(typingIndicator);
}

function hideTyping() {
  if (typingIndicator) { typingIndicator.remove(); typingIndicator = null; }
}

// Lock/unlock the input while waiting
function setDisabled(disabled) {
  sendBtn.disabled = disabled;
  userInput.disabled = disabled;
}

// Send the conversation to our server
async function sendToApi(history) {
  const rsp = await fetch("/api/chat", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ conversationHistory: history }),
  });

  if (!rsp.ok) {
    const data = await rsp.json().catch(() => ({}));
    throw new Error(data.error || "Something went wrong");
  }

  return rsp.json();
}

// Pull the AI's text out of the response
function getResponseText(data) {
  const text = data?.candidates?.[0]?.content?.parts?.[0]?.text;
  if (text) return text;
  if (data?.promptFeedback?.blockReason) return "Response was blocked by safety filters.";
  return "Sorry, I couldn't generate a response.";
}

// Handle sending a message
async function handleSend() {
  const text = userInput.value.trim();
  if (!text) return;

  // Show user's message
  addToChat(createMessage(text, "user"));
  conversationHistory.push({ role: "user", parts: [{ text }] });
  userInput.value = "";

  // Show typing and wait for AI
  showTyping();
  setDisabled(true);

  try {
    const data = await sendToApi(conversationHistory);
    const botText = getResponseText(data);

    hideTyping();
    addToChat(createMessage(botText, "model"));
    conversationHistory.push({ role: "model", parts: [{ text: botText }] });
  } catch (err) {
    hideTyping();
    addToChat(createMessage("Error: " + err.message, "model"));
  } finally {
    setDisabled(false);
    userInput.focus();
  }
}

// Event listeners
sendBtn.addEventListener("click", handleSend);
userInput.addEventListener("keypress", (e) => {
  if (e.key === "Enter") handleSend();
});

// Welcome message
addToChat(createMessage("Hello! How can I help you today?", "model"));
userInput.focus();
```

---

### Step 5 — Run It!

In the terminal, make sure you're in the `ai-chatbot` folder, then:

```bash
npm run dev
```

You should see:

```
Server running at http://localhost:3000
API Key configured: Yes
```

Open your browser and go to **http://localhost:3000**

Type a message and hit Send!

> **✅ Checkpoint:** Your chatbot responds to messages. You should see your message on the right (blue) and the AI's response on the left (gray). A "typing..." indicator appears while the AI is thinking.

---

### 🧠 Mini Lesson — How This All Connects

Here's what happens every time you send a message:

```
1. You type "I'm stressed about homework" and click Send
2. JavaScript catches your message and shows it in the chat
3. JavaScript sends the message to YOUR server (localhost:3000)
4. Your server adds the system instructions and sends everything to Google Gemini
5. Gemini generates a helpful response
6. Your server sends it back to the web page
7. JavaScript shows the AI's response in the chat
```

**Why not call Gemini directly from the browser?** Because your API key would be visible to anyone who opens the page source. By going through your own server, the key stays hidden in the `.env` file.

**What are system instructions?** They're the rules you give the AI before the conversation starts. They control the AI's personality, tone, and behavior. The AI follows them for every response but the user never sees them.

---

### 📝 Day 2 Deliverables

1. Screenshot of your chatbot running with at least 3 messages exchanged
2. The browser URL bar should show `http://localhost:3000`

---

# Day 3: Understand the Code

**Goal:** Understand how each part of your chatbot works so you can customize it on Day 4.

---

### The Backend (index.js) — Key Parts

**Imports and setup:**
```javascript
import express from "express";  // Web server framework
import dotenv from "dotenv";    // Loads your .env file
dotenv.config();                // Now process.env.GEMINI_API_KEY works
```

These lines load the tools and your secret API key.

**The system instructions:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a compassionate and supportive assistant...";
```

This is the AI's "personality." Change this text and the entire chatbot changes. Tomorrow you'll rewrite this to create a completely different bot.

**The chat endpoint:**
```javascript
app.post("/api/chat", async (req, res) => { ... });
```

`app.post` means "when someone sends data to `/api/chat`, run this code." The `async` keyword means it can wait for the AI to respond without freezing everything else.

**Calling Gemini:**
```javascript
const rsp = await fetch(API_URL, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(payload),
});
```

This sends the conversation to Google's AI. `await` means "wait for the response before continuing." The `payload` includes both the system instructions and the full conversation history, so the AI has context for every message.

---

### The Frontend (script.js) — Key Parts

**Conversation history:**
```javascript
let conversationHistory = [];
```

Every message (from both the user and the AI) gets saved here. This is sent with every new message so the AI remembers what you talked about earlier. Without it, every message would be like starting a brand new conversation.

**The send flow:**
```javascript
async function handleSend() {
  // 1. Get the user's text
  // 2. Show it in the chat
  // 3. Add it to history
  // 4. Show "typing..."
  // 5. Call the API
  // 6. Show the AI's response
  // 7. Add response to history
}
```

**Error handling with try/catch:**
```javascript
try {
  // Try to get a response from the AI
} catch (err) {
  // If something goes wrong, show an error message
} finally {
  // Always re-enable the input, no matter what happened
}
```

The `finally` block is important — it makes sure the Send button gets re-enabled even if there's an error. Without it, one error would permanently freeze the chat.

---

### The CSS — Key Parts

**Chat bubble tails:**
```css
.message.user p {
  border-radius: 16px 16px 4px 16px;  /* Flat bottom-right corner */
}
.message.bot p {
  border-radius: 16px 16px 16px 4px;  /* Flat bottom-left corner */
}
```

This gives the bubbles that "tail" effect you see in iMessage or WhatsApp.

**Flexbox layout:**
```css
.chat-container {
  display: flex;
  flex-direction: column;
}
#messages {
  flex: 1;  /* Takes up all remaining space */
}
```

`flex: 1` on the messages area means it stretches to fill whatever space is left after the header, disclaimer, and input area.

---

### 📝 Day 3 Deliverables

1. In your own words: What do "system instructions" do, and why are they important?
2. In your own words: Why does the chatbot send messages to YOUR server instead of directly to Google?

---

# Day 4: Transform Your Chatbot

**Goal:** Change the system instructions to create a completely different chatbot. Make it yours.

---

### Step 1 — Pick a Personality

The magic of your chatbot is the `SYSTEM_INSTRUCTION_TEXT` in `index.js`. Change that one string and you have a totally different bot. Here are ideas:

**Study Buddy:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a helpful study assistant. Help students with study techniques, time management, and understanding concepts. Break down complex topics into simple explanations. Keep responses clear, encouraging, and 1-3 sentences.";
```

**Career Coach:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an enthusiastic career counselor helping students explore career paths. Ask about their interests and strengths. Suggest careers, required education, and first steps. Keep responses encouraging, 2-3 sentences.";
```

**Creative Writing Coach:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an inspiring creative writing coach. Help writers develop ideas, overcome writer's block, and improve their craft. Ask thought-provoking questions. Keep responses brief but impactful.";
```

**Coding Mentor:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a patient coding mentor helping beginners learn programming. Break down concepts into simple terms. Ask guiding questions rather than giving direct answers. Keep responses clear and encouraging.";
```

**Dad Joke Generator:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a dad joke expert. Every response must include at least one terrible pun or dad joke related to whatever the user said. Be cheerful and groan-worthy. Keep responses short and punny.";
```

**Fitness Coach:**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an energetic fitness coach. Provide encouragement, simple exercise ideas, and wellness tips. Keep responses upbeat and actionable. Emphasize progress over perfection. 1-3 sentences.";
```

Or **invent your own** — a travel planner, movie recommender, debate partner, rhyming poet, historical figure roleplay, recipe helper... anything!

---

### Step 2 — Update the UI to Match

After changing the system instructions, update these three things:

**In `public/index.html`** — change the header:
```html
<div class="header">
  <h2>Study Buddy</h2>
  <p>Let's ace those exams together!</p>
</div>
```

**In `public/index.html`** — change the placeholder:
```html
<input id="userInput" type="text" placeholder="What are you studying?" />
```

**In `public/script.js`** — change the welcome message (last few lines):
```javascript
addToChat(createMessage("Hey! What subject are you working on today?", "model"));
```

---

### Step 3 — (Optional) Change the Colors

In `public/style.css`, use **Cmd+F / Ctrl+F** to find `#283593` (the dark blue color) and replace it with something that fits your theme:

| Theme | Color | Code |
|---|---|---|
| Study Buddy | Blue | `#1976d2` |
| Career Coach | Teal | `#00897b` |
| Creative Writing | Purple | `#7b1fa2` |
| Fitness Coach | Green | `#2e7d32` |
| Dad Jokes | Orange | `#e65100` |

---

### Step 4 — Test and Screenshot

Save all your files. The server should auto-restart (nodemon). Refresh the browser and test your new chatbot with a real conversation.

> **✅ Checkpoint:** Your chatbot has a new personality, updated header, and responds differently than the default version.

---

### 📝 Day 4 Deliverables

1. Screenshot of your **transformed chatbot** with at least 3 messages
2. What personality did you choose and why?
3. Paste the system instruction text you wrote
4. A short reflection (3-5 sentences): What was the most interesting thing you learned? How do system instructions change the AI's behavior?

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | **Day 1:** Screenshot of your VS Code project structure (file tree showing your project files) |
| 2 | **Day 2:** Screenshot of your chatbot running at localhost:3000 with at least 3 back-and-forth messages visible |
| 3 | **Day 3:** Your written answers to critical thinking questions |
| 4 | **Day 4:** Screenshot of your transformed chatbot running with at least 3 messages showing the new personality |
| 5 | Your personality choice and system instruction text |
| 6 | Your written reflection (3–5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"** — do **NOT** click "Create" (Create is for text only and won't let you attach files)
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## �📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Project Setup | 5 | Files created, API key configured, server runs |
| Working Chatbot | 5 | Messages send and receive, AI responds appropriately |
| Code Understanding | 5 | Can explain system instructions and why we use a server |
| Creative Transformation | 5 | Changed personality, updated UI, tested with real conversation |
| Deliverables | 5 | All screenshots and reflections submitted |

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **API** | Application Programming Interface — a way for programs to talk to each other |
| **API Key** | A secret code that gives your app permission to use a service |
| **Backend / Server** | Code that runs on the computer serving the website (not in the browser) |
| **Frontend / Client** | Code that runs in the user's browser (HTML, CSS, JS) |
| **Node.js** | A tool that lets you run JavaScript outside the browser |
| **Express** | A framework that makes it easy to build web servers with Node.js |
| **npm** | Node Package Manager — installs and manages code libraries |
| **Environment Variable** | A secret value stored outside your code (like in `.env`) |
| **System Instructions** | Rules given to an AI before a conversation that control its behavior |
| **Async / Await** | A way to write code that waits for something (like an AI response) without freezing |
| **fetch()** | A function that sends requests to a server and gets responses |
| **JSON** | A text format for sending data between programs |
| **Endpoint** | A specific URL that a server listens on (like `/api/chat`) |

---

## 💡 Troubleshooting

**"API Key not configured" in the terminal**
→ Check your `.env` file. Make sure it says `GEMINI_API_KEY=your_actual_key` with no spaces around the `=`.

**Page loads but nothing happens when you send a message**
→ Open browser DevTools (F12), click Console tab, and look for red errors. Usually a typo in `script.js`.

**"Cannot find module" error**
→ Run `npm install` again in the terminal.

**"Port 3000 already in use"**
→ Another server is running. Close other terminal windows or change the port in `.env` to `PORT=3001`.

**AI gives weird or no response**
→ Check that your API key is valid at [aistudio.google.com](https://aistudio.google.com). You may have hit the free tier limit (60 requests/minute).

**Changes don't show up**
→ Make sure you saved all files. Hard refresh the browser with **Ctrl+Shift+R** (or Cmd+Shift+R on Mac).
