# 🔒 Digital Safety and Secrets, Exit Ticket

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

Covers both days. Day 1 is accounts, Day 2 is your data and your code.

---

### Multiple Choice

**1. What makes a password strong?**

A) Using your birthday so it is easy to remember

B) Making it short so you can type it fast

C) Making it long (16 or more characters), unique, and unpredictable

D) Using the same strong password everywhere

---

**2. An email from "Amazon" says your account locks in 12 hours unless you click a link. The sender is `security@amaz0n-alerts.com`. What do you do?**

A) Click the link right away so you do not get locked out

B) Delete it. The fake domain and the deadline are phishing red flags.

C) Forward it to your friends to warn them

D) Reply and ask whether it is real

---

**3. What does two-factor authentication protect you from?**

A) Viruses on your computer

B) Someone who already stole your password, because they still cannot get in without the second factor

C) Slow internet

D) People reading your screen in public

---

**4. Why is AI-written phishing harder to spot than the old kind?**

A) It has more pictures

B) The grammar is perfect and the message is personalized, so the old tells are gone

C) It hacks your computer by itself

D) It only works on iPhones

---

**5. You have a project with two files. `app.py` reads a key using `os.getenv("API_KEY")`. `.env` contains `API_KEY=sk-abc123`. Which one is safe to post publicly?**

A) Both of them

B) Neither of them

C) `app.py` only

D) `.env` only

---

**6. What does `.gitignore` actually do?**

A) Hides files from your own computer

B) Encrypts your secrets so they cannot be read

C) Lists files Git refuses to upload, which is what keeps `.env` off the internet

D) Deletes files after you push them

---

### Short Answer

**7. Write a strong passphrase and explain why it beats a password like `Basketball2024!`**

______________________________________________________________________________

______________________________________________________________________________

---

**8. You are about to put a project on GitHub. It talks to an online service using a key. Name the two files you need and say what goes in each one.**

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **C.** Long, unique, unpredictable. Length matters most. A 16 character passphrase takes centuries.

2. **B.** Delete it. The domain `amaz0n-alerts.com` has a zero in it, and the countdown is a pressure tactic. If they are worried, go to amazon.com directly instead of using the link.

3. **B.** The stolen password is not enough on its own. The attacker also needs the phone or the app.

4. **B.** AI writes clean, personalized text at scale, so bad grammar no longer gives it away. Students should be checking the sender address and the link, not the writing quality.

5. **C.** `app.py` is safe because the key is never in it, only the name `API_KEY`. `.env` holds the real value and must never be posted.
   *Watch for:* students who answer B. They have the instinct right but have missed that keeping the code shareable is the entire point of the pattern.

6. **C.** It is a list of files Git will not include. Answer B is the tempting wrong one, since `.gitignore` does not encrypt anything. The file is still sitting in plain text on the machine.

7. Example: `tamarind-ferry-lantern-thunder`. Better because it is 30 characters, the words are unrelated to each other and to the student, and it is still easy to picture. `Basketball2024!` is short, built from a common word plus a year, and matches a pattern cracking tools try first.
   *Full credit needs the reason, not just a passphrase.*

8. `.env` holds the key itself, as `API_KEY=value`. `.gitignore` contains the line `.env` so Git never uploads it. The code reads the value by name at runtime.
   *Half credit for naming `.env` alone. The `.gitignore` half is the one that actually prevents the leak, and it is the half people forget.*
