<!-- ===========================================================================
TEACHER PLANNING BLOCK. Delete nothing, this never renders on the site.

UNIT / FOLDER   : robotics
FILE NAME       : 3d_printing_project.md
PERIODS         : 4 taught periods, then open build days until every print is done (one period = 60-65 min)
FIRST TAUGHT    : T1 2026. Rebuilt 2026-10-12, revised 2026-10-19 (two prints total, Formlabs and MakerBot tabs, printer care,
                  bonus challenges). The April 2026 original was download or design, print, then a PowerPoint printer guide.
RUNS ALONGSIDE  : another unit. Part of the class is on this while the rest is elsewhere, so "Day 1" means a student's own first
                  printing day, not a calendar date.

PRINTERS (students pick one; each has its own tab on the site page and its own Day 3 section here)
- Formlabs Form 3 / 3+ with Form Wash and Form Cure. PreForm is on ONE lab computer. Plates may run overnight.
- MakerBot Replicator+. MakerBot Print signs in with an UltiMaker account: Mr. Krigger's, signed in on the lab computer. Students do not
  make UltiMaker accounts (UltiMaker treats under-16s as children and needs signed parental consent first). The printer reads a
  .makerbot file from a flash drive, not an STL. Never runs without an adult in the room.

PREP THE DAY BEFORE
- [ ] Tinkercad Classroom created, class code on the board. Students join with a nickname: no accounts, no emails.
- [ ] PreForm computer and the MakerBot Print computer both signed in on my accounts.
- [ ] "3D Print Queue" folder on the PreForm computer, and the class flash drive for the MakerBot.
- [ ] The paper Print Queue sheet (columns: printer, file name, initials, height under 25 mm Y/N, status).
- [ ] Formlabs: cartridge shaken and seated, vent cap open, tank matches the cartridge, no cured bits in the tank, platform clean.
      Read the cartridge label (V4/V4.1 or V5): it sets the wash and cure times.
- [ ] Form Wash IPA level and hydrometer check (replace at 10% resin). IPA 90% or higher.
- [ ] Gloves (nitrile or neoprene, NOT latex), safety glasses, flush cutters, part removal tool, platform scraper, plastic tank tool,
      paper towels, a lidded resin waste container.
- [ ] MakerBot: filament loaded, flexible build plate clean.
- [ ] Printer safety check list for each student. Nobody touches a printer, resin or IPA before passing.
- [ ] Test the whole build myself end to end on both printers: {{ date }}

TIMING FOR DAY 1 (hands on, safety check, Print 1)
- 10 min  Tinkercad nameplate. Hands on before any talking.
- 10 min  Two printers, two ways of building. Pick a printer. Safety rules out loud.
- 20 min  Printer safety checks at the printers, a few at a time, while the rest search for Print 1
- 15 min  Find Print 1, check it fits 40 x 40 x 25 mm in Tinkercad, export, save (Plate folder or flash drive), sign the sheet
- 5 min   Before you leave

TIMING FOR DAY 2 (design Print 2)
- 5 min   Choose: keep it simple (nameplate), level up, or fix a problem
- 10 min  Measure and sketch with numbers
- 35 min  Build in Tinkercad, design rules check
- 10 min  Export, save, sign the sheet

TIMING FOR DAY 3 (printer tab: slice, set up, print, finish)
- 15 min  Slice in PreForm or MakerBot Print, screenshots
- 15 min  Before-every-print checks (Formlabs) or start a print and watch the first layers (MakerBot)
- 25 min  Finish Print 1: wash, dry, cure, clip (Formlabs) or cool and peel (MakerBot). Leave the printer ready.
- 5 min   Photos, before you leave

TIMING FOR DAY 4 (finish and Print Card)
- 15 min  Finish Print 2, photos
- 30 min  Print Card
- 15 min  Exit ticket in Schoology, bonus challenges for anyone done

WHERE STUDENTS GET STUCK
- Model downloaded is huge or tiny -> wrong units. Scale it in Tinkercad and read the dimensions.
- MakerWorld gives a 3MF -> download the STL from the files list, or pick another model.
- Text does not print -> thinner than 1 mm or floating. Raise text 1 mm and overlap it into the base.
- MakerBot screen does not show the file -> they copied the STL, not the .makerbot, or it is inside a folder.
- Resin part sticky after drying -> old IPA. Rewash right away in clean IPA, dry, cure.
- Waiting with nothing to do -> Print Card, bonus challenges, help someone whose print failed.

IF THEY FINISH EARLY   : Bonus challenges (real-world test, Make It Fit, AI Lab). Students who pass the safety check can print their own
                         projects after this, per the syllabus.
IF THEY NEED MORE TIME : Print 2 as a plain nameplate is a passing Base. The Print Card can be finished at home. Never cut the safety check.

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

### Print a model you find, then design and print one of your own

> **Grades:** 7th to 12th &nbsp;|&nbsp; **Time:** 4 class periods, plus open build days while your prints finish &nbsp;|&nbsp; **Difficulty:** Beginner
>
> Two prints, two ways of getting a 3D model. First you find a model someone else made and print it, so you learn the machine. Then you design your own in Tinkercad and print that. Keep it simple with a nameplate, or go further and design something that fixes a real problem. Either way you finish holding two objects that did not exist last week, and one of them is all yours.

---

## 🎯 What You'll Learn

- How to **find a model**, check it will print, and give its designer credit
- How to **design a 3D model** in Tinkercad from shapes, holes and exact measurements
- How a printer turns your model into an object **layer by layer**, and why resin and filament printers do it differently
- How to **run a printer properly**: slice the file, set up the machine, finish the print, and leave it ready for the next person

---

## 🧰 What You Need

- A lab computer with a web browser
- **Tinkercad**, joined with the class code Mr. Krigger gives you and a nickname. **No account, no email, no password.**
- One of the lab's two printers, your pick: the **Formlabs Form 3** (resin) or the **MakerBot Replicator+** (filament). Check with Mr. Krigger which is running today. If yours is down, switch. Your STL does not change.
- For the MakerBot: the class **flash drive**
- A ruler or calipers
- Nitrile or neoprene gloves and safety glasses at the Formlabs wash station

**You never sign in to anything.** PreForm (on one lab computer) and MakerBot Print are already signed in on Mr. Krigger's accounts. Do not make an account on any model website.

---

## ⚠️ Safety Rules: Read Before You Start

These are non-negotiable. Breaking one on purpose costs you printer access and earns a 0 for the day. Getting access back means retaking the check.

1. **Pass the printer safety check first.** Nobody touches a printer, the resin, the wash or the cure before Mr. Krigger has checked them out.
2. **Gloves for anything wet.** Liquid resin, IPA, and any print that has not been washed and cured. **Nitrile or neoprene, never latex.**
3. **Resin on your skin: wash it off with soap and water, right away.** Never IPA or hand sanitizer. Then tell Mr. Krigger. Touching resin again and again can make your skin react to it for the rest of your life.
4. **Safety glasses** when you handle resin or IPA, and when you clip supports. Supports snap and fly.
5. **IPA is flammable.** Bottles and the Form Wash lid stay closed. Nothing hot and no flame near it.
6. **No food or drink at the print station.**
7. **Resin waste never goes down the sink or in the regular trash.** It goes in the marked resin waste container.
8. **Hands out of any printer that is moving.** The MakerBot nozzle runs at about 200°C and the build plate stays hot after a print ends.
9. **Unattended prints:** a Formlabs plate may run overnight under Mr. Krigger's rule. The MakerBot never runs without an adult in the room.
10. **Report spills, damage, a burn smell or an injury right away.** You will never be in trouble for reporting something. You will be for hiding it.

---

## 🗺️ The Plan: Two Prints

| Day | You do | You finish with |
|---|---|---|
| Day 1 | Build a nameplate in Tinkercad, pass the safety check, find **Print 1** | Print 1 ready to print |
| Day 2 | Design **Print 2**: your nameplate, or something that fixes a problem | Print 2 ready to print |
| Day 3 | Your printer's track, **Formlabs** or **MakerBot**: slice, print, finish | Print 1 in your hand |
| Day 4 | Finish Print 2, fill in the Print Card, try a bonus | Both prints, and the card |
| Open build days | Wait for the printer, reprint, bonus challenges | Everything turned in by the due date |

**What is fixed:** two prints, the safety rules, the 40 x 40 x 25 mm size limit, the queue, the due date, and what you turn in. **What moves:** what you print, which printer, and how far you take your own design.

---

## 🧾 How the Printer Queue Works

- **Every part fits in a 40 x 40 x 25 mm box.** About the size of a matchbox standing up.
- **Formlabs: one plate holds a whole class.** It builds every part's layer at the same moment, so twenty short parts take about as long as one. Time depends on the **tallest** part. Plates run overnight.
- **MakerBot: one part at a time**, under 60 minutes, only while an adult is in the room.
- **Failed prints** go first next time.
- Name every file like this, and write the same name on the Print Queue sheet:

```
HS-JK-print1.stl
```

Section, your initials, which print. No full names.

---

# Day 1: Hands On, Safety, and Print 1

**Goal:** By the end of today you have built a nameplate in Tinkercad, passed the printer safety check, and found Print 1.

---

### Step 1: Build a nameplate

1. Go to **tinkercad.com** and click **Log In**. Choose **Students, join your Class**, type the class code, then your nickname: first name or initials, never your full name.
2. Click **Create**, then **3D Design**.
3. Drag a **Box** onto the blue workplane. Click the white squares on its sides and type: **40** mm long, **15** mm wide, **3** mm tall.
4. Drag **Text** onto the box. Make it **2 mm** tall and sink it a little into the box.
5. Select both and click **Group**.

> **✅ Checkpoint:** A grouped nameplate, 40 mm long, with raised text. Keep it. It can become your Print 2 tomorrow.

---

### Step 2: Two printers, two ways to build

| | **Formlabs Form 3** (resin) | **MakerBot Replicator+** (filament) |
|---|---|---|
| Builds with | Liquid resin that a laser turns solid | Plastic string (PLA) melted through a hot nozzle |
| How | The part grows upside down, lifted out of a tank | A nozzle draws each layer like a hot glue gun |
| Looks like | Smooth, fine detail | Visible lines, a bit rougher |
| After printing | Wash, dry, cure, clip supports, with gloves | Let it cool, peel it off |
| Software | PreForm, on one lab computer | MakerBot Print, then a flash drive |

---

### Step 3: The printer safety check

Mr. Krigger checks you out at the machine, a few at a time. You show where the gloves, glasses and resin waste container are; say what you do if resin gets on your skin; show the Form Wash lid closed and say why IPA stays closed; and show where your hands stay while the MakerBot moves. Miss something and you take it again.

> **✅ Checkpoint:** Mr. Krigger has checked you off.

---

### Step 4: Find Print 1

| Site | Good for |
|---|---|
| **Printables** (printables.com) | Clean search, good filters, lots of small useful things |
| **Thingiverse** (thingiverse.com) | The biggest library, plenty of classics |
| **MakerWorld** (makerworld.com) | Lots of new, popular models. Download the **STL**, not a 3MF made for another brand of printer. |

**Your model must:** fit in **40 x 40 x 25 mm** (you can shrink it), be school appropriate with **no weapons or weapon parts**, and download as an **STL** without making an account.

**Write down the page link and the designer's name.** It goes on your Print Card.

---

### Step 5: Check it fits, then save it

1. In Tinkercad, click **Import** and choose the STL.
2. Read its size. Too big? Hold **Shift** and drag a corner to shrink it evenly.
3. Make sure it sits flat, then **Export**, **.STL**.
4. Rename it like `HS-JK-print1.stl`.
5. **Formlabs:** save it in the Plate folder on the PreForm computer. **MakerBot:** save it to the class flash drive. Write it on the Print Queue sheet.

---

### 📝 Before You Leave Today

- [ ] Nameplate built in Tinkercad
- [ ] Printer safety check passed
- [ ] Print 1 found, shrunk to fit, exported, saved, and on the sheet
- [ ] Page link and designer's name written down

---

# Day 2: Design Print 2

**Goal:** By the end of today your own design is finished, checked against the design rules, and saved for printing.

---

### Step 1: Choose your Print 2

| Choice | What it is | Who |
|---|---|---|
| **Keep it simple** | Finish your nameplate from Day 1 | Middle school base |
| **Level up** | A nameplate with at least **two** extra features: a keyring hole, a stand, sunken text, a cut-out shape, a border | HS minimum. MS bonus. |
| **Fix a problem** | Something useful: a cable clip, a headphone hook, a drawer knob, a hurricane kit tag | Anyone. Counts as Level up. |

Fixing a problem? Ask the person it is for what bugs them and what would make it better. Write it down for your Print Card.

---

### Step 2: Measure, then sketch with numbers

1. **Nameplate:** decide how big it is and where it goes. **Fixing a problem:** measure everything your part touches.
2. Sketch your part and write every measurement on the sketch.
3. Check it fits the **40 x 40 x 25 mm** box.

> **✅ Checkpoint:** A sketch with at least three measurements.

---

### Step 3: Build it in Tinkercad

| Move | How |
|---|---|
| Exact size | Click a shape, click a white handle, type the number |
| Make a hole | Click a shape, then **Hole**. Group it with a solid shape to cut it out. |
| Line things up | Select two shapes, click **Align**, then click the dots |
| Move up or down | Drag the small black cone on top of a shape |
| Combine | Select the shapes, click **Group** |
| Fine control | Set **Snap Grid** to **0.5 mm** |

---

### Step 4: Design rules, then save it

| Rule | Why |
|---|---|
| Walls at least **1.5 mm** thick | Thinner walls snap |
| Text at least **1 mm** raised or sunk | Thinner text disappears |
| Holes **0.3 to 0.5 mm bigger** than what goes in | Printed holes come out a little small |
| A flat bottom, nothing taller than **25 mm** | Prints cleanly, fits the queue |
| Every piece touches or overlaps | Loose pieces print as separate bits |

Export as `HS-JK-print2.stl` and save it the same way as Print 1.

---

### 📝 Before You Leave Today

- [ ] Print 2 chosen: keep it simple, level up, or fix a problem
- [ ] A sketch with measurements
- [ ] Print 2 designed, passing every design rule
- [ ] Print 2 exported, saved, and on the sheet

---

# Day 3: Slice, Print, Finish

**Pick your track.** Follow the section for the printer you picked. On the site, each printer has its own tab at the top of the page.

---

## Formlabs Track

### Step 1: Slice in PreForm

1. PreForm is on **one** lab computer, already signed in. Do not sign in with your own account.
2. **File > Open** and choose your STL.
3. Check the printer says **Form 3** and the material matches the cartridge.
4. **Orient > Auto-Orient**, then **Supports > Auto-Generate**.
5. Check **Printability**. Green is good. Red: Auto-Orient again, or tilt the part yourself.
6. **Screenshot** your part with its supports for the Print Card.
7. Mr. Krigger puts the whole class on one plate and starts it.

### Step 2: Before every print

Check these with Mr. Krigger before a plate starts:

- **Cartridge:** shaken well, the right resin, pushed down level with the back of the printer, **vent cap pressed open**. Never pull the rubber valve off the bottom.
- **Tank:** the same resin as the cartridge, clicked into its rails, no cured bits, mixer at its home on the left.
- **Build platform:** clean, pushed in, handle locked down.
- **Cover** closed.

### Step 3: Wash and dry

**Gloves and safety glasses on first.**

1. Remove the build platform and hold it over a paper towel, parts up.
2. **Wash once** in the Form Wash, lid closed:

| Resin on the label | Wash time |
|---|---|
| Grey, White, Black or Clear **V5** | **5 minutes** |
| Grey, White, Black or Clear **V4 or V4.1** | **10 minutes** |

3. **Dry** completely in the air.
4. **Still sticky once dry?** Wash again straight away in **clean** IPA. Sticky usually means the wash IPA is old.

### Step 4: Remove, cure, clip

1. Remove the parts with the part removal tool, pushing away from your other hand.
2. **Cure** in the Form Cure:

| Resin on the label | Cure |
|---|---|
| Grey, White, Black or Clear **V5** | **1 minute, no heat**. Stronger: 5 minutes at 60°C. |
| Grey, White or Black **V4 or V4.1** | **10 minutes at 60°C** |
| Clear **V4 or V4.1** | **5 to 7 minutes at 60°C** |

3. Clip the supports with flush cutters, glasses on, pointing away from people.

### Step 5: Leave it ready for the next person

1. **Clean the build platform:** scrape off cured resin with the platform scraper over a paper towel, then wipe with IPA.
2. **Close the cartridge vent cap** when the printer is done for the day.
3. **Check the tank** for cured bits and tell Mr. Krigger. Only the **plastic tank tool** touches the tank. Metal scratches the film and ruins the tank.
4. A tank out of the printer goes in its case with the lid on, out of the light.
5. Waste in the resin waste container. IPA and Form Wash lid closed.

Changing the resin or the tank is done with Mr. Krigger. The resin in the tank must always match the cartridge.

---

## MakerBot Track

### Step 1: Slice in MakerBot Print

1. Open **MakerBot Print**. It is signed in on Mr. Krigger's UltiMaker account. Do not sign in or make an account.
2. Check the printer is the **Replicator+**.
3. **Add Models**, choose your STL from the flash drive, then **Arrange**, flat side down.
4. **Print Settings:** Balanced, **Raft on**, **Supports on** if anything hangs in the air.
5. **Preview.** Under 60 minutes, or make it smaller. **Screenshot** it for the Print Card.
6. **Export** the `.makerbot` file to the flash drive, at the top level, not inside a folder.

The printer cannot read an STL. It reads the `.makerbot` file.

### Step 2: Print it

1. With Mr. Krigger there, plug the flash drive into the printer.
2. Tap **Print > USB Storage**, your `.makerbot` file, then **Print**.
3. **Watch the first few layers.** If the plastic curls or drags, tell Mr. Krigger to stop it.
4. An adult stays in the room until it finishes. Hands out while it moves.

### Step 3: Take it off the plate

1. Wait for the screen to say it is done, then for the plate to cool.
2. Lift out the flexible build plate and bend it gently. The print pops loose.
3. Peel off the raft and supports. Glasses on if you use pliers.
4. Brush plastic bits off the plate and put it back.

### Step 4: Changing the filament (with Mr. Krigger)

**Unload:** tap **Filament > Unload Filament**, wait for it to heat, then pull the filament gently out of the extruder and the tube and take the spool off.

**Load:** tap **Filament > Load Filament**, wait for it to heat, put the spool on, feed the end through the tube, and push it into the extruder until it grabs. When plastic comes out of the nozzle, tap **Done**. Will not go in? Cut the end at an angle and try again.

---

### 📝 Before You Leave Today

- [ ] Both prints sliced, with screenshots
- [ ] Print 1 finished and photographed
- [ ] The printer left ready for the next person

---

# Day 4: Finish It and Show It

**Goal:** Both prints are finished, and your Print Card is filled in.

### Step 1: Finish Print 2

Finish it the same way as Print 1, in your printer's track. Photograph both prints.

### Step 2: Fill in your Print Card

| Box | What goes in it |
|---|---|
| **Print 1** | Its name, the link, the designer's name, and a photo |
| **Print 2: what it is** | Which choice you made, and why. Fixing a problem? Who it is for. |
| **My design** | A Tinkercad screenshot, and one sentence on how you built it |
| **Measurements** | The numbers that matter, and how you chose them |
| **The prints** | Slicer screenshots, which printer, print times |
| **What went wrong, what I changed** | Every problem, and what you did about it |
| **Photo** | Print 2, finished |

Template: `3d_print_card_template.md`. Write it in a Google Doc or on paper, then make it a PDF or take a clear photo.

### If your print failed

Write down what you think went wrong, fix it, and tell Mr. Krigger. Failed prints go first next time. **Failed twice for a reason that is not your design?** Your STL, your slicer screenshot and a photo of the failure count as your print.

---

## ⭐ Bonus Challenges (optional, not turned in)

Each one you finish and show Mr. Krigger earns bonus points.

| Bonus | What you do |
|---|---|
| **Real-world test** | Your fix-a-problem part goes to the real problem. Hand it to the person it is for and watch them use it. Tell Mr. Krigger how it went. |
| **Make It Fit** | A part that fits a real object you measured. Print a tiny fit test first, then a version 2 that changes at least one measurement. |
| **AI Lab** | Use AI to write OpenSCAD code for a model, or to coach you through a new Tinkercad move |

### AI Lab rules

- Only an AI tool on your **school** account that Mr. Krigger has approved. No personal accounts.
- Never type your name or anyone's personal information into it.
- You must be able to **explain every line or step**.

**Route A: AI writes the code.** OpenSCAD is a free program where you build a model by typing code. Paste the AI's code in, press **F5** to preview, change one number yourself, press **F6** to render, then **File > Export > Export as STL**.

```openscad
// Key tag: 40 x 20 x 3 mm, a 5 mm hole, raised letters 1 mm tall
difference() {
  cube([40, 20, 3]);
  translate([6, 10, -1]) cylinder(h = 5, d = 5, $fn = 40);
}
translate([12, 6, 3]) linear_extrude(1) text("VI", size = 8);
```

**Route B: AI as a coach.** Ask an AI to walk you through building your own idea in Tinkercad, one step at a time. You make every click.

---

## 🎚️ Base and Stretch

**Base: everyone does this.**
**Two prints.** **Print 1:** a model you found, shrunk to fit, printed and finished, with credit to its designer. **Print 2:** your own Tinkercad design, printed and finished. A nameplate is fine. Your **Print Card**, filled in.

**Stretch: required for high school, bonus for middle school.**
**Level up Print 2.** Either a nameplate with at least two extra features (a keyring hole, a stand, sunken text, a cut-out shape, a border), or a part that fixes a problem. Your Print Card says which.

---

## 📝 Deliverables

1. **Print 1 and Print 2**, shown to Mr. Krigger in class
2. **Print 2's STL file**
3. **Your Print Card**, as a PDF or a clear photo, with photos of both prints

There is no slide deck and no printer guide. Bonus challenges are not part of what you turn in.

---

## 📤 How to Submit

Upload the following to **Schoology**:

| # | What to Submit |
|---|---|
| 1 | Your Print Card (PDF or photo), with photos of both prints |
| 2 | Print 2's STL file |

**How to upload:**

1. Go to the assignment in Schoology
2. Click **Submit Assignment**
3. Click **"Upload"**. Do **NOT** click "Create" (Create is for text only and will not let you attach files)
4. Select your files and click **Submit**

The **exit ticket** is a separate Schoology item, taken in class. Both have to be done.

> **Need help taking screenshots?** See the [How to Take & Submit Screenshots](../fundamentals/how_to_screenshot.md) guide.

---

## 📋 Grading Rubric (25 points)

| Category | Points | What I'm Looking For |
|---|---|---|
| The Prints | 10 | Print 1 printed and finished (4). Print 2 printed and finished (6). A print that failed twice for a reason that is not your design counts when the STL, slicer screenshot and a failure photo are submitted. |
| Design | 5 | Print 2 is your own Tinkercad design, follows the design rules, fits 40 x 40 x 25 mm. HS: levelled up or fixes a problem. |
| Print Card | 5 | Every box filled in. "What went wrong" shows real thinking. Print 1's designer is credited. |
| Safety and Workflow | 5 | Passed the safety check, gloves and glasses every time, printer left ready for the next person, files named and queued correctly |

**Bonus:**
- **+3 points** for a middle school student who levels up Print 2 (required of high school students)
- **+2 points** each for a bonus challenge shown to Mr. Krigger: real-world test, Make It Fit, AI Lab (explain every line on request)

---

## 🧠 Vocabulary to Know

| Term | What It Means |
|---|---|
| **STL** | The standard 3D printing file. It describes the outside surface of your shape. |
| **Slicer** | Software that cuts your model into layers and tells the printer how to build each one. PreForm and MakerBot Print are slicers. |
| **.makerbot file** | What MakerBot Print makes from your STL. The only file the MakerBot can print. |
| **Resin** | The liquid a Formlabs printer builds from. Light turns it solid. |
| **Cartridge** | The bottle of resin that feeds the Formlabs tank |
| **Resin tank** | The tray the part is pulled out of. Its clear bottom film must never be scratched. |
| **Filament** | The plastic string a MakerBot melts. Ours is PLA. |
| **Supports** | Thin temporary struts that hold a part up while it prints |
| **Raft** | A flat layer the MakerBot prints first so your part sticks to the plate |
| **IPA** | Isopropyl alcohol. It washes liquid resin off a print. Flammable. |
| **Cure** | Light, and sometimes gentle heat, that finish hardening a resin print |
| **Tolerance** | The small gap you leave so two parts fit together |

---

## 💡 Troubleshooting

**"Resin got on my skin."**
→ Soap and water straight away. Never IPA or hand sanitizer. Tell Mr. Krigger.

**"I spilled resin or IPA."**
→ Step back, keep your gloves on, and tell Mr. Krigger. Used paper towels go in the resin waste container.

**"The model I downloaded is enormous, or almost invisible."**
→ Different units. Scale it in Tinkercad until the numbers are right.

**"MakerWorld gave me a 3MF file."**
→ Download the STL from the files list. If there is only a 3MF, pick a different model.

**"A website wants me to sign up before I can download."**
→ Pick a different model, or ask Mr. Krigger. Do not make an account.

**"My text did not print."**
→ Thinner than 1 mm, or floating. Make it 1 mm or more and overlap it into the part.

**"PreForm says my part will not print (red)."**
→ Run Auto-Orient and Auto-Generate supports again, or tilt the part by hand.

**"My resin part is sticky or has a white film."**
→ Wash again straight away in clean IPA, dry fully, then cure. Tell Mr. Krigger so he can check the IPA.

**"My resin part is soft or bends."**
→ Not cured long enough. Check the cure table for your resin. Curing a bit longer does no harm.

**"The MakerBot screen does not show my file."**
→ You need the `.makerbot` file, not the STL, at the top level of the flash drive.

**"MakerBot: the print will not stick to the plate."**
→ The plate may be dirty or not level, or the raft is off. Tell Mr. Krigger. Never reach in while it moves.

**"MakerBot: the print time is over 60 minutes."**
→ Make the part smaller.

<!-- ===========================================================================
SOURCES CHECKED 2026-10-19
- Form Wash times (V5 5 min, V4/V4.1 10 min; no two-wash cycle listed for standard resin): formlabs.com/support/Form-Wash-Time-Settings
- Staged rinsing is optional; rewash in clean IPA if still tacky: formlabs.com/support/Washing-Prints
- Form Cure V1 (Grey/White/Black V5 default 1 min no heat, full 5 min 60 C; V4/V4.1 10 min 60 C; Clear V4 5 min, V4.1 7 min 60 C):
  formlabs.com/support/Form-Cure-Time-and-Temperature-Settings. If the lab has a Form Cure 2nd gen, use its on-screen preset instead.
- Cartridge, tank, platform setup: formlabs.com/support/Setting-Up-Your-Form-3 ; failed print cleanup, plastic tank tool only:
  formlabs.com/support/Cleaning-After-a-Failed-Print-Form3 ; vent cap closed for storage: Resin cartridge maintenance and storage
- UltiMaker Children's Privacy Policy (under 16 = child, parental consent form), updated Aug 22 2025
- MakerWorld Terms of Use: 13+, under 18 needs a guardian to agree to the terms

BEFORE YOU CALL IT DONE
- [ ] PreForm, MakerBot Print and Tinkercad button names checked on the real lab computers
- [ ] Which Form Cure generation the lab has (V1 dial, or 2nd gen with presets)
- [ ] No API keys, passwords, or Wi-Fi credentials anywhere in the file
- [ ] Safety block present
- [ ] Site version stands alone: rubric and Schoology steps stay in this file
=========================================================================== -->
