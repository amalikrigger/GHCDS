<!-- ===========================================================================
TEACHER PLANNING BLOCK — delete nothing, this never renders on the site.
Fill it while planning. It stays in the repo as the record of how this ran.

UNIT / FOLDER   : {{ fundamentals | ai-chatbots | robotics | raspberry-pi | flutter | capstone }}
FILE NAME       : {{ snake_case_name }}.md
PERIODS         : {{ 1 }}   (one period = 60-65 min. Use Day blocks if 2+, Part blocks if 1.)
FIRST TAUGHT    : {{ trimester + year }}

PREP THE DAY BEFORE
- [ ] Hardware charged / counted: {{ what, how many }}
- [ ] Accounts or logins students need: {{ or "none" }}
- [ ] Software already on lab machines: {{ }}
- [ ] Printed or posted in the room: {{ }}
- [ ] Test the whole build myself end to end: {{ date }}

TIMING FOR PERIOD 1
- {{ 5 }} min  Hook / what we are making today, show the finished thing
- {{ 10 }} min Demo the first step together
- {{ 40 }} min Students build, I circulate
- {{ 5 }} min  Clean up, pack kits, exit ticket

WHERE STUDENTS GET STUCK
- {{ known snag }} -> {{ what to say or do }}

IF THEY FINISH EARLY   : {{ which optional challenge }}
IF THEY NEED MORE TIME : {{ what to cut, what carries to next period }}

ASSESSMENT
- Category  : {{ Formal Assessments | Informal Assessments }}
- Points    : {{ 25 }}
- Schoology : {{ due date }}   Section(s): {{ MS 01YR | Comp Sci 01T_ | both }}

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# {{ emoji }} {{ Lesson Title }}

### {{ One line saying what the student walks out with }}

> **Grades:** 7th–12th &nbsp;|&nbsp; **Time:** {{ N }} class periods &nbsp;|&nbsp; **Difficulty:** {{ Beginner | Intermediate | Advanced }}
>
> {{ Two or three sentences. What they are building, what it does, and why it is worth their time. Write it so a 7th grader reads it and wants to start. }}

---

## 🎯 What You'll Learn

- How to {{ do the main thing }}
- How **{{ key concept }}** works
- How to {{ transferable skill they keep after this project }}
- {{ 3 to 5 bullets total. Bold the terms that show up again in the Vocabulary table. }}

---

## 🧰 What You Need

- {{ Hardware, with the exact model }}
- {{ Cable / adapter, if the wrong one wastes ten minutes }}
- A computer with {{ browser | Python 3 | VS Code }}
- {{ Link to the tool: [name](https://url) — say if it runs in the browser with no install }}

<!-- Delete this block if the lesson does not touch drones, robots, printers, the laser cutter, or soldering. -->

## ⚠️ Safety Rules — Read Before You Start

These are non-negotiable. Breaking them on purpose means you lose access to the tool and earn a 0 for the day.

1. **{{ rule }}**
2. **{{ rule }}**
3. **{{ rule }}**
4. **If something goes wrong**, {{ what actually happens and what to do }}
5. **Report damage, a burn smell, or an injury right away.** You will not be in trouble for reporting something.

---

<!-- ===========================================================================
BODY. Pick ONE shape and delete the other.

  Multi-period build  ->  `# Day 1:`, `# Day 2:` ...  (H1 per day)
  Single period       ->  `## Part 1: Title (15 minutes)` ... (H2 per part)

Copy the block below once per day or part. There is no fixed number.
=========================================================================== -->

# Day {{ N }}: {{ What they accomplish today }}

**Goal:** {{ One sentence. The thing that is true at the end of today that was not true at the start. }}

---

### Step 1 — {{ Action verb first }}

1. {{ Do this }}
2. {{ Then this }}

```{{ bash | python | javascript | html }}
{{ exact command or code, copy-paste ready }}
```

{{ One or two sentences explaining what just happened, in plain words. Never leave a command unexplained. }}

> **✅ Checkpoint:** {{ What they should see on screen or in their hand right now. If they do not see it, they stop and ask. }}

---

### Step 2 — {{ Next }}

{{ Same shape. Small steps. Screenshot-able checkpoints. }}

> **✅ Checkpoint:** {{ }}

---

### 🧠 Mini Lesson — {{ The concept behind what they just did }}

{{ Two to four short paragraphs, or a small table. Teach the idea only after they have made it work, never before. Use a comparison from something they already know. }}

---

### 📝 Day {{ N }} Deliverables

- [ ] {{ Screenshot or photo of the checkpoint }}
- [ ] {{ The file or the working thing }}

<!-- End of repeatable Day block. -->

---

## 🎚️ Base and Stretch

**Base — everyone does this.**
{{ The finished thing every student turns in. }}

**Stretch — required for high school, bonus for middle school.**
{{ A real step up: a new capability, a harder constraint, a second feature, or a real user testing it. Not "make it neater". }}

---

## 📝 Deliverables

1. **{{ The build }}** — {{ what form it takes }}
2. **A demo video** ({{ 30-60 }} seconds) showing {{ what it does }}
3. **Reflection** (3-5 sentences): What did you build? What was the hardest part? What would you add with more time?

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Screenshot / Submit |
|---|---|
| 1 | {{ }} |
| 2 | {{ }} |
| 3 | Your written reflection (3-5 sentences) |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"** — do **NOT** click "Create" (Create is for text only and will not let you attach files)
4. Select your files and click **Submit**

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| Working Project | 10 | {{ It runs and does what they set out to do }} |
| {{ Complexity }} | 5 | {{ The specific thing that separates real work from the minimum }} |
| Understanding | 5 | {{ Reflection or walkthrough shows they know why it works }} |
| Deliverables | 5 | Everything above submitted, on time |

**Bonus:**
- **+{{ 3 }} points** for {{ the stretch, when a middle school student does it }}
- **+{{ 2 }} points** for {{ inventing their own version instead of following the example }}

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **{{ Term }}** | {{ Plain-language definition. No jargon inside the definition. }} |
| **{{ Term }}** | {{ }} |

---

## 💡 Troubleshooting

**"{{ The exact sentence a student says out loud }}"**
→ {{ The fix, in one or two sentences. }}

**"{{ }}"**
→ {{ }}

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [ ] Every command and version checked against the live source today
- [ ] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [ ] Every checkpoint is something a student can actually see
- [ ] Base tier is readable by a 7th grader
- [ ] Safety block present if the lesson touches hardware
- [ ] Every {{ placeholder }} replaced
- [ ] Site version stands alone: it is fine to leave "How to Submit" out of the
      published page, since Schoology steps live in Schoology.
=========================================================================== -->
