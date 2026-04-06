# 🤖 RoboMaster: Navigate the Room — Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

---

### Multiple Choice

**1. What does "autonomous" mean in robotics?**

A) The robot is controlled by a joystick

B) The robot moves on its own using code, without human control

C) The robot is connected to Wi-Fi

D) The robot can talk

---

**2. When debugging your RoboMaster program, what's the best approach?**

A) Change 5 things at once and test

B) Delete everything and start over

C) Change ONE thing, test, and see what happens

D) Ask someone else to fix it

---

**3. Your robot is turning too far at a corner. The rotation block says 90°. What should you try?**

A) Increase it to 95°

B) Decrease it to 85-87°

C) Remove the rotation block entirely

D) Add more forward movement

---

### Short Answer

**4. Why is it important to plan your route on paper before writing any code?**

______________________________________________________________________________

______________________________________________________________________________

---

**5. Why should you add a "wait 0.5 seconds" block between every move and turn?**

______________________________________________________________________________

---

**6. Your robot completes the loop but stops 50cm away from the starting tape. What would you adjust and how?**

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B** — The robot moves on its own using code, without human control

2. **C** — Change ONE thing, test, and see what happens. Changing multiple things at once makes it impossible to know which fix worked.

3. **B** — Decrease it to 85-87°. The robot is overshooting the turn, so it needs fewer degrees. Floor friction can cause turns to vary from the exact number.

4. Planning on paper helps you estimate distances and angles before coding. Without a plan, you'd be guessing at every distance and turn, which wastes time. It's like giving someone directions — you need to know the route before you can describe it.

5. The wait block gives the robot time to fully stop before starting the next action. Without it, the robot might still be moving when it starts turning, which makes the turn inaccurate. Small errors compound over a long route.

6. The robot isn't traveling far enough on the final segment. I would increase the distance on the last "move forward" block by a small amount (maybe 0.3-0.5m) and test again. I might also check if earlier segments are slightly off, since small errors from earlier add up.
