# 🤖 AI Chatbot — Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

---

### Multiple Choice

**1. Why does our chatbot send messages to our own server instead of directly to Google Gemini?**

A) It's faster that way

B) To keep the API key secret — if the browser called Gemini directly, anyone could steal the key

C) Google doesn't allow browser requests

D) The server makes the chatbot look better

---

**2. What are "system instructions" in an AI chatbot?**

A) The code that makes the buttons work

B) Rules given to the AI before the conversation that control its personality and behavior

C) Instructions for how to install the project

D) Error messages that appear when something breaks

---

**3. What does an API key do?**

A) Encrypts all messages so nobody can read them

B) Proves your app is allowed to use a service (like Google Gemini)

C) Makes your website load faster

D) Stores the conversation history

---

**4. What is the difference between the frontend and the backend?**

A) Frontend runs in the browser (HTML/CSS/JS), backend runs on the server (Node.js)

B) Frontend is for mobile, backend is for desktop

C) Frontend is JavaScript, backend is Python

D) There is no difference — they are the same thing

---

**5. What does `async/await` do in JavaScript?**

A) Makes the code run faster

B) Lets the code wait for something (like an AI response) without freezing the whole app

C) Creates animations on the page

D) Connects to the database

---

### Short Answer

**6. Look at this system instruction:**

```javascript
const SYSTEM_INSTRUCTION_TEXT =
  "You are a dad joke expert. Every response must include a terrible pun.";
```

How would the AI respond differently compared to using no system instructions at all?

______________________________________________________________________________

______________________________________________________________________________

---

**7. What is the purpose of the `.env` file? Why is it listed in `.gitignore`?**

______________________________________________________________________________

______________________________________________________________________________

---

**8. Explain what `conversationHistory` does and why it's important. What would happen if we didn't send it with each message?**

______________________________________________________________________________

______________________________________________________________________________

---

**9. What does this line of code do?**

```javascript
app.use(express.static("public"));
```

______________________________________________________________________________

---

**10. You want to create a "Recipe Helper" chatbot. Write the system instruction text you would use (2-3 sentences).**

______________________________________________________________________________

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B** — To keep the API key secret. If the browser called Gemini directly, the key would be visible in the page source to anyone.

2. **B** — Rules given to the AI before the conversation that control its personality and behavior. The user never sees them, but they shape every response.

3. **B** — Proves your app is allowed to use a service. It's like a password that identifies your application to Google's servers.

4. **A** — Frontend runs in the browser (what the user sees), backend runs on the server (invisible to the user, handles security and API calls).

5. **B** — Lets the code wait for something (like an AI response) without freezing the whole app. The browser stays responsive while waiting.

6. With the dad joke system instruction, the AI would include puns and jokes in every response, no matter what the user asks. Without system instructions, the AI would respond normally and seriously. System instructions shape the AI's entire personality and response style.

7. The `.env` file stores secret values like the API key outside of the code. It's in `.gitignore` so it never gets uploaded to GitHub — if someone found your API key on GitHub, they could use it and potentially run up charges on your account.

8. `conversationHistory` is an array that stores every message (from both the user and the AI). It's sent with each new message so the AI has context about what was already discussed. Without it, every message would be treated as a brand new conversation — the AI would have no memory of what you just said.

9. This line tells Express to serve files from the `public/` folder. When someone visits `http://localhost:3000`, the server automatically sends `public/index.html`, along with `style.css` and `script.js`. Without this line, the web page wouldn't load.

10. Acceptable example: "You are a friendly cooking assistant. Help users find recipes based on what ingredients they have. Ask about dietary restrictions and skill level. Give clear, simple instructions and keep responses practical. 1-3 sentences."
