# Tello Drone Python Coding and Creative Flight Course Assignment

## Objective

Your task is to design and code a flight routine for the **DJI Tello drone** using Python. You will build a creative obstacle course and program the drone to fly through it. This project blends creativity, engineering, and coding with hands-on drone piloting.

## Why This Matters

This assignment teaches you the fundamentals of drone control and automation. You’ll strengthen your Python skills, learn about drones and flight safety, and apply computational thinking to real-world robotics. By the end, you will have designed, coded, and executed your own aerial course.

---

## Part A — Getting Started with the Tello Drone

1. Power on the Tello drone.
2. Connect your computer to the drone’s Wi-Fi network (SSID: **TELLO-XXXXXX**).
3. Install the **Tello Python SDK** or use a provided library such as `djitellopy`.
4. Test your connection with a simple Python script:
   ```python
   from djitellopy import Tello

   tello = Tello()
   tello.connect()
   print(tello.get_battery())
   tello.takeoff()
   tello.land()
   ```

If the drone takes off and lands safely, you’re ready to begin!

Helpful resources:

- [DJITelloPy GitHub](https://github.com/damiafuentes/DJITelloPy)

---

## Part B — Designing Your Flight Course

- Be **as creative as possible** when designing your aerial course.
- Use safe classroom materials such as cardboard hoops, cones, tunnels, or markers on the floor.
- Your course must include at least **three unique challenges**, such as:
  - Flying through a hoop
  - Turning around an object
  - Landing on a marked target

---

## Part C — Programming Your Drone with Python

1. Start with simple flight commands: `takeoff`, `move_forward(x)`, `rotate_clockwise(x)`, `land`.
2. Add more complex maneuvers like flips or curves.
3. Use loops and functions to keep your code clean.

**Example flight routine:**

```python
tello.takeoff()
tello.move_forward(100)
tello.rotate_clockwise(90)
tello.move_forward(100)
tello.land()
```

---

## Extra Credit

- +1 point for adding a creative **aerial trick** (such as a flip) safely in your course.
- +2 points for designing an **exceptionally creative and visually impressive course**.

---

## Deliverables

1. A video of your drone flying and completing your course.
2. Your Python program (`.py` file).
3. A short reflection (3–5 sentences): What challenges did you face, and how did you solve them?

---

## Grading Rubric (25 points + extra credit)

- **Course Design (5 pts):** Safe, creative, and well-structured aerial course.
- **Python Program (10 pts):** Drone completes the course as intended using Python.
- **Execution (5 pts):** Smooth and accurate flight completion.
- **Submission (5 pts):** Includes video, code, and reflection.
- **Extra Credit (up to 3 pts):** Aerial tricks (+1) and outstanding creativity (+2).

---

## Tips for Success

- Always test in a safe, open area free of people or fragile objects.
- Fly at low altitude until you’re confident in your code.
- Break down your program into smaller sections and test step by step.
- Be creative — your drone should not just fly straight, but perform an engaging routine.

