<!-- ===========================================================================
TEACHER PLANNING BLOCK. Delete nothing, this never renders on the site.

UNIT / FOLDER   : fundamentals
FILE NAME       : digital_safety.md
PERIODS         : 2
FIRST TAUGHT    : T1 2026-27

PREP THE DAY BEFORE
- [ ] Hardware charged / counted: none, this is a laptop lesson
- [ ] Accounts or logins students need: none new. They use accounts they already have.
      Do NOT require a school account for 2FA, some are managed and students cannot change them.
- [ ] Software already on lab machines: a browser. VS Code or any text editor for the Day 2 stretch.
- [ ] Printed or posted in the room: the three phishing examples, blown up, taped to the wall
- [ ] Test the whole build myself end to end: ____

TIMING FOR PERIOD 1 (Day 1: accounts)
- 5 min   Hook: put `password1` into the checker on the projector, watch it die instantly
- 10 min  Passphrase demo, build one together on the board
- 15 min  Students build three passphrases and test them
- 20 min  2FA walkthrough, students enable it on one account and screenshot
- 10 min  Spot the Phish, whole class, then clean up and exit ticket

TIMING FOR PERIOD 2 (Day 2: data and secrets)
- 5 min   Hook: show a photo and find the address, school, or plate in the background
- 10 min  Deepfake clip, then the verify-through-another-channel rule
- 15 min  Secrets: what one is, where they leak, the taped-key comparison
- 25 min  The .env drill. Base tier spots the leak, stretch tier builds the .env and .gitignore
- 10 min  Reflection and clean up

WHERE STUDENTS GET STUCK
- School-managed account will not let them turn on 2FA -> have them use a personal account
  (gaming, social) instead. Any account counts.
- Student does not want to screenshot a real account -> blurring is fine, or use a throwaway.
- MS students find .env abstract -> stay on the base tier, spotting the leak in a screenshot.
  Do not push them into the terminal.
- "I don't have anything worth stealing" -> the SIM swap and account-resale angle usually lands.

IF THEY FINISH EARLY   : the Day 2 stretch, or the haveibeenpwned audit bonus
IF THEY NEED MORE TIME : Day 2 secrets carries into the next period. Day 1 must finish on Day 1
                         because the 2FA screenshot is the deliverable that takes longest to chase.

ASSESSMENT
- Category  : Informal Assessments
- Points    : 25
- Schoology : ____   Section(s): both

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🔒 Digital Safety and Secrets

### Lock down your own accounts, then learn to handle the keys your code depends on

> **Grades:** 7th to 12th &nbsp;|&nbsp; **Time:** 2 class periods &nbsp;|&nbsp; **Difficulty:** Beginner
>
> You already have accounts worth stealing. Over two days you will make your passwords hard to crack, turn on the one setting that stops most break-ins, learn to spot a fake message even when it is written perfectly, and then learn how programmers keep **secrets** out of their code. That last part is the reason you will not leak a password in every project you build this year.

---

## 🎯 What You'll Learn

- How to build a **passphrase** that would take centuries to crack
- How **two-factor authentication** stops someone who already has your password
- How to spot **phishing** even when the grammar is perfect and the sender looks real
- What a **secret** is in programming, and why it never goes in your code
- How a **.env** file keeps a key out of the file you share

---

## 🧰 What You Need

- A computer with a web browser
- One account you actually control and can change settings on. A personal account is fine and is usually easier than a school one.
- A text editor for the Day 2 stretch. [VS Code](https://code.visualstudio.com/) is on the lab machines.
- [Password strength checker](https://www.security.org/how-secure-is-my-password/), runs in the browser, nothing to install
- [Have I Been Pwned](https://haveibeenpwned.com/), for the bonus

---

# Day 1: Lock Down Your Accounts

**Goal:** By the end of today you have three passphrases you can actually remember, two-factor authentication switched on somewhere real, and the ability to look at a message and say why it is fake.

---

### Step 1: Watch a bad password die

These show up at the top of the leaked-password lists every single year.

| Rank | Password | Time to crack |
|---|---|---|
| 1 | `123456` | under a second |
| 2 | `password` | under a second |
| 3 | `qwerty` | under a second |
| 4 | `abc123` | under a second |
| 5 | Your birthday | minutes to hours |

Attackers do not sit there typing guesses. They run software that tries millions of combinations a second against a stolen list. Anything on that table is gone before you finish reading this sentence.

1. Open the [password strength checker](https://www.security.org/how-secure-is-my-password/)
2. Type in something close to a password you have used before. Not the real one.
3. Read the crack time

> **⚠️ Never type a password you actually use into any website.** Type something similar instead. This applies to every "check your password" tool on the internet, including this one.

> **✅ Checkpoint:** You have seen a real crack-time estimate for a weak password on your own screen.

---

### Step 2: Build a passphrase

Length beats everything else. Each character you add multiplies the work an attacker has to do.

| Length | Time to crack by brute force |
|---|---|
| 6 characters | seconds |
| 8 characters | hours |
| 12 characters | centuries |
| 16+ characters | effectively impossible |

The easiest way to get long and still remember it is to string together four or five unrelated words.

```
mango-bicycle-cloud-seventeen
purple-guitar-elephant-sunrise
Tamarind-Ferry-Lantern-42!
```

Unrelated is the important part. `saint-croix-high-school` is four words and still weak, because it is a phrase someone could guess about you.

1. Write three passphrases of four or more unrelated words each
2. Test each one in the checker
3. Write down the crack time next to each

> **✅ Checkpoint:** Three passphrases, each showing a crack time measured in centuries or longer.

---

### 🧠 Mini Lesson: why length beats symbols

Schools and websites spent years telling people to add a capital, a number, and a symbol. That advice produced `Password1!`, which is short, predictable, and cracks fast.

Think of it as a combination lock. Adding symbols gives you more choices per dial. Adding length gives you more dials. Another dial multiplies the total combinations, so it wins every time. Four random words give you enough dials that no amount of computing power gets through in a human lifetime.

That is why a long phrase you can remember beats a short mess you have to write on a sticky note.

---

### Step 3: Turn on two-factor authentication

Two-factor means logging in takes two things: something you **know** (your passphrase) and something you **have** (your phone). Someone who steals your password still cannot get in.

| Method | Security | How it works |
|---|---|---|
| Text message code | Good | A code is texted to your phone |
| Authenticator app | Better | An app generates a code that changes every 30 seconds |
| Hardware key | Best | A physical device you plug in |
| Fingerprint or face | Good | Your device confirms it is you |

Text codes are the weakest of the four because of SIM swapping, which you will read about in Step 4. They are still far better than nothing.

Turn it on somewhere that matters. Email first if you can, because password resets for everything else land there.

1. Open the security settings of an account you control
2. Find two-factor authentication, two-step verification, or login verification. The name changes by site.
3. Turn it on and finish the setup
4. Screenshot the confirmation screen. Blur anything private.

> **✅ Checkpoint:** A screenshot showing two-factor authentication is on.

---

### Step 4: Spot the phish

Phishing is someone pretending to be a company or a person you trust so you hand over something. It is how most people actually get hacked. The movie version, where someone breaks the encryption, almost never happens.

Older scam emails were easy to spot because the grammar was broken. That tell is gone. AI writes clean, personalized messages at scale, sometimes from an account belonging to someone you know. So you check structure instead of tone.

**🚩 Read the sender address itself.** The display name is free to type. The name says Apple Support and the address says `support@apple-security-update-2026.com`.

**🚩 Urgency and threats.** "Your account will be DELETED in 24 hours." Real companies do not work this way.

**🚩 A generic greeting.** "Dear Customer" from a company that knows your name.

**🚩 The link does not match.** Hover first. `paypa1.com` uses a number one. `paypal.security-update.com` belongs to `security-update.com`, not PayPal. The real domain is the part right before the first single slash.

**🚩 An attachment you did not ask for.** Especially `.exe`, `.zip`, and `.scr`.

**🚩 Too good to be true.** It is not true.

Now judge these three.

**Message 1**
> From: netflix-support@netflix.com
> Subject: Your payment failed
> "Hi Amali, we could not process your last payment. Update your billing at https://netflix.com/account/billing"

**Message 2**
> From: security@amaz0n-alerts.com
> Subject: Unusual sign-in activity
> "Dear Customer, we detected suspicious activity. Click here immediately to secure your account or it will be locked within 12 hours."

**Message 3**
> From: your teacher's real address
> Subject: Assignment update
> "Hi class, I updated the rubric for the capstone. Check Schoology for the new version."

> **Answers:** Message 1 looks real. Correct domain, uses your name, the link goes to the real netflix.com. Message 2 is phishing. The domain has a zero in it, the greeting is generic, and it threatens you with a deadline. Message 3 looks real. Known sender, nothing to click, no pressure.

> **✅ Checkpoint:** You can say out loud which red flag gives Message 2 away.

---

### 📝 Day 1 Deliverables

- [ ] Three passphrases with the crack time for each
- [ ] Screenshot of two-factor authentication enabled, private parts blurred

---

# Day 2: Protect Your Data and Your Code

**Goal:** By the end of today you know what you are giving away without meaning to, and you know where a password belongs in a project you are going to share.

---

### Step 1: See what a photo gives away

Here is what someone builds from pieces that each feel harmless.

| What they get | What they do with it |
|---|---|
| Full name and birthday | Open accounts in your name |
| Email and password | Get into your other accounts, then message your friends as you |
| Phone number | SIM swap, taking over your number and every code sent to it |
| School or workplace | Write a phishing message convincing enough to fool you |
| Location, live | Know when your house is empty |

Look at the last five photos on your phone without opening anything private. Check the backgrounds. Look for a house number, a street sign, a school logo, a license plate, a package label, a screen with a name on it.

The rules that follow from this are short. Keep profiles private. Post the vacation photos after you get home. Check the background before you post. Ask whether you would be fine with a stranger, a teacher, and an employer all seeing it.

> **✅ Checkpoint:** You found at least one identifying detail in the background of a photo, yours or a classmate's.

---

### Step 2: Assume the voice can be faked

A few seconds of audio is enough to clone a voice. Video of a real person saying things they never said is cheap to make now. A profile photo of a person who does not exist takes one click.

You cannot win this by looking harder at the video. The fakes get better every year and your eyes do not. So the defense is procedural instead of visual.

**Verify through a different channel.** A call from a panicked family member asking for money gets hung up on and called back on the number you already have. A message from a friend asking for a code gets a text to that friend. A news claim gets checked against a second source you went and found yourself.

This one habit covers voice cloning, deepfake video, hacked accounts, and every scam that has not been invented yet, because it never depends on you detecting the fake.

---

### Step 3: Learn what a secret is

A **secret** is any value that proves who you are to a computer. A password. An **API key**. A Wi-Fi password. A database login. A token an app uses to talk to a service.

Here is the problem, and it is the reason this section exists in a Computer Science class instead of a health class.

```python
# BAD. Never do this.
api_key = "sk-a83ff20c9d4e1b77c5"

response = ask_the_ai(api_key, "explain recursion")
```

That key is now inside your code. Every place the code goes, the key goes. You post the project to GitHub, the key is public. You share the folder with a partner, they have your key. You submit a screenshot to Schoology, the key is in the picture. Bots scan public code for keys around the clock and start spending on them within minutes.

Putting a key in your code is like taping your house key to your front door and then handing out photos of your door.

**The rule: the code goes in the file you share. The secret goes in a file you never share.**

---

### Step 4: Put the secret somewhere safe

A `.env` file holds the secrets. It sits next to your code and it never leaves your machine.

**Base tier, everyone does this.** Look at this pair of files and answer three questions.

`app.py`
```python
import os
from dotenv import load_dotenv

load_dotenv()
api_key = os.getenv("API_KEY")

response = ask_the_ai(api_key, "explain recursion")
```

`.env`
```
API_KEY=sk-a83ff20c9d4e1b77c5
```

1. Which of these two files is safe to post publicly?
2. If you emailed a classmate only `app.py`, would they have your key?
3. What would happen if you posted `.env` to GitHub?

**Stretch tier, required for high school, bonus for middle school.** Build it and prove it works.

1. Make a folder with a file called `.env` containing one made-up key:

```
API_KEY=not-a-real-key-12345
```

2. Make a file called `.gitignore` next to it containing one line:

```
.env
```

3. Make `read_secret.py`:

```python
import os
from dotenv import load_dotenv

load_dotenv()
print("Loaded key:", os.getenv("API_KEY"))
```

4. Install the library and run it:

```bash
pip install python-dotenv
python read_secret.py
```

You should see `Loaded key: not-a-real-key-12345`.

> **✅ Checkpoint:** Your terminal printed the key, and the key is nowhere inside `read_secret.py`.

---

### 🧠 Mini Lesson: why .gitignore is the part people forget

`load_dotenv()` reads the `.env` file and hands the values to your program at the moment it runs. Your code asks for `API_KEY` by name and never contains the value.

`.gitignore` is the second half, and skipping it is the single most common way keys leak. It is a list of files Git refuses to include when you save or upload your work. Without that one line, the moment you push your project the `.env` goes with it, and everything you just did was for nothing.

Real key leaked by a real company, real often. This is not a beginner mistake. It is the mistake.

---

### 📝 Day 2 Deliverables

- [ ] Your three answers from the base tier
- [ ] Stretch only: screenshot of the terminal printing the key, plus your `.gitignore`

---

## 🎚️ Base and Stretch

**Base, everyone does this.**
Three passphrases with crack times, two-factor authentication turned on with a screenshot, the phishing red flag identified, and the three secret-handling questions answered correctly.

**Stretch, required for high school, bonus for middle school.**
A working `.env` setup: the `.env` file, a `.gitignore` containing it, and a script that prints the key without the key appearing anywhere in the script. Screenshot the terminal output.

---

## 📝 Deliverables

1. **Three passphrases** with the crack time for each. Make up new ones, never submit a password you use.
2. **Screenshot of two-factor authentication** enabled on an account, private details blurred
3. **Phishing analysis**: two example messages with the red flags labeled
4. **Secrets questions**: your three answers, or the stretch screenshots if you did the stretch
5. **Reflection** (3 to 5 sentences): What is the biggest security mistake you have been making? What are you changing?

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | Your three passphrases with crack times |
| 2 | Screenshot of two-factor authentication enabled, private info blurred |
| 3 | Two phishing examples with the red flags labeled |
| 4 | Your three secrets answers, or the stretch terminal screenshot and `.gitignore` |
| 5 | Your written reflection (3 to 5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**. Do **NOT** click "Create", it is for text only and will not let you attach files.
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Accounts Secured | 10 | Strong passphrases, two-factor actually enabled with proof, phishing red flags correctly identified |
| Secrets Handling | 5 | Base answers correct, or a working `.env` and `.gitignore` for the stretch |
| Understanding | 5 | Reflection explains in your own words why these steps work |
| Deliverables | 5 | Everything above submitted, on time |

**Bonus:**
- **+3 points** for a middle school student who completes the stretch tier
- **+2 points** for running your email through [Have I Been Pwned](https://haveibeenpwned.com/) and reporting which breaches it appeared in

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Passphrase** | A password built from several unrelated words, long enough that guessing it is hopeless |
| **Two-Factor Authentication** | Needing two different proofs to log in, usually a password plus a code on your phone |
| **Phishing** | Pretending to be someone trustworthy to trick you into handing over information |
| **Social Engineering** | Attacking the person instead of the computer |
| **SIM Swap** | Taking over someone's phone number so every code sent to it arrives at the attacker instead |
| **Data Breach** | A company's stored logins getting stolen |
| **Deepfake** | Video or audio of a real person, generated by AI, showing something that never happened |
| **Secret** | Any value that proves identity to a computer: a password, an API key, a token |
| **API Key** | A string that identifies your account to an outside service, usually attached to money or private data |
| **.env file** | A file holding secrets, kept next to your code and never shared |
| **.gitignore** | A list of files Git refuses to upload, which is what keeps `.env` off the internet |
| **Brute Force** | Trying every possible combination until one works |

---

## 💡 Troubleshooting

**"My school account will not let me turn on two-factor."**
→ It is probably managed by the school and locked. Use a personal account instead. Any account you control counts for this assignment.

**"I do not want to screenshot my real account."**
→ Blur everything except the confirmation that two-factor is on. That is all that is being checked.

**"The checker says my passphrase is weak."**
→ Your words are probably related to each other or to you. Swap in words that have nothing to do with each other or with your life.

**"`pip install python-dotenv` says pip is not found."**
→ Try `pip3 install python-dotenv`, or `python3 -m pip install python-dotenv`.

**"My script prints `Loaded key: None`."**
→ Three usual causes. The file is named `.env.txt` instead of `.env`, the file is in a different folder than the script, or there are spaces around the `=`. It must read `API_KEY=value` with nothing between.

**"I cannot see the `.env` file in my folder."**
→ Files starting with a dot are hidden. On Mac press `Cmd + Shift + .` in Finder. On Windows turn on hidden items in the View tab.

**"I do not have anything worth stealing."**
→ Your accounts are worth money to someone who resells them, and your identity is worth more. Your phone number alone can be used to reset logins you have forgotten you own.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [x] Every command and version checked against the live source today (2026-09-09)
      security.org checker replaced the dead howsecureismypassword.net link
- [x] No API keys, passwords, or Wi-Fi credentials anywhere in the file (the sk- string is fake)
- [x] Every checkpoint is something a student can actually see
- [x] Base tier is readable by a 7th grader
- [x] No safety block, this lesson touches no hardware
- [x] No em dashes or en dashes in student-facing text, per house style
- [ ] Site version: strip "How to Submit" before publishing to thinkinbits.site
=========================================================================== -->
