# 🤖 RoboMaster: Navigate the Room, Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

---

### Multiple Choice

**1. What does "autonomous" mean in robotics?**

A) The robot is controlled by a joystick

B) The robot runs on its program with nobody touching the controls

C) The robot is connected to Wi-Fi

D) The robot can talk

---

**2. Your Circle program works, except the robot turns too far at one corner. The rotate block says 90°. What do you try first?**

A) Change every angle in the program to 85°

B) Lower that one angle a few degrees and run it again

C) Delete the program and start over

D) Double the speed

---

**3. Your five number-card blocks are all built correctly, but the robot never reacts to any card. What did you most likely forget?**

A) A wait block at the end

B) The block that enables marker identification

C) A faster speed

D) A sixth color

---

**4. Your Figure 8 clears the first table, then clips the second one. Where do you look first?**

A) The very last block of the program

B) The crossing, where the robot lines up for the second loop

C) The LED colors

D) The first block of loop one

---

**5. Your robot finishes the Circle about 40 cm past the X. The corners look fine. What do you adjust?**

A) The LED color

B) The last side, shortened a little

C) Every turn angle

D) The number cards

---

### Short Answer

**6. Why is it important to plan your route on paper before you write any code?**

______________________________________________________________________________

______________________________________________________________________________

---

**7. Why should you change only one thing between test runs?**

______________________________________________________________________________

---

**8. Your robot has no map of the room. Explain why the last side of a long loop is the hardest one to get right.**

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B**: The robot runs on its program with nobody touching the controls.

2. **B**: Lower that one angle a few degrees and run it again. One corner is wrong, so fix that corner. Changing every angle breaks the corners that already work.

3. **B**: Marker identification is off until the program turns it on. The event blocks cannot fire if the camera is not looking for anything.

4. **B**: The crossing. Loop one worked, so the trouble starts between the loops. A small error at the crossing sends the robot at the second table at the wrong angle.

5. **B**: The last side. The corners are fine, so the extra distance is in a straight run, and the last side holds the pile of every earlier error.

6. Planning on paper lets you estimate distances and angles before you code. Without a plan you are guessing at every side and turn, which wastes time. A robot follows directions exactly, so you need to know the route before you can give it. Accept any answer that says the robot cannot work out the route for itself.

7. If you change several things at once and the run improves, you cannot tell which change helped. One change per test shows you what each change does. Full marks for naming the "which one worked" problem.

8. The robot only counts how far its wheels have turned. Wheels slip a little, so every move is slightly off, and each new move starts from the wrong spot and adds its own error. By the last side, all of those errors have piled up. Accept any answer that says small errors add up, and award extra credit for the term **dead reckoning**.
