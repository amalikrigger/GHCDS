# Replit AI Chatbot Assignment (Node.js + Gemini)

## Overview

In this assignment, you will build and publish a full-stack AI chatbot using Node.js, Express, and Google’s Gemini API on Replit. The project includes creating a backend API, designing a clean chat interface, and securely managing your API key through Replit Secrets.

## Learning Goals

- Develop a backend using Node.js and Express
- Create a frontend with HTML, CSS, and JavaScript
- Integrate APIs securely with environment variables (Replit Secrets)
- Deploy a functional web application with a public URL

## Prerequisites

- A free Replit account
- Basic understanding of HTML, CSS, and JavaScript
- No local installations required; all work will be done in Replit

## 1) Create Your Replit Project

1. Go to [Replit](https://replit.com) and click **Create App**.
2. Select the **Express.js** template.
3. Name your project, for example: **ai-mental-health-chatbot**.
4. Click **Create App**. Replit will open your project with the file tree, editor, console, and webview.

## 2) Project Structure

Your project should look like this:

```
ai-chatbot/
├── index.js               # Backend server
├── package.json           # Dependencies and scripts
├── public/                # Frontend files served by Express
│   ├── index.html         # Chat UI
│   ├── style.css          # Styles
│   └── script.js          # Frontend logic
└── .env (managed by Replit Secrets)
```

## 3) Install Dependencies

In the Replit **Shell**, run:

```
npm install express cors dotenv node-fetch
```

Dependencies:

- **express**: Web server framework
- **cors**: Allows the frontend to call the backend
- **dotenv**: Loads environment variables from Replit Secrets
- **node-fetch**: Makes HTTP requests to the Gemini API

## 4) Build the Backend (index.js)

Replace the contents of **index.js** with this starter code:

```js
const express = require("express");
const cors = require("cors");

const app = express();
const PORT = process.env.PORT || 3000;

app.use(cors());
app.use(express.json());
app.use(express.static("public"));

const GEMINI_API_KEY = process.env.GEMINI_API_KEY;

const SYSTEM_INSTRUCTION_TEXT =
  "You are a compassionate mental health assistant. Respond kindly and offer practical, actionable, and brief tips or coping strategies. Keep responses concise, typically 1–3 sentences unless more detail is clearly beneficial. Avoid making diagnoses or giving medical advice. Focus on emotional support and general well-being techniques.";

let fetch;

// Chat endpoint
app.post("/api/chat", async (req, res) => {
  if (!GEMINI_API_KEY) {
    return res.status(500).json({ error: "Server API Key not configured." });
  }
  try {
    const { conversationHistory } = req.body || {};
    if (!conversationHistory) {
      return res.status(400).json({ error: "Missing conversationHistory in request body." });
    }

    const API_URL = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${GEMINI_API_KEY}`;

    const requestBody = {
      system_instruction: { parts: [{ text: SYSTEM_INSTRUCTION_TEXT }] },
      contents: conversationHistory,
    };

    const response = await fetch(API_URL, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(requestBody),
    });

    const data = await response.json();
    if (!response.ok) {
      return res.status(response.status).json({
        error: data.error?.message || "Error from Gemini API.",
      });
    }

    res.json(data);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: "Internal server error connecting to Gemini." });
  }
});

// List models endpoint
app.get("/api/models", async (req, res) => {
  if (!GEMINI_API_KEY) {
    return res.status(500).json({ error: "Server API Key not configured." });
  }
  try {
    const url = `https://generativelanguage.googleapis.com/v1beta/models?key=${GEMINI_API_KEY}`;
    const rsp = await fetch(url);
    const data = await rsp.json();
    if (!rsp.ok) {
      return res.status(rsp.status).json({ error: data.error?.message || "Error listing models." });
    }
    res.json(data);
  } catch (err) {
    console.error(err);
    res.status(500).json({ error: "Internal server error fetching models." });
  }
});

(async () => {
  try {
    const mod = await import("node-fetch");
    fetch = mod.default;
    app.listen(PORT, () => console.log(`Server listening on port ${PORT}`));
  } catch (e) {
    console.error("Failed to load node-fetch:", e);
    process.exit(1);
  }
})();
```

## 5) Build the Frontend (public/)

Create a `public/` folder with three files: **index.html**, **style.css**, and **script.js**.

**public/index.html**

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Mental Health Assistant</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="chat-container">
      <div class="header">
        <h2>Mental Health Assistant</h2>
        <p>I am here to listen and support you</p>
      </div>
      <div id="messages"></div>
      <div class="input-area">
        <input id="userInput" placeholder="How are you feeling today?" />
        <button id="sendBtn">Send</button>
      </div>
    </div>
    <script src="script.js"></script>
  </body>
</html>
```

**public/style.css**

```css
* { box-sizing: border-box; margin: 0; padding: 0; }
body { font-family: system-ui, -apple-system, Segoe UI, Roboto, Arial; background: #f4f6f8; min-height: 100vh; display: grid; place-items: center; padding: 20px; }
.chat-container { background: #fff; width: 100%; max-width: 420px; height: 600px; border-radius: 12px; box-shadow: 0 8px 28px rgba(0,0,0,.12); display: flex; flex-direction: column; overflow: hidden; }
.header { background: #283593; color: #fff; padding: 18px; text-align: center; }
#messages { flex: 1; padding: 16px; overflow-y: auto; background: #fafafa; }
.message { margin-bottom: 12px; }
.message p { display: inline-block; padding: 10px 14px; border-radius: 16px; max-width: 80%; line-height: 1.4; }
.message.user { text-align: right; }
.message.user p { background: #283593; color: #fff; margin-left: auto; }
.message.bot p { background: #e9ecef; color: #222; border: 1px solid #dee2e6; }
.message.typing p { background: #f1f3f4; color: #666; font-style: italic; }
.input-area { display: flex; border-top: 1px solid #e0e0e0; }
#userInput { flex: 1; padding: 14px; border: none; outline: none; font-size: 14px; }
#sendBtn { padding: 0 16px; margin: 8px; border: none; background: #283593; color: #fff; border-radius: 8px; cursor: pointer; }
#sendBtn:disabled { opacity: .6; cursor: not-allowed; }
```

**public/script.js**

```js
"use strict";

const CONFIG = { CHAT_API_ENDPOINT: "/api/chat" };
const ROLES = { USER: "user", MODEL: "model" };
const MESSAGE_CLASSES = { USER: "user", BOT: "bot", TYPING: "typing" };

const sendBtn = document.getElementById("sendBtn");
const userInput = document.getElementById("userInput");
const messagesContainer = document.getElementById("messages");

let conversationHistory = [];
let typingIndicator = null;

function createMessageEl(text, role, isTyping = false) {
  const wrap = document.createElement("div");
  const roleClass = role === ROLES.USER ? MESSAGE_CLASSES.USER : MESSAGE_CLASSES.BOT;
  wrap.className = `message ${roleClass}` + (isTyping ? ` ${MESSAGE_CLASSES.TYPING}` : "");
  const p = document.createElement("p");
  p.textContent = text; wrap.appendChild(p); return wrap;
}
function append(el){ messagesContainer.appendChild(el); messagesContainer.scrollTop = messagesContainer.scrollHeight; }
function showTyping(){ if(typingIndicator) typingIndicator.remove(); typingIndicator = createMessageEl("typing...", ROLES.MODEL, true); append(typingIndicator); }
function hideTyping(){ if(typingIndicator){ typingIndicator.remove(); typingIndicator = null; } }
function setDisabled(b){ sendBtn.disabled=b; userInput.disabled=b; }

function updateHistory(role, text){ conversationHistory.push({ role, parts: [{ text }] }); }

async function sendToApi(history){
  const rsp = await fetch(CONFIG.CHAT_API_ENDPOINT, { method: "POST", headers: {"Content-Type":"application/json"}, body: JSON.stringify({ conversationHistory: history }) });
  if(!rsp.ok){ const data = await rsp.json().catch(()=>({})); throw new Error(data.error || `HTTP ${rsp.status}`); }
  return rsp.json();
}
function parseGemini(data){
  return data?.candidates?.[0]?.content?.parts?.[0]?.text
      || (data?.promptFeedback?.blockReason ? `Response blocked: ${data.promptFeedback.blockReason}` : "Sorry, I could not generate a response.");
}

async function handleSend(){
  const txt = userInput.value.trim(); if(!txt) return;
  append(createMessageEl(txt, ROLES.USER)); updateHistory(ROLES.USER, txt);
  userInput.value = ""; showTyping(); setDisabled(true);
  try{
    const data = await sendToApi(conversationHistory);
    const bot = parseGemini(data); hideTyping(); append(createMessageEl(bot, ROLES.MODEL)); updateHistory(ROLES.MODEL, bot);
  }catch(err){ hideTyping(); append(createMessageEl(`Error: ${err.message}`, ROLES.MODEL)); }
  finally{ setDisabled(false); userInput.focus(); }
}

sendBtn.addEventListener("click", handleSend);
userInput.addEventListener("keypress", e => { if(e.key === "Enter" && !e.shiftKey){ e.preventDefault(); handleSend(); }});

append(createMessageEl("Hello! I am here to support you. How are you feeling today?", ROLES.MODEL));
userInput.focus();
```

---

## 6) Get Your Google AI API Key (Required)

1. Visit [Google AI Studio](https://aistudio.google.com).
2. Sign in with your Google account.
3. Click **API Keys** in the left navigation.
4. Create a new API key.
5. Copy the key and save it securely.

Add it to **Replit Secrets**:

1. In your Replit project, click the **Secrets** icon on the left.
2. Add a new secret:
   - Key: `GEMINI_API_KEY`
   - Value: paste your API key
3. Save. Do **not** hardcode keys directly into your code.

---

## 7) Integrate Gemini in Your Backend

Your `index.js` already references `process.env.GEMINI_API_KEY` and defines the `/api/chat` route. After adding your secret, click **Run**. In the console you should see: `Server listening on port 3000`.

