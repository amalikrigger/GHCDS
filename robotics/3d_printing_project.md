<!-- ===========================================================================
TEACHER PLANNING BLOCK. Delete nothing, this never renders on the site.

UNIT / FOLDER   : robotics
FILE NAME       : 3d_printing_project.md
PERIODS         : 4 taught periods, then open build days until every print is done (one period = 60-65 min)
FIRST TAUGHT    : T1 2026, rebuilt 2026-10-12 (the April 2026 original was download or design, print, then a PowerPoint printer guide)
RUNS ALONGSIDE  : another unit. Part of the class is on this while the rest is elsewhere, so "Day 1" means a student's own first printing day, not a calendar date.

PRINTERS
- Formlabs Form 3 / 3+ with Form Wash and Form Cure: LIVE.
- MakerBot Replicator+ with MakerBot Print: ON HOLD until repaired. The track is fully written. To switch it on, change
  data-default and the "on hold" flag on the site page (cs/robotics/3d-printing/index.html), and the On hold line in this file.
- Formlabs plates may run overnight. The MakerBot never runs without an adult in the room.

PREP THE DAY BEFORE
- [ ] Tinkercad Classroom created, class code written on the board. Students join with a nickname: no accounts, no emails.
      Use initials or a first name as the nickname, never a full name plus surname.
- [ ] Lab computers: PreForm installed and signed in on Mr. Krigger's account (students never sign in to Formlabs or MakerBot).
      PreForm checked 2026-10-12: current release 3.63.1 (Sep 25, 2026).
- [ ] A queue folder on the lab computer that runs PreForm: "3D Print Queue" with subfolders Plate 1, Plate 2, Reprints.
- [ ] The paper Print Queue sheet on a clipboard by the printer (columns: plate, file name, initials, height under 25 mm Y/N, status).
- [ ] Resin: cartridge loaded, enough left for a full plate. Read the cartridge label: V4/V4.1 or V5 changes the wash and cure times.
- [ ] Wash station: Form Wash IPA level, hydrometer check (replace at 10% resin), lid closed. IPA 90% or higher.
- [ ] Gloves: nitrile or neoprene, NOT latex, a box at the wash station. Safety glasses at the station and the cutting tray.
- [ ] Flush cutters, part removal tool, paper towels, a marked resin waste container with a lid.
- [ ] Rulers or calipers, and a few real objects for Make It Fit (bottle caps, cables, markers).
- [ ] Printer safety check list for each student (see Lab Safety lesson). Nobody touches a printer, resin or IPA before passing.
- [ ] Test the whole build myself end to end: {{ date }}

TIMING FOR DAY 1 (hands on, safety check, Print 1)
- 10 min  Join the Tinkercad Classroom and build a nameplate. Hands on before any talking.
- 10 min  Two printers, two ways of building. Safety rules out loud.
- 20 min  Printer safety checks at the printer, two or three students at a time, while the rest search for Print 1
- 15 min  Find Print 1, check it fits the 40 x 40 x 25 mm box in Tinkercad, export, drop in Plate 1, sign the sheet
- 5 min   Before you leave
TONIGHT: lay out Plate 1 in PreForm, print overnight.

TIMING FOR DAY 2 (design Print 2)
- 5 min   Start card. Pick a problem.
- 10 min  Talk to the person it is for. Measure. Sketch with numbers.
- 35 min  Build in Tinkercad, design rules check
- 10 min  HS: export the fit test and queue it. Everyone: save.
TONIGHT: Plate 2 if it has enough parts. Otherwise hold for Day 3.

TIMING FOR DAY 3 (finish Print 1, slice and queue Print 2)
- 25 min  Plate 1 post-processing in small groups: wash, dry, cure, supports. Others slice Print 2 in PreForm.
- 25 min  Fit test results (HS), adjust, slice, queue Print 2
- 10 min  Photos of Print 1, start the Print Card

TIMING FOR DAY 4 (test it, version 2, Print Card)
- 20 min  Post-process Print 2, test on the real problem with the real person
- 25 min  Version 2 if needed, or AI Lab, or another lab need
- 15 min  Print Card, photos, exit ticket in Schoology

THE QUEUE, IN ONE LINE
Files in by the end of a student's Day 1 go on the next plate. A resin plate takes the same time whether it holds one part or twenty,
because time depends on height, not count. So: batch, cap height at 25 mm, and run plates overnight. Failed parts go to Reprints,
which goes first on the next plate.

WHERE STUDENTS GET STUCK
- Model downloaded is huge or tiny -> it is in the wrong units. Scale it in Tinkercad and read the dimensions.
- Text does not print -> text thinner than 1 mm or not attached to the base. Raise text 1 mm and overlap it into the base.
- Two parts that should fit do not -> printed holes come out small. Add 0.3 to 0.5 mm. That is what the fit test is for.
- Part fell off supports or never printed -> PreForm printability check was red. Re-run auto supports, or orient at an angle.
- Student waiting for a plate with nothing to do -> Print Card, version 2, AI Lab, or the "things the lab needs" list.

IF THEY FINISH EARLY   : AI Lab (bonus), version 2, a part from the "things the lab needs" list, or a second Stretch. Students who pass the
                         safety check can queue prints for their own projects after this, per the syllabus.
IF THEY NEED MORE TIME : Print 1 plus the Print Card is a passing Base. Print 2 can be a simple measured part with no fit test. The Print
                         Card can be finished at home. Never cut the safety check.

ASSESSMENT
- Category  : Formal Assessments
- Points    : 25
- Exit ticket: 3d_printing_quiz.md, separate Schoology item, 10 points
- Schoology : due Wed Nov 4, 11:59 pm   Section(s): MS 01YR and Comp Sci 01T1
- Draft     : 3d_printing_schoology.md (nothing posted yet)

AFTER TEACHING IT (fill in, this is the most valuable part)
- What ran long  :
- What flopped   :
- Change next time:
=========================================================================== -->

# 🖨️ 3D Printing: Make Something Real

### Print a model, then design and print something that fixes a real problem for a real person

> **Grades:** 7th to 12th &nbsp;|&nbsp; **Time:** 4 class periods, plus open build days while your prints finish &nbsp;|&nbsp; **Difficulty:** Beginner
>
> Somewhere in this building a cable keeps falling behind a desk, a door has no name on it, and a drawer is full of things with nowhere to go. You are going to fix one of them. First you print a model someone else made, so you learn the machine. Then you design your own part, measure it against the real thing, and print it. By the end you hold an object that did not exist last week, and someone is using it.

---

## 🎯 What You'll Learn

- How to **design a 3D model** in Tinkercad from shapes, holes and exact measurements
- How a 3D printer turns your model into an object, **layer by layer**, and why resin and filament printers do it differently
- How to **prepare a print** in the slicer and check it will succeed before it costs an hour of printer time
- How to **finish a resin print safely**: wash, dry, cure, and remove supports
- How to **design for a real person**, test on the real problem, and improve it

---

## 🧰 What You Need

- A lab computer with a web browser
- **Tinkercad**, joined with the class code Mr. Krigger gives you and a nickname. **No account, no email, no password.**
- The lab's printer. Right now that is the **Formlabs Form 3**, a resin printer. The **MakerBot Replicator+** filament printer is **on hold until it is repaired**. Both are written into this lesson, so if it comes back you switch over and keep going.
- A ruler or calipers, and the real object your design has to work with
- Nitrile or neoprene gloves and safety glasses at the wash station. Mr. Krigger has them ready.

**You never sign in to anything.** The printer software on the lab computers is already set up. If a model website asks you to make an account to download, pick a different model or ask Mr. Krigger. Do not make one.

---

## ⚠️ Safety Rules: Read Before You Start

These are non-negotiable. Breaking one on purpose costs you printer access and earns a 0 for the day. Getting access back means retaking the check.

1. **Pass the printer safety check first.** Nobody touches a printer, the resin, the wash or the cure before Mr. Krigger has checked them out. This is the same check from the Lab Safety lesson.
2. **Gloves for anything wet.** Liquid resin, IPA, and any print that has not been washed and cured. **Nitrile or neoprene, never latex.** Resin can soak through latex.
3. **Resin on your skin: wash it off with soap and water, right away.** Never use IPA or hand sanitizer on skin. Then tell Mr. Krigger. Touching resin again and again can make your skin react to it for the rest of your life, which is why gloves are not optional.
4. **Safety glasses** when you handle resin or IPA, and when you clip supports. Supports snap and fly.
5. **IPA is flammable.** Bottles and the Form Wash lid stay closed. Nothing hot and no flame near it.
6. **No food or drink at the print station.**
7. **Resin waste never goes down the sink or in the regular trash.** Paper towels, gloves and failed parts with resin on them go in the marked resin waste container.
8. **Hands out of any printer that is moving.** The MakerBot nozzle runs at about 200°C and the build plate stays hot after a print ends.
9. **Unattended prints:** a Formlabs plate may run overnight under Mr. Krigger's rule. The MakerBot never runs without an adult in the room.
10. **Report spills, damage, a burn smell or an injury right away.** You will never be in trouble for reporting something. You will be for hiding it.

---

## 🗺️ The Plan

| Day | You do | You finish with |
|---|---|---|
| Day 1 | Build a nameplate in Tinkercad, pass the safety check, find **Print 1** | Print 1 in the queue for the next plate |
| Day 2 | Pick a real problem, measure it, design **Print 2** | Print 2 designed. HS: a fit test in the queue. |
| Day 3 | Finish Print 1 (wash, dry, cure, supports). Slice and queue Print 2 | Print 1 in your hand. Print 2 in the queue. |
| Day 4 | Test Print 2 on the real problem, version 2 if needed, Print Card | A part someone uses, and the card that explains it |
| Open build days | Wait for the printer, reprint, AI Lab, finish the card | Everything turned in by the due date |

**What is fixed:** the safety rules, the 40 x 40 x 25 mm size limit, the queue, the due date, and what you turn in. **What moves:** what you design, which problem you fix, and how fast you go. Some of you will be waiting on a plate. That is built in. The waiting work is real work.

---

## 🧾 How the Printer Queue Works

There is one working printer and a lot of you. Here is how everyone gets a print.

- **Every part fits in a 40 x 40 x 25 mm box.** That is about the size of a matchbox standing up.
- **One plate holds a whole class.** On a resin printer, a plate with twenty small parts takes the same time as a plate with one, because the printer builds every part's layer at the same moment. Time depends on how **tall** the tallest part is, not how many parts there are. That is why the height limit matters most.
- **Plates run overnight.** Get your file into the queue by the end of class and it prints that night.
- **To join the queue:** save your STL into the right folder on the PreForm computer, named like this, then write the same name on the Print Queue sheet.

```
HS-JK-print1.stl
```

Section, your initials, which print. No full names.

- **If your print fails,** it goes in the Reprints folder, which always goes first on the next plate. Write down what you think went wrong. That goes on your Print Card.

---

# Day 1: Hands On, Safety, and Print 1

**Goal:** By the end of today you have built something in Tinkercad, passed the printer safety check, and put Print 1 in the queue.

**Start here:** sit at a lab computer, open a browser, and find the class code on the board.

---

### Step 1: Join the class and build a nameplate

1. Go to **tinkercad.com** and click **Log In**.
2. Choose **Students, join your Class**, type the class code from the board, then type your nickname. Use your first name or initials, not your full name.
3. Click **Create**, then **3D Design**.
4. Drag a **Box** onto the blue workplane. Click it, then click the small white squares on its sides to type exact sizes: **40 mm** long, **15 mm** wide, **3 mm** tall.
5. Drag **Text** onto the box. Type your name or a word. Set its height to **2 mm** and lower it so it sits on top of the box and sinks into it a little.
6. Select both (drag a box around them) and click **Group**.

That is a nameplate. You have a 3D model, and it took about ten minutes.

> **✅ Checkpoint:** You have a grouped nameplate, 40 mm long, with raised text.

---

### Step 2: Two printers, two ways to build

Both printers build a shape one thin layer at a time, bottom to top. They do it very differently.

| | **Formlabs Form 3** (resin) | **MakerBot Replicator+** (filament) |
|---|---|---|
| Status | **Live** | **On hold until repaired** |
| Builds with | Liquid resin that a laser hardens | Plastic string (PLA) melted through a hot nozzle |
| How it builds | The part grows **upside down**, pulled up out of a tank of resin | A nozzle draws each layer like a hot glue gun |
| Looks like | Smooth, fine detail | Visible lines, a bit rougher |
| After printing | Wash, dry, cure, clip supports, with gloves | Let it cool, peel it off |
| Software | **PreForm** | **MakerBot Print** |

Your design and your STL file work on both. Only the slicing and the finishing change.

---

### Step 3: The printer safety check

Before you touch a printer, Mr. Krigger checks you out at the machine. It takes a few minutes, in small groups.

- You show where the gloves, the glasses and the resin waste container are.
- You say what you do if resin gets on your skin.
- You show the Form Wash lid closed, and say why IPA stays closed.
- You answer one "what would you do if" question.

You can take it again if you miss something. Pass it once and the printers are yours to use for your own projects for the rest of the year.

> **✅ Checkpoint:** Mr. Krigger has checked you off on the printer safety check.

---

### Step 4: Find Print 1

Print 1 is a model someone else designed. You are learning the machine, not proving you can design yet.

| Site | Good for |
|---|---|
| **Printables** (printables.com) | Clean search, good filters, lots of small useful things |
| **Thingiverse** (thingiverse.com) | The biggest library, a lot of classics |

**Your model must:**
- Fit in **40 x 40 x 25 mm**. You can scale it down, so check it still looks right small.
- Be school appropriate. **No weapons or weapon parts**, even as a joke.
- Be free to download without making an account.
- Come with an **STL** file. Look for a button that says Download or Files.

**Write down the page link and the designer's name.** It goes on your Print Card. Someone made it, and they get the credit.

---

### Step 5: Check it fits, then queue it

1. In Tinkercad, click **Import** and choose the STL you downloaded.
2. Click it and read its size. If it is bigger than 40 x 40 x 25 mm, drag a corner while holding **Shift** to shrink it evenly, or type a smaller size into one box.
3. Make sure it sits flat on the workplane.
4. Click **Export**, then **.STL**.
5. Rename the file like the queue example (`HS-JK-print1.stl`) and save it into the **Plate 1** folder on the PreForm computer.
6. Write the same file name on the Print Queue sheet.

> **✅ Checkpoint:** Your Print 1 file is in the queue folder and on the sheet, under 25 mm tall.

---

### 📝 Before You Leave Today

- [ ] Nameplate built in Tinkercad
- [ ] Printer safety check passed
- [ ] Print 1 found, scaled to fit, exported, in the queue, on the sheet
- [ ] Page link and designer's name written down

---

# Day 2: Design Something That Fixes Something

**Goal:** By the end of today you have a Print 2 design, measured against the real thing it has to work with.

**Start here:** open your Tinkercad class. Print 1 may already be printed. You will finish it on Day 3.

---

### Step 1: Pick a problem

Find something small that bugs somebody. The best problems belong to a real person you can talk to: you, a classmate, a teacher, someone at home.

| Where | Ideas |
|---|---|
| The lab | A clip that keeps a charging cable on the edge of the desk. A label tag for a kit box. A holder for the glue stick that always rolls away. |
| School | A door nameplate for a teacher. A pencil cup for a classroom that needs one. A hook for a bag strap. |
| Home | A spare knob for a drawer. A headphone hook. A hurricane kit tag that says what is inside and when the batteries were changed. |
| Just yours | A keychain for a team, a club, or carnival. A name tag for your water bottle. |

**Ask the person it is for.** Two questions: what is the problem, and what would make it better? Write their answer down. It goes on your Print Card.

---

### Step 2: Measure, then sketch with numbers

A design that is 2 mm off does not fit. Measure the real thing.

1. Measure everything your part touches: how thick is the cable, how wide is the desk edge, how big is the knob's screw hole?
2. Sketch your part on paper. Write every measurement on the sketch.
3. Check it fits the **40 x 40 x 25 mm** box.

> **✅ Checkpoint:** A sketch with at least three measurements written on it.

---

### Step 3: Build it in Tinkercad

| Move | How |
|---|---|
| Exact size | Click a shape, then click a white handle and type the number |
| Make a hole | Click a shape, then click **Hole** in the shape panel. Group it with a solid shape to cut it out. |
| Line things up | Select two shapes, click **Align**, then click the dots to line them up |
| Move up or down | Drag the black cone on top of a shape |
| Combine | Select shapes, click **Group** |
| Snap Grid | Bottom right. Set it to **0.5 mm** for small parts. |

Build it a piece at a time, and measure in Tinkercad against your sketch as you go.

---

### Step 4: Design rules for printing

| Rule | Why |
|---|---|
| Walls at least **1.5 mm** thick | Thinner walls snap |
| Raised or sunken text at least **1 mm** deep | Thinner text disappears |
| Holes and slots **0.3 to 0.5 mm bigger** than the thing that goes in | Printed holes come out a little small |
| A flat side for the bottom | Easier to print on both printers |
| Nothing taller than **25 mm** | The queue height limit |
| Pieces touch or overlap | Loose pieces print as separate bits, or not at all |

> **✅ Checkpoint:** Your design follows every rule in the table. Check each one.

**High school: make a fit test.** Before you print the whole part, cut out just the piece that has to fit (the slot, the hole, the clip) as a tiny test, under 10 mm tall. Export it as `HS-JK-fittest.stl` and queue it. It prints fast and tells you if your measurements are right before you spend a full print on them.

---

### 📝 Before You Leave Today

- [ ] A real problem, and what the person it is for said
- [ ] A sketch with measurements
- [ ] Print 2 designed in Tinkercad, following the design rules
- [ ] HS: fit test exported and in the queue

---

# Day 3: Finish Print 1, Queue Print 2

**Goal:** By the end of today Print 1 is finished and in your hand, and Print 2 is in the queue.

**Start here:** check the Print Queue sheet. If your Print 1 is printed, you start at the wash station with Mr. Krigger. If not, start with Print 2.

> **Printer tracks.** Every step below has a Formlabs version (live) and a MakerBot version (on hold until repaired). Follow the one for the printer your print is on.

---

### Step 1: Slice Print 2

#### Formlabs track (live): PreForm

1. On the PreForm computer, open **PreForm**. It is already signed in. Do not sign in with your own account.
2. **File > Open** and choose your Print 2 STL.
3. Check the printer says **Form 3** (or Form 3+) and the material matches the cartridge in the printer. Use the layer height Mr. Krigger has set.
4. Click **Orient**, then **Auto-Orient**.
5. Click **Supports**, then **Auto-Generate**.
6. Look at the **Printability** check. Green means good. Red means a part will not print. Try Auto-Orient again, or tilt the part yourself.
7. Take a **screenshot** of your part on the build platform with its supports. It goes on your Print Card.
8. Save your STL into the next plate's queue folder and write it on the sheet. Mr. Krigger lays the whole plate out and starts it.

#### MakerBot track (on hold until the printer is repaired): MakerBot Print

1. On the lab computer, open **MakerBot Print**. It is already signed in.
2. Check the printer is the **Replicator+**.
3. Click **Add Models** and choose your STL.
4. Click **Arrange** to put it in the middle of the plate, flat side down.
5. Open **Print Settings**: Balanced, **Raft on**, **Supports on** if anything hangs out in the air.
6. Click **Preview**. Read the print time. **It must be under 60 minutes.** If it is longer, make it smaller.
7. Take a **screenshot** of the preview. It goes on your Print Card.
8. Click **Export**, save the `.makerbot` file to the class USB stick, and give it to Mr. Krigger. He starts it and an adult stays in the room the whole time.

> **✅ Checkpoint:** A slicer screenshot, and Print 2 in the queue.

---

### Step 2: Finish Print 1

#### Formlabs track (live): wash, dry, cure, clip

**Gloves and safety glasses on first.** Everything here is wet with resin until the cure is done.

1. **Remove the build platform** from the printer and hold it over a paper towel, parts up.
2. **Wash.** Put the platform in the **Form Wash** and close the lid. Set the time for the resin on the cartridge label:

| Resin on the label | Wash time |
|---|---|
| Grey, White, Black or Clear **V5** | **5 minutes** |
| Grey, White, Black or Clear **V4 or V4.1** | **10 minutes** |

3. **Dry.** When the Form Wash lifts the basket out, let the parts air dry completely. Wet IPA under the cure light leaves a sticky, white surface.
4. **Remove the parts** from the platform with the part removal tool. Push away from your other hand.
5. **Cure.** Put the parts in the **Form Cure**, choose the resin on its screen, and use the setting it shows. For V5 standard resin that is 5 minutes with no heat. For V4 it is longer and heated, so let the screen tell you.
6. **Clip the supports** with flush cutters, glasses on, pointing away from people. Sand the small bumps if you want.
7. Gloves, paper towels and support bits go in the **resin waste container**. Close the IPA and the Form Wash lid.

#### MakerBot track (on hold until the printer is repaired): cool and peel

1. **Wait** for the build plate to cool. The screen tells you when the print is done. The plate is still hot.
2. Lift out the flexible build plate and **bend it gently**. The print pops loose.
3. Peel off the raft and any supports with your fingers or pliers.
4. Put the plate back, level and clean, for the next person.

> **✅ Checkpoint:** Print 1 is finished and in your hand. Take a photo of it.

---

### 🧠 Mini Lesson: Why the resin part grows upside down

A resin printer has a tank with a clear bottom. A laser draws one layer of your part on the bottom of the tank, and the light turns that thin layer of liquid into solid plastic. The build platform lifts a tiny bit, fresh resin flows in underneath, and the laser draws the next layer. Thousands of times. Your part hangs upside down from the platform the whole time, and the supports are what hold it there. That is why the supports matter, and why a part with no supports falls into the tank.

---

### 📝 Before You Leave Today

- [ ] Print 1 washed, dried, cured, clipped, and photographed
- [ ] Print 2 sliced, with a screenshot
- [ ] Print 2 in the queue and on the sheet
- [ ] Station clean: gloves in the waste, IPA closed, lid down

---

# Day 4: Test It, Fix It, Show It

**Goal:** By the end of today your Print 2 has been tried on the real problem, and your Print Card is filled in.

**Start here:** collect Print 2 from the plate and finish it the same way as Print 1 (Day 3, Step 2).

---

### Step 1: Test it on the real problem

Take your part to the real thing. Does the clip hold the cable? Does the tag fit the box? Give it to the person it is for and watch them use it. Do not explain it to them first. If they can not tell how it works, that is information too.

---

### Step 2: Version 2, if it needs one

Most real designs need a second try. That is not failing, that is how designing works.

| What happened | Try this |
|---|---|
| Too tight | Make the hole or slot 0.3 mm bigger |
| Too loose | Make it 0.3 mm smaller |
| It snapped | Thicker walls, or round the sharp inside corners |
| It works but looks rough | Fine. A part that works beats a part that looks nice. |

**Change one thing at a time.** Then you know which change fixed it. Version 2 goes in the queue like any other print.

---

### Step 3: Fill in your Print Card

The Print Card is one page about your print, like the card next to an object in a museum. It answers: what is this, who is it for, and how did it get made.

| Box | What goes in it |
|---|---|
| **The problem** | What was wrong, in one or two sentences |
| **Who it is for** | The person, and what they told you |
| **My design** | A Tinkercad screenshot, and one sentence about how it works |
| **Measurements** | The numbers that matter, and how you chose them |
| **The print** | Slicer screenshot, which printer, print time |
| **What went wrong, what I changed** | Every problem, and what you did about it |
| **Print 1** | Its name, the link, and the designer's name |
| **Photo** | Print 2 in use, solving the problem |
| **AI used?** | Yes or no, and for what (only if you did the AI Lab) |

Write it in a Google Doc or on paper, then turn it into a PDF or a clear photo.

---

### While You Wait: Open Build Days

Waiting for a plate is normal. Here is what to do.

- **Finish your Print Card.** Most people underestimate this.
- **Version 2.** If Print 2 is not perfect, improve it.
- **AI Lab** (below). Bonus, optional.
- **Things the lab needs.** Ask Mr. Krigger for the list. A part that gets used every day in this room is a good part.

### If Your Print Failed

1. Look at what came out (or did not) and write down what you think went wrong.
2. Check the design rules and the Printability check, fix it, and put it in the **Reprints** folder. Reprints go first on the next plate.
3. **If it fails twice for a reason that is not your design**, your STL, your slicer screenshot and a photo of the failure count as your print. Tell Mr. Krigger.

---

## 🤖 AI Lab (Optional Bonus)

AI is useful for design if you stay the designer. This is extra, for anyone who wants it, and never instead of your own Print 2 work.

**Rules:**
- Use only an AI tool on your **school** account that Mr. Krigger has approved. Do not make a personal account for this. Many AI tools need you to be 18, or 13 with a parent's permission.
- Never type your name or anyone's personal information into it.
- You must be able to **explain every line or step** it gave you. If you can not explain it, it is not yours.
- Say on your Print Card that you used AI and what for.

### Route A: AI writes code that builds a model

**OpenSCAD** is a free program where you build models by typing code instead of dragging shapes. An AI can write that code for you. Your job is to read it, change it, and make it right.

1. Ask the AI for OpenSCAD code. Be exact: say the size in millimeters, the shape, the holes, the limit of 40 x 40 x 25 mm.
2. Paste the code into OpenSCAD. Press **F5** to preview it.
3. **Change one number yourself** and preview again. Can you predict what will happen?
4. Press **F6** to render it, then **File > Export > Export as STL**.

Here is what OpenSCAD code looks like. This makes a 40 mm key tag with a hole and raised letters.

```openscad
// Key tag: 40 x 20 x 3 mm, a 5 mm hole, raised letters 1 mm tall
difference() {
  cube([40, 20, 3]);
  translate([6, 10, -1]) cylinder(h = 5, d = 5, $fn = 40);
}
translate([12, 6, 3]) linear_extrude(1) text("VI", size = 8);
```

### Route B: AI as a step by step coach

Ask an AI to walk you through building your own idea in Tinkercad, one step at a time. You do every click. Ask it "why" at every step. This route is about learning a move you did not know, not about getting a file.

---

## 🎚️ Base and Stretch

**Base: everyone does this.**
**Print 1:** a downloaded model, scaled to fit, printed and finished, with credit to its designer. **Print 2:** your own Tinkercad design that fixes a real problem for a real person, measured and printed. **Print Card** filled in.

**Stretch: required for high school, bonus for middle school.**
**Make It Fit.** Print 2 has to fit or attach to a real object you measured: a cable, a bottle, a desk edge, a box. Print a **fit test** first. Then print a **version 2** that changes at least one measurement because of what the fit test or the first print showed you. Your Print Card shows the numbers before and after.

---

## 📝 Deliverables

1. **The objects.** Print 1 and Print 2, shown to Mr. Krigger in class.
2. **Print 2's STL file.**
3. **Your Print Card**, as a PDF or a clear photo, with a photo of Print 2 in use.
4. **If you did the Stretch:** the fit test and version 2 numbers on the card.
5. **If you did the AI Lab:** the STL or a screenshot of your OpenSCAD code, and the AI line on your card.

There is no slide deck and no printer guide. The objects and the card are the work.

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Submit |
|---|---|
| 1 | Your Print Card (PDF or photo) |
| 2 | Print 2's STL file |
| 3 | A photo of Print 2 in use (on the card or as its own file) |
| 4 | AI Lab only: your OpenSCAD code screenshot or STL |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**. Do **NOT** click "Create" (Create is for text only and will not let you attach files)
4. Select your files and click **Submit**

Print 1 and Print 2 themselves are shown to Mr. Krigger in class. The **exit ticket** is a separate Schoology item, taken in class. Both have to be done.

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| The Objects | 10 | Print 1 printed and finished (3). Print 2 printed, finished, and it works on the real problem (7). A print that failed twice for a reason that is not your design counts when the STL, the slicer screenshot and a failure photo are submitted. |
| Design Choices | 5 | Print 2 is your own design, measured against the real thing, follows the design rules, fits the 40 x 40 x 25 mm box |
| Print Card | 5 | Every box filled in. The "what went wrong" box shows real thinking, not "nothing". Print 1's designer is credited. |
| Safety and Workflow | 5 | Passed the safety check, gloves and glasses every time, station left clean, files named and queued correctly |

**Bonus:**
- **+3 points** for a middle school student who completes Make It Fit (required of high school students)
- **+2 points** for the AI Lab, when you can explain every line or step on request
- **+2 points** for a part from the "things the lab needs" list that ends up in daily use

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **STL** | The standard 3D printing file. It describes the outside surface of your shape. |
| **Slicer** | Software that cuts your model into layers and tells the printer how to build each one. PreForm and MakerBot Print are slicers. |
| **Layer height** | How thick each layer is. Thinner is smoother and slower. |
| **Resin** | The liquid a Formlabs printer builds from. Light turns it solid. |
| **Filament** | The plastic string a MakerBot melts to build with. Ours is PLA. |
| **Supports** | Thin temporary struts that hold a part up while it prints. You clip them off after. |
| **Overhang** | A part of the model that sticks out over nothing. It needs supports. |
| **Raft** | A flat layer the MakerBot prints first, under your part, so it sticks to the plate |
| **IPA** | Isopropyl alcohol. It washes liquid resin off a print. Flammable. |
| **Cure** | Light and gentle heat that finish hardening a resin print |
| **Tolerance** | The small gap you leave so two parts fit together |
| **Fit test** | A tiny print of just the part that has to fit, to check your measurements cheaply |
| **Iteration** | Test, change one thing, test again |

---

## 💡 Troubleshooting

**"The model I downloaded is enormous, or almost invisible."**
→ It was made in different units. In Tinkercad, read its size and scale it until the numbers are right.

**"A website wants me to sign up before I can download."**
→ Pick a different model, or ask Mr. Krigger. Do not make an account.

**"My text did not print."**
→ It was thinner than 1 mm, or it was floating above the base instead of sinking into it. Make it 1 mm or more and overlap it into the part.

**"PreForm says my part will not print (red)."**
→ Run Auto-Orient and Auto-Generate supports again. If it is still red, tilt the part by hand so no big flat face points straight down.

**"My resin part has a sticky or white surface."**
→ It went into the cure while still wet with IPA, or the IPA in the wash is old. Tell Mr. Krigger. Let the next part dry fully first.

**"My resin part is soft or bends."**
→ It was not cured, or the cure was too short. Check the setting on the Form Cure screen for your resin.

**"Two parts that should fit do not."**
→ Printed holes come out a little small. Make the hole 0.3 to 0.5 mm bigger. That is exactly what the fit test is for.

**"Resin got on my skin."**
→ Wash it with soap and water straight away. Never IPA or hand sanitizer. Then tell Mr. Krigger.

**"I spilled resin or IPA."**
→ Step back, tell Mr. Krigger, and keep gloves on. Do not wipe it with bare hands. Used paper towels go in the resin waste container.

**"MakerBot (when it is back): the print is not sticking to the plate."**
→ The plate may be dirty or not level, or the raft is off. Tell Mr. Krigger. Do not reach in while it moves.

**"MakerBot (when it is back): the print time is over 60 minutes."**
→ Make the part smaller, or lower the infill, or check you did not leave something huge on the plate.

<!-- ===========================================================================
BEFORE YOU CALL IT DONE
- [ ] PreForm and MakerBot Print button names checked on the real lab computers (written from vendor docs and school guides, 2026-10-12)
- [ ] Wash and cure times checked against the cartridge label and the Form Cure screen
- [ ] Tinkercad "Students, join your Class" wording checked on the live site
- [ ] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [ ] Every checkpoint is something a student can actually see
- [ ] Base tier is readable by a 7th grader
- [ ] Safety block present
- [ ] Site version stands alone: rubric and Schoology steps stay in this file
=========================================================================== -->
