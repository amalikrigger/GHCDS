<!-- ===========================================================================
TEACHER PLANNING BLOCK. Delete nothing, this never renders on the site.

UNIT / FOLDER   : robotics
FILE NAME       : robomaster_competition.md
PERIODS         : Term-long team project, roughly Oct 13 - Nov 24. Not a single or multi day build.
FIRST TAUGHT    : T1 2026-27

PREP THE DAY BEFORE
- [ ] Hardware charged / counted: all working RoboMaster S1 units, currently 4, 2 more being built
- [ ] Accounts or logins students need: none new. Robots are activated on a teacher DJI account,
      never a student one. See Safety Rules below, this is not optional.
- [ ] Software already on lab machines: the RoboMaster app, block coding is the default path.
      Python inside the app's Lab is a stretch option, not yet built as a reference for students.
- [ ] Printed or posted in the room: the Game Design Document template, the Open Events board
      (the three autonomous events any crew can enter, see below)
- [ ] Test the whole build myself end to end: not applicable, this is open build and design time

WHERE STUDENTS GET STUCK
- "Our game does not need any code" -> that is fine for the game itself. Point them at the Open
  Events board: every crew still enters an autonomous event from that list, which is where the
  Programmer role and the individual code requirement live.
- Two crews want the same game idea -> first one to submit a claimed proposal keeps it. Say so
  up front so nobody argues about it later.
- A crew cannot find three real competitions to research -> point them at RoboMaster's own
  university league and the DJI 2019 S1 Challenge as a starting pair, then have them find a
  third themselves.
- Rules fall apart in front of people who did not write them -> normal. That is what Stage 1 is
  for. Do not let a crew treat a broken rule as a failure, it is the assignment working.

IF THEY FINISH EARLY   : a bonus Game Design Document field, or help another crew's playtest
IF THEY NEED MORE TIME : the design document deadline can flex, the live event dates cannot

ASSESSMENT
- Category  : Formal Assessments
- Points    : 100 (70 group, 30 individual, see Grading Rubric)
- Schoology : due dates pending, not yet posted. Section(s): both
- Do not publish this page or post the Schoology assignment until Amali confirms due dates,
  the Boo Bash table, and that the RoboMaster units are formally requested for 30 October.

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🤖 RoboMaster Competition: Design the Game

### Your crew designs one event. The whole school ends up playing it.

> **Grades:** 7th to 12th &nbsp;|&nbsp; **Time:** The back half of the trimester &nbsp;|&nbsp; **Difficulty:** Intermediate to advanced, team project
>
> The RoboMasters have been sitting in this room for a while and nobody has done anything with them yet. That changes now. You and your crew design, build, and run one event in a real competition using our S1 robots: a course, a battle, a race, whatever you invent. You write the rules, you program the robot, you playtest it, and you referee it live. First your own class plays it. Then the other section plays it. Then the whole school does, at a public event you help run.

---

## 🎯 What You'll Learn

- How to design a game that is actually fair: clear scoring, a real way to win, rules that hold up when a stranger plays
- How to program a **RoboMaster S1 autonomous routine** that runs start to finish with nobody touching a controller
- How **playtesting** finds the holes in your own rules before an audience does
- How to run a live event: referee a match, keep score, keep everyone safe
- Whatever your crew's **lead role** teaches at real depth: driving, programming, field building, or documentation

---

## 🧰 What You Need

- You must have already completed **RoboMaster: Navigate the Room**, or already know how to drive and code a RoboMaster. This project builds on that, it does not repeat it.
- A RoboMaster S1, charged and activated. Robots are set up by Mr. Krigger on a teacher account, not a student one. See Safety Rules.
- The RoboMaster app, in **Lab** mode. Block coding (Scratch) is the default. Python inside the Lab is available if you want to push further.
- Field materials for whatever your game needs: tape, cones, cardboard, targets. Ask Mr. Krigger, the lab is a makerspace and these are cheap.
- The **Game Design Document** template, from Schoology.

---

## ⚠️ Safety Rules: Read Before You Start

These are non-negotiable. Breaking them on purpose means you lose access to the robots and earn a 0 for the day.

1. **Eye protection whenever a blaster is armed.** No exceptions, no matter how short the test.
2. **Never fire at a person's face.** The blaster fires an infrared beam and, in games that use them, gel beads. Neither goes near anyone's eyes on purpose.
3. **Gel beads only inside a space built for them**, supervised, with a way to clean up after. If your game does not specifically need beads, run it on infrared. Hits still register.
4. **Batteries charge at the charging station.** Never left charging unattended overnight, never swapped mid match without powering the robot down first.
5. **No robot runs with nobody watching it.** Autonomous does not mean unsupervised.
6. **Report damage, a burn smell, or an injury right away.** You will not be in trouble for reporting something. These are the only RoboMaster units this class has, and DJI does not make more of them.

---

## Build One Game, Enter Others

Two separate things, and they stay separate on purpose.

**You build one game.** Your crew designs, builds, and owns exactly one event in the competition. It might use a program. It might not. A game like Capture the Flag or Robot Soccer does not need one, and forcing code into a game that does not want it just makes the game worse. Build the game that is actually good.

**You enter other games too**, including a set of autonomous events that run all term no matter what anyone designs:

| Event | What it is |
|---|---|
| **Precision Return** | Loop the room, stop on the mark, autonomous |
| **Line Sprint** | Fastest clean run along a taped line, autonomous |
| **Figure 8 Grand Prix, auto division** | The Navigate the Room figure 8, timed, autonomous |

**Every crew must enter at least one of these three**, hands off, with a working program. That is where the coding requirement actually lives. It is why the Programmer role always has a real job, even on a crew whose own game has no code in it, and why every student always has somewhere to ship code.

---

## Your Crew and Your Lead Role

High School runs four crews of four. Middle School runs three crews of three. Everyone on a crew participates in everything. On top of that, each student leads one area and is graded on it directly, so it is clear who did what.

Middle School crews of three double up two roles. The crew decides which two combine, and says so in the Game Design Document.

| Role | What you own | You owe, five points each |
|---|---|---|
| **Pilot** | Driving | Every crew member completes a clean driver run because you ran the clinic &middot; you drive in at least one live match &middot; you give the safety briefing before every match your game runs |
| **Programmer** | The code | Your crew's Open Events entry runs start to finish with nobody touching the controls &middot; you tuned it at least twice and can say what changed and what happened &middot; every crew member has code of their own that runs, because you taught them |
| **Engineer** | Hardware and field | Your game's field is built and sets up in under ten minutes &middot; a written pre match check exists and gets used every time &middot; batteries, armor, and beads are ready whenever your crew is called |
| **Media and Rules** | The document | The rules and penalties section is written and holds up in play &middot; the referee script is written so a substitute could run your game cold &middot; the recap exists, photos or film plus a short write-up |

---

## The Game Design Document

One form, every crew, turned in twice: a draft before Stage 1, a final version after Stage 2. Six fields are required. Test for whether a field is actually finished: **could a referee who has never met you run your game from this page alone?**

**Required**

1. **Game name and the one line pitch.** What the announcer says, and what a spectator sees happening.
2. **Setup.** What you build, roughly how big, what it is made of.
3. **How to play.** Robots per side, match length, what starts and stops the clock.
4. **How you score and how you win.** Every way to earn a point, with the number. How a tie is broken.
5. **Rules and penalties.** What is illegal, what it costs, and the safety rules specific to your game on top of the ones above.
6. **Referee script.** What the ref says and does, in order, start to finish.

**Bonus, not required of anyone**

- A field diagram drawn to real measurements.
- Program notes, if your game uses one: what it does, when it runs.

---

## How the Competition Runs

Three stages. Each one is bigger than the last, and each one finds problems with your rules that the last stage could not.

| Stage | When | What happens |
|---|---|---|
| **1. Inside the class** | Oct 13 to Oct 23 | Each section plays every crew's game within its own section. Your rules get tested by people who did not write them. Expect to change something. |
| **2. Class against class** | Oct 26 to Nov 13 | Middle School and High School play each other's games. A game that only makes sense to the crew who built it breaks here. |
| **3. The whole school** | Boo Bash 30 Oct, championship week of Nov 16 | Boo Bash is a public demo booth, students design it, not finished on purpose. The championship the week of Nov 16 is the real event: staff, other classes, and Mr. Krigger enter. |

**Winning a match is worth zero points.** Placement earns bragging rights, not grade points. Your grade comes from the game you built, the document you wrote, the code you shipped, and the match you ran.

---

## 🎚️ Base and Stretch

**Base, everyone does this.**
Join a crew, claim a lead role. Research three real robot competitions and say what you took from each. Propose your game and claim it before another crew does. Complete the six required fields of the Game Design Document, final version. Run two playtests with people outside your crew, and change at least one rule because of what happened. Enter at least one Open Events event with a working autonomous program. Drive in at least one live match. Write code of your own that runs on a robot. Referee, score, or film two matches you are not competing in. Set up, referee, and run your own game live, finished on time.

**Stretch, required for high school, bonus for middle school.**
Name one idea your crew tried and rejected, and why it did not work on our robots. Complete one of the two bonus Game Design Document fields. Run a third playtest at the next stage up. Your Open Events program reads a sensor, a line, a vision marker, an armor hit, or a sound, and uses a loop or a variable. Python in the Lab instead of blocks earns the top of this band. Run your game once with a team from outside your section in it. Cover a second crew role for a meeting when someone is absent, and say what you did.

---

## 📝 Deliverables

1. **Game Design Document**, final version, all six required fields
2. **Two playtest logs**: date, who played, what broke, what you changed
3. **Your Open Events program**, the file or a link, plus a short clip of it running hands off
4. **Proof you drove**: a photo or clip from a live match
5. **Reflection** (3 to 5 sentences, each student submits their own): what was your role, what did you actually do, what would you change

---

## 📤 How to Submit

Upload the following to **Schoology**. The Game Design Document and playtest logs are one submission per crew, from whoever your crew designated as Media and Rules. The reflection is individual, every student submits their own.

| # | What to Submit | Who submits it |
|---|---|---|
| 1 | Game Design Document, final version | Crew |
| 2 | Two playtest logs | Crew |
| 3 | Open Events program file or link, plus a clip | Crew |
| 4 | A photo or clip proving you drove | Individual |
| 5 | Your reflection | Individual |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**, not "Create". Create is for typing text and will not let you attach a file.
4. Select your files and click **Submit**

---

## 📋 Grading Rubric (100 points)

Seventy points on the crew's game. Thirty on what you personally did.

**Group, 70 points**

| Category | Points | What I'm looking for |
|---|---|---|
| Research and proposal | 10 | Three real competitions researched, your game proposed and claimed |
| Game Design Document | 30 | All six required fields, final version, complete enough that another crew could run your game without asking you anything |
| Playtesting | 15 | Two playtests with people outside your crew, at least one rule changed because of what happened |
| Running it live | 15 | Your field is set up, you referee, you keep score, you finish on time |

**Individual, 30 points**

| Category | Points | What I'm looking for |
|---|---|---|
| Your lead role | 15 | The three things your role owes, five points each. See the role table above. |
| You drove | 5 | A completed clean driver run in at least one live match |
| You shipped code | 10 | Code you wrote runs on a robot. Blocks are fine. If your crew's own game has no code in it, this is your part of the Open Events entry every crew already owes. |

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **Autonomous** | The robot runs on a program with nobody touching the controls |
| **Driver control** | A person is actively steering the robot with a controller |
| **Playtest** | Having someone who did not write your rules actually play your game, so you find the problems before an audience does |
| **Vision marker** | A printed symbol the robot's camera reads and reacts to |
| **Armor panel** | The six sensors on the S1 that detect a hit |
| **HP** | Hit points, how much damage a robot can take in a battle game before it is out |
| **Iteration** | Writing a rough version of your rules, testing them, then improving them, rather than trying to get them perfect on the first try |
| **Lead role** | The one area of the project you personally own and are graded on, separate from what your whole crew does together |

---

## 💡 Troubleshooting

**"Our game doesn't use any code."**
→ That is fine. Your crew still enters an Open Events autonomous event, which is where the Programmer role and the individual code requirement live.

**"We can't find three real competitions to research."**
→ Start with the RoboMaster University League and DJI's own 2019 S1 Challenge. Find a third yourself, it does not have to involve a RoboMaster.

**"Another crew wants to build the same game as us."**
→ First crew to turn in a claimed proposal keeps the idea. Change yours, or combine two ideas into something new.

**"Our rules fell apart the first time someone else played."**
→ That is Stage 1 working, not failing. Write down what broke and change it. That change is part of your grade.

**"The robot won't connect to the app."**
→ Check with Mr. Krigger before troubleshooting further, robots are activated on a teacher account and reconnecting sometimes needs that account.

**"We're not sure our scoring is actually fair."**
→ Run it past another crew before your final document is due. If two people can read your scoring rule and land on different winners for the same match, it needs a rewrite.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [ ] Every command and version checked against the live source today
- [ ] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [ ] Safety block present, this lesson touches the RoboMaster hardware
- [ ] Base tier is readable by a 7th grader
- [ ] Every placeholder replaced
- [ ] Site version stands alone: points and Schoology steps live here and in Schoology, not on the site
- [ ] Do not post to Schoology or publish the site page until Amali confirms due dates
=========================================================================== -->
