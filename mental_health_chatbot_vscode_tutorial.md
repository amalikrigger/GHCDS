# Mental Health Chatbot — Comprehensive VS Code Tutorial

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites & Setup](#prerequisites)
3. [Project Architecture Overview](#architecture)
4. [Step 1: Project Initialization](#step-1)
5. [Step 2: API Key Configuration](#step-2)
6. [Step 3: Package Configuration](#step-3)
7. [Step 4: Backend Development](#step-4)
8. [Step 5: Frontend Development](#step-5)
9. [Step 6: Running & Testing](#step-6)
10. [📸 Submission Requirements](#submission-requirements)
11. [Troubleshooting](#troubleshooting)
12. [Next Steps & Extensions](#next-steps)
13. [🎨 Creative Challenge: Transform Your Chatbot!](#creative-challenge-transform-your-chatbot)

---

## Introduction

### What You'll Build

In this comprehensive tutorial, you'll create a **full-stack Mental Health Chatbot** that provides compassionate, AI-powered emotional support to users. This project demonstrates real-world application development skills including:

- **Backend API development** using Node.js and Express
- **Frontend web development** with vanilla HTML, CSS, and JavaScript
- **AI integration** using Google's Gemini API
- **Asynchronous programming** and API communication
- **Responsible AI practices** for sensitive applications

### Why This Project Matters

Mental health support is increasingly important, especially for students. While this chatbot **is not a substitute for professional help**, it demonstrates how technology can provide accessible, judgment-free emotional support. You'll learn to build ethically responsible AI applications that prioritize user safety.

### Learning Objectives

By completing this tutorial, you will:

- Understand client-server architecture and RESTful API design
- Learn to integrate third-party AI services securely
- Practice environment variable management for API keys
- Build responsive, user-friendly interfaces
- Implement proper error handling and user feedback
- Apply ethical considerations in AI development

### Project Architecture

```
User Browser (Frontend)
    ↓
HTML/CSS/JS Interface
    ↓
Express.js Server (Backend)
    ↓
Google Gemini API (AI)
```

The application follows a **three-tier architecture**: the frontend handles user interaction, the backend manages API requests and security, and the AI service generates responses.

---

## <a name="prerequisites"></a>0. Prerequisites & Environment Setup

### Required Software

Before starting, ensure you have:

1. **Node.js (v18 or higher)** — Node.js is the JavaScript runtime that allows us to run JavaScript on the server side
   - Download from [nodejs.org](https://nodejs.org)
   - Verify installation: `node --version` and `npm --version`
   - **Why LTS?** Long-Term Support versions receive security updates and are stable for production

2. **Visual Studio Code** — A powerful, free code editor with excellent Node.js support
   - Download from [code.visualstudio.com](https://code.visualstudio.com)
   - **Recommended Extensions:**
     - ESLint (code quality)
     - Prettier (code formatting)
     - REST Client (API testing)

3. **Google Account** — Required to obtain a Gemini API key
   - Visit [aistudio.google.com](https://aistudio.google.com)
   - The API is free with generous usage limits

### Required Knowledge

This tutorial assumes basic familiarity with:

- Command-line/terminal operations
- JavaScript fundamentals (variables, functions, async/await)
- HTML/CSS basics
- HTTP concepts (requests, responses, status codes)

**Don't worry if you're not an expert** — we'll explain concepts as we go!

### Setting Up Your Development Environment

1. **Create a dedicated workspace folder** for your projects (e.g., `~/Development/`)
2. **Open VS Code** and familiarize yourself with the integrated terminal (`View → Terminal`)
3. **Test your Node installation** by running `node -v` in the terminal

---

## <a name="architecture"></a>Project Architecture Overview

### Understanding the Components

Before diving into code, let's understand how the pieces fit together:

#### 1. **Backend (Node.js + Express)**
- **Purpose:** Acts as a secure intermediary between your frontend and the Gemini API
- **Why not call Gemini directly from the browser?** 
  - Security: Your API key would be exposed to anyone viewing the page source
  - CORS: Browser security policies restrict direct third-party API calls
  - Control: The backend can validate, log, and modify requests

#### 2. **Frontend (HTML/CSS/JavaScript)**
- **Purpose:** Provides the user interface and manages conversation state
- **Design Philosophy:** Clean, accessible, and mobile-responsive
- **State Management:** Maintains conversation history for context-aware responses

#### 3. **Gemini API (AI Service)**
- **Purpose:** Generates intelligent, context-aware responses
- **Model:** We'll use `gemini-2.5-flash` for fast, high-quality responses
- **System Instructions:** Guide the AI to provide appropriate emotional support

### Data Flow Example

Here's what happens when a user sends a message:

```
1. User types "I'm feeling anxious about exams"
2. Frontend captures input and displays it
3. Frontend sends conversation history to backend via POST /api/chat
4. Backend adds system instructions and forwards to Gemini API
5. Gemini generates supportive response
6. Backend receives response and sends to frontend
7. Frontend displays AI response to user
8. Conversation history updated for context in next message
```

### File Structure Preview

```
ai-mental-health-chatbot/
├── index.js              # Backend server (Express + API logic)
├── package.json          # Project dependencies and scripts
├── .env                  # Environment variables (API key)
├── .gitignore            # Files to exclude from version control
└── public/               # Static frontend files
    ├── index.html        # Page structure
    ├── style.css         # Visual design
    └── script.js         # User interaction logic
```

**Why this structure?** It separates concerns: backend logic, configuration, and frontend code are independent, making the project easier to maintain and scale.

---

## <a name="step-1"></a>1. Project Initialization

### Understanding npm and Dependencies

**npm** (Node Package Manager) is Node.js's package manager. It:
- Manages project dependencies (third-party code libraries)
- Runs scripts (like starting your server)
- Tracks package versions in `package.json`

### Step-by-Step Setup

Open your terminal and execute these commands:

```bash
# Create project directory and navigate into it
mkdir ai-mental-health-chatbot && cd ai-mental-health-chatbot

# Initialize a new Node.js project with default settings
# The -y flag automatically answers "yes" to all prompts
npm init -y

# Install production dependencies
npm install express cors dotenv node-fetch

# Install development dependencies
npm install --save-dev nodemon
```

### Understanding Each Dependency

Let's break down **why** we need each package:

#### Production Dependencies (`dependencies`)

1. **express** (`^5.1.0`)
   - **What:** Minimalist web framework for Node.js
   - **Why:** Simplifies routing, middleware, and HTTP server creation
   - **Alternative:** We could use Node's built-in `http` module, but Express provides better abstractions

2. **cors** (`^2.8.5`)
   - **What:** Cross-Origin Resource Sharing middleware
   - **Why:** Allows our frontend (served from the browser) to communicate with our backend
   - **Without it:** Browser security would block API requests

3. **dotenv** (`^16.5.0`)
   - **What:** Loads environment variables from `.env` file
   - **Why:** Keeps sensitive data (API keys) out of source code
   - **Security:** Never commit `.env` to version control!

4. **node-fetch** (`^3.3.2`)
   - **What:** Browser-style `fetch()` API for Node.js
   - **Why:** Makes HTTP requests to Gemini API elegantly
   - **Note:** Node 18+ has built-in `fetch`, but node-fetch provides consistency

#### Development Dependencies (`devDependencies`)

1. **nodemon** (`^3.1.10`)
   - **What:** Monitors file changes and auto-restarts the server
   - **Why:** Dramatically improves development experience — no manual restarts!
   - **Usage:** Only for development, not production

### Version Numbers Explained

Notice the `^` symbol in version numbers (e.g., `^5.1.0`):

- `5.1.0` = major.minor.patch
- `^5.1.0` = accept compatible updates (5.1.x, 5.2.x, but NOT 6.0.0)
- **Why?** Allows security patches while preventing breaking changes

### Creating the Project Structure

Now create the folder structure:

```bash
# Create public directory for frontend files
mkdir public

# Create empty files (use 'touch' on macOS/Linux, 'type nul >' on Windows)
touch index.js .env .gitignore
touch public/index.html public/style.css public/script.js
```

**Tip:** In VS Code, you can also create files using the Explorer sidebar.

### Setting Up .gitignore

Create `.gitignore` with this content:

```gitignore
# Dependencies
node_modules

# Environment variables (contains sensitive API keys)
.env

# OS files
.DS_Store
Thumbs.db

# Editor directories
.vscode
.idea

# Logs
*.log
npm-debug.log*
```

**Why `.gitignore`?** 
- `node_modules/` is huge (often 100+ MB) and can be regenerated with `npm install`
- `.env` contains secrets that should **never** be shared publicly
- Prevents accidental exposure of sensitive information on GitHub

### Checkpoint ✓

At this point, you should have:
- A project directory with the proper structure
- All dependencies installed (check `node_modules/` folder exists)
- Empty files ready for code

Run `ls -la` (or `dir` on Windows) to verify your structure matches the diagram above.

---

## <a name="step-2"></a>2. Obtaining & Configuring Your Gemini API Key

### Understanding API Keys

An **API key** is like a password that:
- Identifies your application to Google's servers
- Tracks your usage for billing/rate limiting
- Provides access to Gemini's AI capabilities

**Security Warning:** Treat API keys like passwords! Never:
- Commit them to Git/GitHub
- Share them in screenshots or videos
- Hardcode them in source files
- Send them in client-side code

### Obtaining Your API Key

1. **Visit Google AI Studio**
   - Navigate to [aistudio.google.com](https://aistudio.google.com)
   - Sign in with your Google account

2. **Navigate to API Keys**
   - Click "Get API Key" in the left sidebar
   - Click "Create API Key"
   - Choose "Create API key in new project" (or use existing project)

3. **Copy Your Key**
   - Your key will look like: `AIzaSyC...` (40 characters)
   - Click the copy icon
   - **Store it securely** — you'll need it next

### Understanding API Quotas

The Gemini API free tier includes:
- **60 requests per minute**
- **1,500 requests per day**
- Sufficient for development and small-scale testing

For production apps with more users, consider upgrading to a paid plan.

### Creating the .env File

Create a `.env` file in your project root with:

```env
GEMINI_API_KEY=YOUR_ACTUAL_KEY_HERE
PORT=3000
```

**Replace `YOUR_ACTUAL_KEY_HERE`** with your copied API key.

### Understanding Environment Variables

**Environment variables** are configuration values stored outside your code:

- **Development:** Loaded from `.env` file (convenient for local testing)
- **Production:** Set in your hosting platform (Heroku, AWS, etc.)
- **Benefits:** Same code works in different environments without modification

**How dotenv works:**
```javascript
// Before dotenv.config()
process.env.GEMINI_API_KEY // undefined

// After dotenv.config()
process.env.GEMINI_API_KEY // "AIzaSyC..."
```

### Security Best Practices

1. **Never commit `.env`** — Verify it's in `.gitignore`
2. **Use different keys** for development and production
3. **Rotate keys** if accidentally exposed (revoke and create new)
4. **Set key restrictions** in Google Cloud Console:
   - IP address restrictions
   - API restrictions (only Gemini API)

### Checkpoint ✓

Verify your setup:
1. `.env` exists in project root
2. Contains your actual API key
3. `.gitignore` includes `.env`
4. Running `git status` (if initialized) doesn't show `.env`

---

## <a name="step-3"></a>3. Configuring package.json

### Understanding package.json

Your `package.json` file is the **manifest** for your Node.js project. It defines:

- **Metadata:** Project name, version, description
- **Dependencies:** Required packages
- **Scripts:** Commands to run your application
- **Configuration:** How Node.js should execute your code

### Complete package.json

Replace your `package.json` contents with:

```json
{
  "name": "ai-mental-health-chatbot",
  "version": "1.0.0",
  "description": "A compassionate AI-powered mental health support chatbot",
  "type": "module",
  "main": "index.js",
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js --ext js,html,css,json"
  },
  "keywords": ["mental-health", "chatbot", "ai", "gemini"],
  "author": "Your Name",
  "license": "MIT",
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

### Key Configuration Explained

#### `"type": "module"`

This critical setting enables **ES Modules** (ESM) syntax:

```javascript
// ES Modules (modern, recommended)
import express from 'express';
export default function() { }

// CommonJS (older style)
const express = require('express');
module.exports = function() { }
```

**Why ESM?**
- Aligns with modern JavaScript standards
- Better tree-shaking (smaller bundles)
- Native browser compatibility
- Required for node-fetch v3

#### Scripts Section

Scripts are shortcuts for terminal commands:

**1. `npm start`** — Production mode
```bash
node index.js
```
- Runs your server normally
- Use in production environments
- No auto-restart on file changes

**2. `npm run dev`** — Development mode
```bash
nodemon index.js --ext js,html,css,json
```
- Uses nodemon for auto-restart
- `--ext` flag specifies which file types to watch
- Restarts server when you save changes
- **Use this during development!**

### Understanding Nodemon

**Without nodemon:**
```
1. Edit index.js
2. Ctrl+C to stop server
3. Run 'node index.js' again
4. Test changes
5. Repeat...
```

**With nodemon:**
```
1. Run 'npm run dev' once
2. Edit files
3. Save — nodemon auto-restarts!
4. Test immediately
```

The `--ext` flag tells nodemon to watch:
- `js` — Server-side JavaScript
- `html` — Frontend markup
- `css` — Styles
- `json` — Config files

### Checkpoint ✓

Verify your configuration:
```bash
# View your package.json
cat package.json

# Test that scripts are defined
npm run
# Should list 'start' and 'dev' scripts
```

---

## <a name="step-4"></a>4. Backend Development (index.js)

### Backend Architecture Overview

Our Express server will:
1. **Serve static files** (HTML, CSS, JS) from the `public/` directory
2. **Provide API endpoints** for the frontend to communicate with
3. **Proxy requests** to Gemini API securely
4. **Handle errors** gracefully

### Complete Backend Code

Create `index.js` with the following code:

```javascript
// index.js
// =========================================================================
// Mental Health Chatbot Backend
// Express.js server that proxies requests to Google Gemini API
// =========================================================================

import express from "express";
import cors from "cors";
import dotenv from "dotenv";
import fetch from "node-fetch";

// Load environment variables from .env file into process.env
dotenv.config();

// Initialize Express application
const app = express();

// Configuration from environment variables
const PORT = process.env.PORT || 3000;
const GEMINI_API_KEY = process.env.GEMINI_API_KEY;

// =========================================================================
// MIDDLEWARE CONFIGURATION
// =========================================================================

// CORS: Enable Cross-Origin Resource Sharing
// Allows frontend (running in browser) to make requests to this server
app.use(cors());

// Body Parser: Parse incoming JSON request bodies
// Enables req.body to contain parsed JSON data
app.use(express.json());

// Static File Server: Serve files from 'public' directory
// Automatically serves index.html, style.css, script.js
app.use(express.static("public"));

// =========================================================================
// AI SYSTEM INSTRUCTIONS
// =========================================================================

/**
 * System instructions guide the AI's behavior and responses.
 * 
 * Key principles:
 * 1. Non-clinical: No diagnoses or medical advice
 * 2. Supportive: Empathetic and validating
 * 3. Actionable: Provide practical coping strategies
 * 4. Concise: Brief responses (1-3 sentences typically)
 * 5. Safety-focused: Encourage professional help for crisis situations
 */
const SYSTEM_INSTRUCTION_TEXT =
  "You are a compassionate mental health assistant. Respond kindly and offer practical, actionable, and brief tips or coping strategies. Keep responses concise, typically 1–3 sentences unless more detail is clearly beneficial. Avoid making diagnoses or giving medical advice. Focus on emotional support and general well-being techniques. If a user mentions intent to harm themselves or others, encourage them to seek immediate help from a trusted adult, counselor, or emergency services.";

// =========================================================================
// API ENDPOINTS
// =========================================================================

/**
 * POST /api/chat
 * Main chat endpoint - sends conversation to Gemini and returns response
 * 
 * Request body:
 * {
 *   conversationHistory: [
 *     { role: "user", parts: [{ text: "Hello" }] },
 *     { role: "model", parts: [{ text: "Hi there!" }] }
 *   ]
 * }
 * 
 * Response:
 * - Success: Gemini API response with generated content
 * - Failure: { error: "Error message" }
 */
app.post("/api/chat", async (req, res) => {
  // Validate API key configuration
  if (!GEMINI_API_KEY) {
    return res.status(500).json({ 
      error: "Server API Key not configured. Check your .env file." 
    });
  }

  try {
    // Extract conversation history from request
    const { conversationHistory } = req.body || {};

    // Validate request body
    if (!conversationHistory || !Array.isArray(conversationHistory)) {
      return res.status(400).json({ 
        error: "Missing conversationHistory (array) in request body." 
      });
    }

    // Construct Gemini API endpoint
    // Using gemini-2.5-flash for fast, high-quality responses
    const API_URL = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent?key=${GEMINI_API_KEY}`;

    // Prepare request payload
    // system_instruction: Guides AI behavior
    // contents: Conversation history for context
    const payload = {
      system_instruction: { 
        parts: [{ text: SYSTEM_INSTRUCTION_TEXT }] 
      },
      contents: conversationHistory,
    };

    // Make request to Gemini API
    const rsp = await fetch(API_URL, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(payload),
    });

    // Parse response
    const data = await rsp.json();

    // Handle API errors
    if (!rsp.ok) {
      return res.status(rsp.status).json({ 
        error: data.error?.message || "Error from Gemini API." 
      });
    }

    // Return successful response
    return res.json(data);

  } catch (err) {
    // Log error for debugging
    console.error("Error in /api/chat:", err);
    
    // Return generic error to client
    return res.status(500).json({ 
      error: "Internal server error connecting to Gemini." 
    });
  }
});

/**
 * GET /api/models
 * Optional endpoint to list available Gemini models
 * Useful for debugging and exploring API capabilities
 */
app.get("/api/models", async (_req, res) => {
  if (!GEMINI_API_KEY) {
    return res.status(500).json({ 
      error: "Server API Key not configured." 
    });
  }

  try {
    const url = `https://generativelanguage.googleapis.com/v1beta/models?key=${GEMINI_API_KEY}`;
    const rsp = await fetch(url);
    const data = await rsp.json();

    if (!rsp.ok) {
      return res.status(rsp.status).json({ 
        error: data.error?.message || "Error listing models." 
      });
    }

    return res.json(data);
  } catch (e) {
    console.error("Error in /api/models:", e);
    return res.status(500).json({ 
      error: "Internal server error fetching models." 
    });
  }
});

// =========================================================================
// SERVER STARTUP
// =========================================================================

app.listen(PORT, () => {
  console.log(`✓ Server listening on http://localhost:${PORT}`);
  console.log(`✓ API Key configured: ${GEMINI_API_KEY ? 'Yes' : 'No'}`);
  console.log(`\nPress Ctrl+C to stop the server.`);
});
```

### Deep Dive: Key Concepts

#### 1. **Middleware in Express**

Middleware are functions that process requests **before** they reach your route handlers:

```javascript
app.use(cors());          // 1st: Enable cross-origin requests
app.use(express.json());  // 2nd: Parse JSON bodies
app.use(express.static("public")); // 3rd: Serve static files
```

**Execution order matters!** Middleware runs in the order defined.

#### 2. **Why Proxy Through Our Server?**

We could call Gemini directly from the browser, but:

❌ **Client-side (Bad):**
```javascript
// API key exposed in browser!
fetch(`https://gemini.com/api?key=${API_KEY}`)
```

✅ **Server-side (Good):**
```javascript
// Key stays secure on server
app.post("/api/chat", async (req, res) => {
  // Server makes request with hidden key
});
```

#### 3. **Async/Await Pattern**

Modern JavaScript handles asynchronous operations with async/await:

```javascript
// Old way (callbacks)
fetch(url, (error, response) => {
  if (error) { /* handle */ }
  else { /* use response */ }
});

// Modern way (async/await)
try {
  const response = await fetch(url);
  // use response
} catch (error) {
  // handle error
}
```

**Why better?** Reads like synchronous code, easier to understand and debug.

#### 4. **Error Handling Strategy**

Our error handling has multiple layers:

```javascript
// 1. Validate inputs
if (!conversationHistory) {
  return res.status(400).json({ error: "..." });
}

// 2. Catch exceptions
try {
  await fetch(API_URL);
} catch (err) {
  return res.status(500).json({ error: "..." });
}

// 3. Check API response
if (!rsp.ok) {
  return res.status(rsp.status).json({ error: "..." });
}
```

**Result:** Users always get meaningful error messages, never crashes.

#### 5. **System Instructions**

The `SYSTEM_INSTRUCTION_TEXT` is crucial for responsible AI:

- **Without:** Generic ChatGPT-style responses
- **With:** Specialized mental health support focused on safety

**Example difference:**

**Without system instructions:**
```
User: "I feel depressed"
AI: "That sounds difficult. Have you considered therapy?"
```

**With system instructions:**
```
User: "I feel depressed"
AI: "I'm sorry you're feeling this way. Try going for a short walk or talking to someone you trust. If these feelings persist, please reach out to a counselor or mental health professional."
```

### Testing the Backend

Before moving to the frontend, let's test the server:

```bash
# Start the development server
npm run dev
```

You should see:
```
✓ Server listening on http://localhost:3000
✓ API Key configured: Yes

Press Ctrl+C to stop the server.
```

**Test in browser:** Navigate to `http://localhost:3000` — you should see a blank page (we haven't added HTML yet).

**Test the API** (optional, using curl):
```bash
curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"conversationHistory":[{"role":"user","parts":[{"text":"Hello"}]}]}'
```

### Checkpoint ✓

- Server starts without errors
- Port 3000 is accessible
- API key is loaded (check console output)
- No syntax errors or crashes

---

## <a name="step-5"></a>5. Frontend Development

Now let's build the user interface! The frontend consists of three files working together:

- **HTML** — Structure and content
- **CSS** — Visual design and layout
- **JavaScript** — Interactive behavior

### public/index.html — Structure

Create `public/index.html`:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <!-- Responsive viewport for mobile devices -->
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Mental Health Assistant</title>
    
    <!-- Link to external stylesheet -->
    <link rel="stylesheet" href="style.css" />
  </head>
  
  <body>
    <!-- Main container for chat interface -->
    <div class="chat-container">
      
      <!-- Header section with title and subtitle -->
      <div class="header">
        <h2>Mental Health Assistant</h2>
        <p>I'm here to listen and support you.</p>
      </div>

      <!-- Messages area - dynamically populated by JavaScript -->
      <div id="messages"></div>

      <!-- Legal disclaimer for user safety -->
      <div class="disclaimer">
        <strong>Disclaimer:</strong> This chatbot provides general emotional support and coping ideas only.
        It is not medical advice. If you feel unsafe or in crisis, contact a trusted adult, school counselor,
        or local emergency services immediately.
      </div>

      <!-- Input area for user messages -->
      <div class="input-area">
        <input 
          id="userInput" 
          type="text"
          placeholder="How are you feeling today?" 
          aria-label="Message input"
        />
        <button id="sendBtn" aria-label="Send message">Send</button>
      </div>
    </div>
    
    <!-- Load JavaScript last for performance -->
    <script src="script.js"></script>
  </body>
</html>
```

#### HTML Structure Explained

**1. Semantic Structure**
```html
<div class="chat-container">  <!-- Main wrapper -->
  <div class="header">        <!-- Title area -->
  <div id="messages">         <!-- Scrollable chat -->
  <div class="disclaimer">    <!-- Legal notice -->
  <div class="input-area">    <!-- User input -->
</div>
```

**2. Accessibility Features**
- `lang="en"` — Assists screen readers
- `aria-label` — Provides context for assistive technologies
- Semantic HTML — Clear document outline

**3. Mobile Responsiveness**
```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```
This ensures proper scaling on mobile devices.

### public/style.css — Visual Design

Create `public/style.css`:

```css
/* =========================================================================
   MENTAL HEALTH CHATBOT STYLES
   Modern, accessible, mobile-responsive design
   ========================================================================= */

/* -------------------------------------------------------------------------
   RESET & BASE STYLES
   ------------------------------------------------------------------------- */

* { 
  box-sizing: border-box;  /* Include padding/border in width calculations */
  margin: 0; 
  padding: 0; 
}

body {
  /* Modern system font stack for cross-platform consistency */
  font-family: system-ui, -apple-system, 'Segoe UI', Roboto, Arial, sans-serif;
  
  /* Subtle background color */
  background: #f4f6f8;
  
  /* Full viewport height */
  min-height: 100vh;
  
  /* Center the chat container */
  display: grid;
  place-items: center;
  
  /* Padding for mobile devices */
  padding: 20px;
}

/* -------------------------------------------------------------------------
   CHAT CONTAINER
   ------------------------------------------------------------------------- */

.chat-container {
  background: #fff;
  
  /* Responsive width: full on mobile, capped on desktop */
  width: 100%;
  max-width: 480px;
  
  /* Fixed height with internal scrolling */
  height: 640px;
  
  /* Modern rounded corners */
  border-radius: 12px;
  
  /* Subtle shadow for depth */
  box-shadow: 0 8px 28px rgba(0, 0, 0, 0.12);
  
  /* Flexbox for vertical layout */
  display: flex;
  flex-direction: column;
  
  /* Prevent content overflow */
  overflow: hidden;
}

/* -------------------------------------------------------------------------
   HEADER
   ------------------------------------------------------------------------- */

.header { 
  background: #283593;  /* Material Design Indigo 800 */
  color: #fff;
  padding: 18px;
  text-align: center;
}

.header h2 {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 4px;
}

.header p {
  font-size: 0.875rem;
  opacity: 0.9;
}

/* -------------------------------------------------------------------------
   MESSAGES AREA
   ------------------------------------------------------------------------- */

#messages { 
  /* Take remaining vertical space */
  flex: 1;
  
  padding: 16px;
  
  /* Enable scrolling for long conversations */
  overflow-y: auto;
  
  /* Subtle background differentiation */
  background: #fafafa;
}

/* Individual message wrapper */
.message { 
  margin-bottom: 12px;
  
  /* Clearfix for floated content */
  display: flow-root;
}

/* Message bubble (both user and bot) */
.message p {
  display: inline-block;
  padding: 10px 14px;
  border-radius: 16px;
  max-width: 80%;  /* Prevent overly wide bubbles */
  line-height: 1.4;
  word-wrap: break-word;  /* Handle long words */
}

/* User messages (right-aligned, blue) */
.message.user { 
  text-align: right; 
}

.message.user p { 
  background: #283593;
  color: #fff;
  margin-left: auto;
  border-radius: 16px 16px 4px 16px;  /* Tail effect */
}

/* Bot messages (left-aligned, gray) */
.message.bot p { 
  background: #e9ecef;
  color: #222;
  border: 1px solid #dee2e6;
  border-radius: 16px 16px 16px 4px;  /* Tail effect */
}

/* Typing indicator (animated dots could be added) */
.message.typing p { 
  background: #f1f3f4;
  color: #666;
  font-style: italic;
}

/* -------------------------------------------------------------------------
   DISCLAIMER
   ------------------------------------------------------------------------- */

.disclaimer {
  background: #fff8e1;  /* Light yellow */
  color: #5d4037;       /* Brown text for readability */
  border-top: 1px solid #ffe082;
  padding: 8px 12px;
  font-size: 12px;
  line-height: 1.4;
}

/* -------------------------------------------------------------------------
   INPUT AREA
   ------------------------------------------------------------------------- */

.input-area { 
  display: flex;
  border-top: 1px solid #e0e0e0;
}

#userInput { 
  /* Take remaining horizontal space */
  flex: 1;
  
  padding: 14px;
  border: none;
  outline: none;
  font-size: 14px;
  font-family: inherit;  /* Match body font */
}

#userInput::placeholder {
  color: #999;
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
  transition: background 0.2s ease;
}

#sendBtn:hover {
  background: #1a237e;  /* Darker on hover */
}

#sendBtn:disabled { 
  opacity: 0.6;
  cursor: not-allowed;
}

/* -------------------------------------------------------------------------
   RESPONSIVE ADJUSTMENTS
   ------------------------------------------------------------------------- */

@media (max-width: 600px) {
  .chat-container {
    height: calc(100vh - 40px);  /* Full height minus padding */
    max-width: 100%;
  }
  
  .message p {
    max-width: 85%;  /* Slightly wider on mobile */
  }
}
```

#### CSS Design Principles

**1. Mobile-First Responsive Design**
```css
width: 100%;           /* Full width on mobile */
max-width: 480px;      /* Capped on desktop */
```

**2. Flexbox Layout**
```css
display: flex;
flex-direction: column;
```
This creates a flexible vertical layout where the messages area grows to fill available space.

**3. Accessibility Considerations**
- High contrast ratios (WCAG AA compliant)
- Clear focus states for keyboard navigation
- Readable font sizes (14px minimum)

**4. Visual Hierarchy**
- Bold header draws attention
- Message bubbles clearly differentiated
- Disclaimer visually distinct (yellow background)

### public/script.js — Interactive Behavior

Create `public/script.js`:

```javascript
// =========================================================================
// MENTAL HEALTH CHATBOT - FRONTEND LOGIC
// Handles user interaction, API communication, and conversation management
// =========================================================================

"use strict";  // Enforce stricter JavaScript parsing

// -------------------------------------------------------------------------
// CONFIGURATION & CONSTANTS
// -------------------------------------------------------------------------

const CONFIG = {
  CHAT_API_ENDPOINT: "/api/chat"
};

// Role constants for conversation history (matches Gemini API format)
const ROLES = {
  USER: "user",
  MODEL: "model"
};

// CSS class constants for message styling
const MESSAGE_CLASSES = {
  USER: "user",
  BOT: "bot",
  TYPING: "typing"
};

// -------------------------------------------------------------------------
// DOM ELEMENT REFERENCES
// -------------------------------------------------------------------------

const sendBtn = document.getElementById("sendBtn");
const userInput = document.getElementById("userInput");
const messagesContainer = document.getElementById("messages");

// -------------------------------------------------------------------------
// APPLICATION STATE
// -------------------------------------------------------------------------

/**
 * Conversation history in Gemini API format:
 * [
 *   { role: "user", parts: [{ text: "Hello" }] },
 *   { role: "model", parts: [{ text: "Hi there!" }] }
 * ]
 */
let conversationHistory = [];

/**
 * Reference to typing indicator DOM element
 * Allows us to remove it when response arrives
 */
let typingIndicator = null;

// -------------------------------------------------------------------------
// HELPER FUNCTIONS
// -------------------------------------------------------------------------

/**
 * Creates a message element to display in the chat
 * 
 * @param {string} text - Message content
 * @param {string} role - "user" or "model"
 * @param {boolean} isTyping - Whether this is a typing indicator
 * @returns {HTMLElement} Message element ready to append
 */
function createMessageEl(text, role, isTyping = false) {
  // Create wrapper div
  const wrap = document.createElement("div");
  
  // Determine CSS class based on role
  const roleClass = role === ROLES.USER 
    ? MESSAGE_CLASSES.USER 
    : MESSAGE_CLASSES.BOT;
  
  // Apply classes
  wrap.className = `message ${roleClass}` + 
    (isTyping ? ` ${MESSAGE_CLASSES.TYPING}` : "");
  
  // Create paragraph for message text
  const p = document.createElement("p");
  p.textContent = text;
  
  wrap.appendChild(p);
  return wrap;
}

/**
 * Appends element to messages container and scrolls to bottom
 * Ensures newest messages are always visible
 * 
 * @param {HTMLElement} el - Element to append
 */
function append(el) {
  messagesContainer.appendChild(el);
  
  // Scroll to bottom (smooth scrolling can be added with CSS)
  messagesContainer.scrollTop = messagesContainer.scrollHeight;
}

/**
 * Shows "typing..." indicator to provide user feedback
 */
function showTyping() {
  // Remove previous indicator if exists
  if (typingIndicator) typingIndicator.remove();
  
  // Create new typing indicator
  typingIndicator = createMessageEl("typing...", ROLES.MODEL, true);
  append(typingIndicator);
}

/**
 * Removes typing indicator when response is ready
 */
function hideTyping() {
  if (typingIndicator) { 
    typingIndicator.remove(); 
    typingIndicator = null; 
  }
}

/**
 * Enables/disables input controls during API requests
 * Prevents users from sending multiple messages simultaneously
 * 
 * @param {boolean} disabled - Whether controls should be disabled
 */
function setDisabled(disabled) { 
  sendBtn.disabled = disabled;
  userInput.disabled = disabled;
}

/**
 * Adds a message to conversation history
 * Maintains context for AI responses
 * 
 * @param {string} role - "user" or "model"
 * @param {string} text - Message content
 */
function updateHistory(role, text) { 
  conversationHistory.push({ 
    role, 
    parts: [{ text }] 
  }); 
}

// -------------------------------------------------------------------------
// API COMMUNICATION
// -------------------------------------------------------------------------

/**
 * Sends conversation history to backend API
 * 
 * @param {Array} history - Conversation history array
 * @returns {Promise<Object>} API response data
 * @throws {Error} If request fails or returns non-OK status
 */
async function sendToApi(history) {
  const rsp = await fetch(CONFIG.CHAT_API_ENDPOINT, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ conversationHistory: history }),
  });
  
  // Check for HTTP errors
  if (!rsp.ok) {
    // Try to parse error message from response
    const data = await rsp.json().catch(() => ({}));
    throw new Error(data.error || `HTTP ${rsp.status}`);
  }
  
  return rsp.json();
}

/**
 * Extracts text from Gemini API response
 * Handles various response formats and error cases
 * 
 * @param {Object} data - API response object
 * @returns {string} Extracted message text
 */
function parseGemini(data) {
  // Try to extract first candidate text
  const responseText = data?.candidates?.[0]?.content?.parts?.[0]?.text;
  
  if (responseText) {
    return responseText;
  }
  
  // Check if response was blocked by safety filters
  if (data?.promptFeedback?.blockReason) {
    return `Response blocked: ${data.promptFeedback.blockReason}`;
  }
  
  // Fallback for unexpected response format
  return "Sorry, I couldn't generate a response.";
}

// -------------------------------------------------------------------------
// MAIN MESSAGE HANDLER
// -------------------------------------------------------------------------

/**
 * Handles the entire message sending flow:
 * 1. Validates input
 * 2. Displays user message
 * 3. Updates conversation history
 * 4. Shows typing indicator
 * 5. Sends to API
 * 6. Displays bot response
 * 7. Handles errors gracefully
 */
async function handleSend() {
  // Get and trim user input
  const txt = userInput.value.trim();
  
  // Ignore empty messages
  if (!txt) return;

  // 1. Display user message
  append(createMessageEl(txt, ROLES.USER));
  
  // 2. Add to conversation history
  updateHistory(ROLES.USER, txt);
  
  // 3. Clear input field
  userInput.value = "";
  
  // 4. Show loading state
  showTyping();
  setDisabled(true);

  try {
    // 5. Send to API and wait for response
    const data = await sendToApi(conversationHistory);
    
    // 6. Parse response
    const botResponse = parseGemini(data);
    
    // 7. Display bot message
    hideTyping();
    append(createMessageEl(botResponse, ROLES.MODEL));
    
    // 8. Add to history for context in next message
    updateHistory(ROLES.MODEL, botResponse);
    
  } catch (err) {
    // Handle errors gracefully
    hideTyping();
    append(createMessageEl(`Error: ${err.message}`, ROLES.MODEL));
    
    // Optional: Could add retry logic here
    
  } finally {
    // 9. Always re-enable controls
    setDisabled(false);
    userInput.focus();  // Return focus for better UX
  }
}

// -------------------------------------------------------------------------
// EVENT LISTENERS
// -------------------------------------------------------------------------

// Send button click
sendBtn.addEventListener("click", handleSend);

// Enter key in input field
userInput.addEventListener("keypress", (e) => {
  if (e.key === "Enter" && !e.shiftKey) {
    e.preventDefault();  // Prevent form submission
    handleSend();
  }
});

// -------------------------------------------------------------------------
// INITIALIZATION
// -------------------------------------------------------------------------

// Display welcome message when page loads
append(createMessageEl(
  "Hello! I'm here to support you. How are you feeling today?", 
  ROLES.MODEL
));

// Focus input field for immediate typing
userInput.focus();
```

#### JavaScript Architecture Explained

**1. State Management**
```javascript
let conversationHistory = [];  // Maintains context
let typingIndicator = null;    // UI reference
```

We keep conversation history in memory to provide context for each new message. The AI can reference previous messages for coherent responses.

**2. Separation of Concerns**

The code is organized into clear sections:
- **Constants** — Configuration values
- **DOM References** — Element lookups (done once)
- **Helper Functions** — Reusable utilities
- **API Communication** — Network logic
- **Event Handlers** — User interaction
- **Initialization** — Startup code

**3. Async/Await for Readability**
```javascript
async function handleSend() {
  try {
    const data = await sendToApi();  // Wait for response
    displayResponse(data);
  } catch (err) {
    displayError(err);
  }
}
```

**4. Error Handling**
```javascript
try {
  await sendToApi();
} catch (err) {
  // Show error in UI
} finally {
  // Always re-enable controls
  setDisabled(false);
}
```

The `finally` block ensures controls are re-enabled even if an error occurs.

**5. User Experience Details**
- **Typing indicator** — Shows the bot is "thinking"
- **Disabled controls** — Prevents duplicate submissions
- **Auto-scroll** — Keeps latest messages visible
- **Auto-focus** — Returns focus to input after sending

### Checkpoint ✓

All three frontend files are now complete. The structure should look like:

```
public/
├── index.html  (70 lines)
├── style.css   (150 lines)
└── script.js   (220 lines)
```

---

## <a name="step-6"></a>6. Running & Testing Your Chatbot

### Starting the Application

1. **Ensure your `.env` file has your API key**
2. **Start the development server:**

```bash
npm run dev
```

You should see output like:
```
[nodemon] starting `node index.js`
✓ Server listening on http://localhost:3000
✓ API Key configured: Yes
```

3. **Open your browser** and navigate to:
```
http://localhost:3000
```

### Testing the Chatbot

Try these test cases to ensure everything works:

#### Test 1: Basic Conversation
```
You: "Hello"
Bot: "Hello! How can I support you today?"
```

#### Test 2: Emotional Support
```
You: "I'm feeling stressed about exams"
Bot: "It's normal to feel stressed before exams. Try the 4-7-8 breathing technique: breathe in for 4 seconds, hold for 7, exhale for 8. Breaking study time into small chunks can also help."
```

#### Test 3: Context Retention
```
You: "I have a test tomorrow"
Bot: "How are you feeling about tomorrow's test?"
You: "Anxious"
Bot: "Test anxiety is common. Try reviewing your notes one last time tonight, then get good rest. Remember that you've prepared, and one test doesn't define you."
```

The AI should remember "test tomorrow" from your first message!

#### Test 4: Safety Response
```
You: "I want to hurt myself"
Bot: "I'm really concerned about what you're sharing. Please talk to a trusted adult, counselor, or call a crisis helpline immediately. You don't have to face this alone."
```

### Understanding What Happens

Let's trace a complete message flow:

```
1. User types "I'm anxious" and clicks Send
   ↓
2. script.js captures input, displays it immediately
   ↓
3. Message added to conversationHistory array
   ↓
4. "typing..." indicator appears
   ↓
5. POST request sent to http://localhost:3000/api/chat
   Body: { conversationHistory: [...] }
   ↓
6. index.js receives request, validates data
   ↓
7. Server sends conversation + system instructions to Gemini API
   ↓
8. Gemini generates contextual response
   ↓
9. Server receives response, forwards to frontend
   ↓
10. script.js parses response, removes "typing..." indicator
   ↓
11. Bot message displayed, added to history
   ↓
12. Input field re-enabled and focused
```

### Common Issues & Solutions

#### Issue 1: "API Key not configured"
**Cause:** `.env` file missing or not loaded
**Solution:**
```bash
# Verify .env exists
ls -la .env

# Check contents
cat .env

# Restart server
npm run dev
```

#### Issue 2: Blank page
**Cause:** `public/` folder not found or named incorrectly
**Solution:**
```bash
# Verify folder structure
ls -la public/
# Should show: index.html, style.css, script.js
```

#### Issue 3: "CORS error" in browser console
**Cause:** Frontend served from different origin
**Solution:** Always access via `http://localhost:3000`, not by opening `index.html` directly

#### Issue 4: Bot doesn't respond
**Cause:** API quota exceeded or invalid key
**Solution:**
- Check Google AI Studio for quota limits
- Generate a new API key if necessary
- Check browser console for error messages

#### Issue 5: Old changes not appearing
**Cause:** Browser cache
**Solution:** Hard refresh with `Ctrl+Shift+R` (Windows/Linux) or `Cmd+Shift+R` (Mac)

### Browser DevTools Debugging

Open Developer Tools (`F12` or right-click → Inspect):

**Console Tab:** Check for JavaScript errors
```javascript
// You should see:
Navigated to http://localhost:3000
// Not see any red errors
```

**Network Tab:** Monitor API requests
```
POST /api/chat   Status: 200   Response time: ~2s
```

**Application Tab:** Check if files are loaded correctly

---

## 📸 Submission Requirements

### What to Submit

To complete this project, you need to submit **a screenshot of your working chatbot** showing a meaningful conversation.

### Screenshot Guidelines

Your screenshot should include:

✅ **At least 3-4 message exchanges** (user and bot messages)  
✅ **The browser URL bar** showing `http://localhost:3000`  
✅ **A conversation demonstrating the chatbot's supportive responses**  
✅ **Clear, readable text** (not blurry or cut off)  

### How to Take a Screenshot

**On macOS:**
- **Full screen:** `Cmd + Shift + 3`
- **Selected area:** `Cmd + Shift + 4` (recommended)
- **Specific window:** `Cmd + Shift + 4`, then press `Space`, click window

**On Windows:**
- **Full screen:** `PrtScn` or `Windows + PrtScn`
- **Selected area:** `Windows + Shift + S` (Snipping Tool)
- **Specific window:** `Alt + PrtScn`

**On Linux:**
- **Full screen:** `PrtScn`
- **Selected area:** `Shift + PrtScn`
- Or use Screenshot tool from applications menu

### Example Conversation to Screenshot

Here's a sample conversation that demonstrates your chatbot working properly:

```
You: "Hello! I'm testing my chatbot."
Bot: "Hello! How can I support you today?"

You: "I've been feeling stressed about my coding project."
Bot: "It's normal to feel stressed about projects. Try breaking it into smaller tasks, and take short breaks every hour. Remember, every developer faces challenges—you're learning and growing!"

You: "Thanks, that helps!"
Bot: "You're welcome! Feel free to reach out anytime you need support."
```

### Tips for a Great Screenshot

1. **Test your chatbot first** — Make sure it's responding properly
2. **Choose meaningful messages** — Show that the AI understands context
3. **Clean your browser** — Close unnecessary tabs (optional, but professional)
4. **Good lighting** — If taking a photo, ensure good lighting and no glare
5. **File format** — PNG or JPG are both acceptable

### What If Something Goes Wrong?

If your chatbot isn't working when you try to take the screenshot:
- Review the [Troubleshooting Guide](#troubleshooting) below
- Check the browser console for errors (F12)
- Verify your API key is correctly configured
- Restart the server with `npm run dev`

---

## <a name="troubleshooting"></a>7. Troubleshooting Guide

### Debugging Methodology

When something doesn't work, follow this systematic approach:

1. **Check the Console** — Browser console (frontend) and terminal (backend)
2. **Verify Setup** — API key, file structure, dependencies
3. **Test Components** — Isolate frontend vs. backend issues
4. **Read Error Messages** — They usually point to the problem
5. **Check Network Tab** — Verify requests are being made

### Backend Debugging

**Problem: Server won't start**

```bash
# Check for syntax errors
node index.js

# Common issues:
# - Missing dependencies: npm install
# - Port already in use: Use different PORT in .env
# - Syntax error: Check error message for line number
```

**Problem: API returns errors**

```javascript
// Add logging to index.js
app.post("/api/chat", async (req, res) => {
  console.log("Received request:", req.body);
  // ... rest of code
});
```

**Check for:**
- API key validity (regenerate if needed)
- Request format (must be valid JSON)
- Rate limiting (60 requests/minute)

### Frontend Debugging

**Problem: Messages not appearing**

```javascript
// Add console logs to script.js
function append(el) {
  console.log("Appending element:", el);
  messagesContainer.appendChild(el);
}
```

**Problem: API requests failing**

```javascript
// Log API responses
async function sendToApi(history) {
  const rsp = await fetch(CONFIG.CHAT_API_ENDPOINT, {...});
  console.log("API response status:", rsp.status);
  const data = await rsp.json();
  console.log("API response data:", data);
  return data;
}
```

### Testing Without AI (Fallback Mode)

To test frontend without Gemini API, add a mock endpoint:

```javascript
// In index.js, add:
app.post("/api/chat/mock", (req, res) => {
  res.json({
    candidates: [{
      content: {
        parts: [{ text: "This is a mock response for testing." }]
      }
    }]
  });
});

// In script.js, temporarily change:
const CONFIG = {
  CHAT_API_ENDPOINT: "/api/chat/mock"  // Use mock endpoint
};
```

---

## <a name="next-steps"></a>8. Next Steps & Extensions

Congratulations! You've built a working AI chatbot. Here are ways to extend it:

---

## 🎨 Creative Challenge: Transform Your Chatbot!

Now that you have a working mental health chatbot, it's time to get creative! **The power of your chatbot lies in the system instructions** — by changing them, you can transform your chatbot into almost anything.

### Understanding System Instructions

The system instructions are like the chatbot's "personality" and "job description." Currently, your chatbot is a mental health assistant because of this code in `index.js`:

```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a compassionate mental health assistant. Respond kindly and offer practical, actionable, and brief tips or coping strategies. Keep responses concise, typically 1–3 sentences unless more detail is clearly beneficial. Avoid making diagnoses or giving medical advice. Focus on emotional support and general well-being techniques. If a user mentions intent to harm themselves or others, encourage them to seek immediate help from a trusted adult, counselor, or emergency services.";
```

**By changing these instructions, you can create entirely different chatbots!**

### 💡 Creative Ideas to Try

#### 1. **Career Counselor Bot**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an enthusiastic career counselor helping students explore career paths. Ask thoughtful questions about their interests, strengths, and goals. Suggest relevant careers, required education, and first steps. Keep responses encouraging and actionable, typically 2-3 sentences.";
```

**Example conversation:**
```
User: "I like science and helping people"
Bot: "That's a great combination! Have you considered careers like nursing, physical therapy, or biomedical research? What aspect of helping people excites you most?"
```

#### 2. **Study Buddy Bot**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a helpful study assistant. Help students with study techniques, time management, and understanding concepts. Ask clarifying questions, suggest study strategies, and provide encouragement. Break down complex topics into simple explanations. Keep responses clear and supportive.";
```

**Example conversation:**
```
User: "I have 3 exams next week and don't know where to start"
Bot: "Let's create a plan! What subjects are the exams for, and which one do you feel least prepared for? We'll prioritize and break it into manageable chunks."
```

#### 3. **Creative Writing Coach**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an inspiring creative writing coach. Help writers develop ideas, overcome writer's block, and improve their craft. Offer specific, actionable feedback and ask thought-provoking questions. Encourage creativity and unique perspectives. Keep responses brief but impactful.";
```

**Example conversation:**
```
User: "I want to write a story but have no ideas"
Bot: "Let's spark some ideas! What's the last thing that made you really emotional—happy, sad, or angry? Strong feelings often lead to compelling stories."
```

#### 4. **Fitness Motivation Bot**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an energetic fitness coach focused on motivation and healthy habits. Provide encouragement, simple exercise suggestions, and wellness tips. Keep responses upbeat and actionable. Emphasize progress over perfection. Remind users to consult professionals for medical advice.";
```

**Example conversation:**
```
User: "I want to start exercising but I'm always too tired"
Bot: "Start small—even 5 minutes counts! Try a short morning walk or stretching. The energy will come as you build the habit. What time of day do you usually feel most energetic?"
```

#### 5. **Language Learning Assistant**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a patient language learning tutor. Help learners practice conversations, explain grammar simply, and provide cultural context. Correct mistakes gently and offer encouragement. Ask questions to practice dialogue. Keep responses clear and educational.";
```

**Example conversation:**
```
User: "How do I introduce myself in Spanish?"
Bot: "Great question! You can say '¡Hola! Me llamo [your name]' (Hello! My name is...). Try it with your name!"
```

#### 6. **Coding Mentor Bot**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an experienced coding mentor helping beginners learn programming. Break down complex concepts into simple terms, suggest practice projects, and debug thought processes (not full solutions). Encourage problem-solving skills. Ask guiding questions rather than giving direct answers when possible.";
```

**Example conversation:**
```
User: "What's the difference between let and const?"
Bot: "Good question! 'let' is for variables that change, 'const' is for values that stay the same. If you're storing a user's age that might update, use 'let'. For a fixed value like 'maxRetries = 3', use 'const'. Which sounds right for a shopping cart total?"
```

#### 7. **Travel Planning Assistant**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an enthusiastic travel planning assistant. Help users discover destinations, plan itineraries, and find travel tips. Ask about their interests, budget, and travel style. Provide practical suggestions and insider tips. Keep responses inspiring yet realistic.";
```

#### 8. **Book Recommendation Bot**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a knowledgeable book recommender. Ask about reading preferences, past favorites, and current mood. Suggest books with brief, spoiler-free descriptions. Explain why each recommendation might appeal to them. Keep responses concise but engaging.";
```

#### 9. **Environmental Action Guide**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are an environmental educator focused on actionable sustainability tips. Provide practical, realistic suggestions for reducing environmental impact. Encourage without overwhelming. Celebrate small changes. Keep responses positive and empowering.";
```

#### 10. **Recipe & Cooking Helper**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a friendly cooking assistant. Help users with recipe suggestions, cooking techniques, and meal planning. Ask about dietary restrictions, available ingredients, and skill level. Provide clear, simple instructions. Keep responses practical and encouraging.";
```

### 🎯 Your Challenge

**Choose one of the above ideas (or create your own!) and transform your chatbot:**

1. **Modify the system instructions** in `index.js`
2. **Update the UI** to match the new purpose:
   - Change the header title in `public/index.html`
   - Update the placeholder text in the input field
   - Adjust the welcome message in `public/script.js`
   - (Optional) Change the color scheme in `public/style.css`
3. **Test your new chatbot** with relevant conversations
4. **Take a screenshot** of your transformed chatbot in action

### Example: Transforming to a Study Buddy

**Step 1: Update `index.js`**
```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a helpful study assistant...";  // Replace with study buddy instructions
```

**Step 2: Update `public/index.html`**
```html
<div class="header">
  <h2>Study Buddy Assistant</h2>
  <p>Let's ace those exams together!</p>
</div>
```

**Step 3: Update input placeholder in `public/index.html`**
```html
<input id="userInput" placeholder="What subject are you studying?" />
```

**Step 4: Update welcome message in `public/script.js`**
```javascript
append(createMessageEl(
  "Hey there! Ready to tackle some studying? What are you working on today?", 
  ROLES.MODEL
));
```

**Step 5: (Optional) Update colors in `public/style.css`**
```css
.header { 
  background: #1976d2;  /* Change from indigo to blue */
}
.message.user p { 
  background: #1976d2;  /* Match the header */
}
```

### 💭 Tips for Writing Great System Instructions

1. **Be specific** — Define the chatbot's role clearly
2. **Set boundaries** — Explain what it should and shouldn't do
3. **Define tone** — Friendly? Professional? Casual? Enthusiastic?
4. **Keep it concise** — The AI works best with clear, focused instructions
5. **Include response style** — Length, format, level of detail
6. **Add safety notes** — Especially for educational/health topics

### 🌟 Bonus Challenge: Create Your Own Unique Chatbot

Think outside the box! Create something unique:
- **Movie Quote Buddy** — Responds only in famous movie quotes
- **Rhyme Time Poet** — Answers everything in rhymes
- **Historical Figure** — Roleplay as Einstein, Shakespeare, or Marie Curie
- **Debate Partner** — Helps practice argumentation skills
- **Dad Joke Generator** — Provides terrible puns on demand
- **Interview Coach** — Practices job interview questions

**The possibilities are endless!** The same technical foundation can create wildly different user experiences just by changing the system instructions.

---

### Easy Extensions (1-2 hours)

**1. Persistent Conversation History**
```javascript
// Save to localStorage
localStorage.setItem('chatHistory', JSON.stringify(conversationHistory));

// Load on page load
const saved = localStorage.getItem('chatHistory');
if (saved) conversationHistory = JSON.parse(saved);
```

**2. Clear Chat Button**
```javascript
// Add to HTML
<button id="clearBtn">Clear Chat</button>

// Add handler in script.js
document.getElementById("clearBtn").addEventListener("click", () => {
  conversationHistory = [];
  messagesContainer.innerHTML = "";
  append(createMessageEl("Chat cleared. How can I help?", ROLES.MODEL));
});
```

**3. Typing Animation**
```css
/* Add to style.css */
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.3; }
}

.message.typing p::after {
  content: "...";
  animation: blink 1.5s infinite;
}
```

**4. Message Timestamps**
```javascript
function createMessageEl(text, role, isTyping = false) {
  const wrap = document.createElement("div");
  // ... existing code ...
  
  const time = document.createElement("span");
  time.className = "timestamp";
  time.textContent = new Date().toLocaleTimeString();
  wrap.appendChild(time);
  
  return wrap;
}
```

### Intermediate Extensions (3-5 hours)

**1. User Authentication**
- Add login/signup system
- Store conversations per user in database
- Use MongoDB or Firebase

**2. Mood Tracking**
- Add mood selection (😊 😐 😢)
- Store mood history
- Generate weekly mood reports

**3. Crisis Detection**
- Enhanced keyword detection
- Automatic resource suggestions
- Emergency contact quick links

**4. Multilingual Support**
```javascript
// Add language detection
const SYSTEM_INSTRUCTION_TEXT = 
  "Respond in the same language the user uses. " +
  "You support English, Spanish, French, and more...";
```

**5. Voice Input**
```javascript
// Use Web Speech API
const recognition = new webkitSpeechRecognition();
recognition.onresult = (e) => {
  userInput.value = e.results[0][0].transcript;
};
```

### Advanced Extensions (8+ hours)

**1. Deploy to Production**
- Host on Heroku, Railway, or Vercel
- Set up environment variables in hosting platform
- Configure custom domain

**2. Database Integration**
- Store conversations in PostgreSQL or MongoDB
- Track user analytics
- Generate insights dashboards

**3. Mobile App**
- Use React Native or Flutter
- Wrap as Progressive Web App (PWA)
- Add push notifications

**4. Advanced AI Features**
- Integrate with crisis helpline APIs
- Add resource recommendations (articles, videos)
- Implement sentiment analysis
- Generate personalized coping strategies

**5. Therapist Dashboard**
- Anonymous usage analytics
- Common concerns tracker
- Resource effectiveness metrics

### Learning Resources

**Frontend:**
- MDN Web Docs (JavaScript, HTML, CSS)
- freeCodeCamp (hands-on practice)
- JavaScript.info (comprehensive guide)

**Backend:**
- Express.js official documentation
- Node.js documentation
- REST API design best practices

**AI/ML:**
- Google AI documentation
- Prompt engineering guides
- Responsible AI practices

---

## Conclusion

You've successfully built a sophisticated AI chatbot that:

✅ Uses modern JavaScript (ES Modules, async/await)  
✅ Integrates with Google's Gemini AI  
✅ Implements secure API key management  
✅ Provides responsive, accessible UI  
✅ Handles errors gracefully  
✅ Maintains conversation context  
✅ Follows ethical AI practices  

### 📋 Before You Submit

Make sure you've completed:

1. **✓ Built the working chatbot** — All features functioning properly
2. **✓ Tested thoroughly** — Verified conversations work as expected
3. **📸 Taken a screenshot** — See the [Submission Requirements](#submission-requirements) section
4. **🎨 (Optional) Transformed your chatbot** — Try the [Creative Challenge](#creative-challenge-transform-your-chatbot)!

**Bonus points if you:**
- Transform your chatbot into something unique
- Submit a screenshot of BOTH versions (original mental health bot AND your creative transformation)
- Add your own custom styling or features

### Key Takeaways

1. **Architecture Matters** — Separating frontend, backend, and AI services creates maintainable code
2. **Security First** — Never expose API keys client-side
3. **User Experience** — Loading indicators, error messages, and accessibility features matter
4. **Ethical Responsibility** — AI for mental health requires careful consideration of user safety
5. **System Instructions Are Powerful** — The same technical foundation can create completely different experiences

### Your Portfolio Project

This chatbot is an excellent portfolio piece demonstrating:
- Full-stack development skills
- API integration expertise
- Modern JavaScript proficiency
- Responsible AI implementation
- Understanding of prompt engineering

Consider open-sourcing your project on GitHub!

---

## Appendix: Complete File Reference

### Project Structure
```
ai-mental-health-chatbot/
├── index.js              # Backend server (199 lines)
├── package.json          # Dependencies and scripts
├── .env                  # API key (NEVER commit!)
├── .gitignore            # Git exclusions
├── README.md             # Project documentation (create your own!)
└── public/
    ├── index.html        # Frontend structure (70 lines)
    ├── style.css         # Styles (150 lines)
    └── script.js         # Frontend logic (220 lines)
```

### Quick Command Reference

```bash
# Install dependencies
npm install

# Start development server (auto-restart on changes)
npm run dev

# Start production server
npm start

# Check for updates
npm outdated

# Update dependencies
npm update

# Add new package
npm install <package-name>
```

### API Endpoints Reference

**POST /api/chat**
- **Purpose:** Send message and get AI response
- **Request Body:** `{ conversationHistory: [...] }`
- **Response:** Gemini API response object
- **Status Codes:**
  - 200: Success
  - 400: Bad request (invalid body)
  - 500: Server or API error

**GET /api/models**
- **Purpose:** List available Gemini models
- **Response:** Array of model objects with names and capabilities

---

## Final Notes

### 📸 Submission Reminder

**Don't forget to submit your screenshot!** Review the [Submission Requirements](#submission-requirements) section for details on what to include.

**Extra Credit Opportunity:**
- Complete the [Creative Challenge](#creative-challenge-transform-your-chatbot) and submit screenshots of BOTH your original chatbot AND your transformed version
- Show off your creativity and understanding of system instructions!

### Important Reminders

**About This Project:**
- This is an educational project, not a substitute for professional mental health care
- Always include appropriate disclaimers
- Encourage users to seek professional help when needed
- Test thoroughly before sharing with others

**Need Help?**
- Check the browser console for errors (F12)
- Read error messages carefully
- Review this tutorial step-by-step
- Search for specific error messages online
- Verify your API key is properly configured

**Share Your Success!**
Once your chatbot is working, consider:
- Adding it to your portfolio website
- Writing a blog post about what you learned
- Sharing on GitHub with proper documentation
- Teaching others how to build it
- Creating variations with different system instructions

### What You've Learned

By completing this tutorial, you now understand:
- ✅ Full-stack application architecture
- ✅ RESTful API design and implementation
- ✅ Secure handling of API keys and environment variables
- ✅ Modern JavaScript (ES Modules, async/await, fetch)
- ✅ AI integration with third-party services
- ✅ Prompt engineering and system instructions
- ✅ Responsive UI design principles
- ✅ Error handling best practices
- ✅ Ethical considerations in AI development

**These are professional skills used by real software engineers!**

---

**Happy coding, and thank you for building technology that makes a difference! 🧠💙✨**

*Remember: Submit your screenshot(s) and have fun with the Creative Challenge!*
