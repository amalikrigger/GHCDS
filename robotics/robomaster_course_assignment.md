# RoboMaster Coding and Creative Course Assignment

## Objective

Your task is to learn how to operate the RoboMaster robot, design a unique obstacle course, and then program the robot to complete it using **both Scratch (block-based coding)** and **Python**. This assignment blends creativity with robotics, coding, and engineering, giving you hands-on experience in designing, problem-solving, and programming.

## Why This Matters

This project moves you from learning how to operate a robot to creating your own challenges and solutions. You will strengthen your coding skills, practice problem-solving, and apply computer science concepts to real-world robotics. By completing this assignment, you’ll see how creativity and engineering design come together.

## Part A — Driving and Operating the RoboMaster

1. Turn on your RoboMaster and connect it to the RoboMaster app.
2. Learn the basic controls:
   - Driving with the joysticks in the app
   - Shooting projectiles
   - Using the laser system
3. Practice until you can confidently maneuver the robot.

Helpful resources:

- [Beginner RoboMaster S1 Tutorial](https://www.youtube.com/watch?v=UdLHT3nBP_o)
- [Driving and Controls Overview](https://www.youtube.com/watch?v=1hJdxSszHdk)

## Part B — Designing Your Course

- Be **as creative as possible** when building your obstacle course.
- Use safe classroom materials such as cones, boxes, or books.
- Your course must include at least **three distinct challenges**, such as:
  - Driving in a zig-zag pattern
  - Shooting at a target
  - Passing through a tunnel or under an arch
- The course should be fun, challenging, and achievable by the RoboMaster.

## Part C — Programming the RoboMaster with Scratch

1. Open the RoboMaster app and switch to **Scratch coding mode**.
2. Write a program that can:
   - Move forward
   - Turn left and right
   - Pause or stop at certain checkpoints
3. Expand your code until the robot can complete the full course.

Reference: [Scratch RoboMaster Programming Guide](https://www.dji.com/robomaster-s1/programming-guide)

## Part D — Programming the RoboMaster with Python

### Step 1: Set Up Python in the RoboMaster App

1. Open the RoboMaster app.
2. Go to Programming > Python.
3. Test your setup by running this simple code:
   ```python
   import robomaster
   from robomaster import robot

   ep_robot = robot.Robot()
   ep_robot.initialize(conn_type="ap")

   ep_chassis = ep_robot.chassis
   ep_chassis.move(x=0.5, y=0, z=0, xy_speed=0.5).wait_for_completed()

   ep_robot.close()
   ```
4. Confirm that your RoboMaster moves forward slightly.

### Step 2: Program the Course

- Translate your Scratch program into Python.
- Use loops and functions for clean, organized code.
- Example for navigating a zig-zag:
  ```python
  for i in range(3):
      ep_chassis.move(x=0.5, y=0, z=0, xy_speed=0.5).wait_for_completed()
      ep_chassis.move(x=0, y=0, z=30, xy_speed=30).wait_for_completed()
  ```

Helpful tutorials:

- [RoboMaster Python Basics](https://www.youtube.com/watch?v=9LFIQ76ZJQ0)
- [DJI Official Programming Guide](https://www.dji.com/robomaster-s1/programming-guide)
- [Coding RoboMaster with Python](https://www.youtube.com/watch?v=a5sC6ssuzfo)

## Extra Credit

- +1 point for each additional RoboMaster you successfully set up (either by building or fixing an existing one).
- Up to +2 points for exceptional creativity in course design.

## Deliverables

1. A video of your RoboMaster completing your obstacle course.
2. Your Scratch program and your Python program.
3. A short reflection (3–5 sentences): What challenges did you face? How did you solve them?

## Grading Rubric (25 points + extra credit)

- **Course Design (5 pts):** Safe, creative, and well-structured obstacle course.
- **Scratch Program (5 pts):** Robot completes the course as intended.
- **Python Program (5 pts):** Robot completes the course using Python.
- **Execution (5 pts):** Smooth and accurate course completion.
- **Submission (5 pts):** Includes required video, programs, and reflection.
- **Extra Credit (up to 3 pts):** Additional RoboMasters working (+1 each) and outstanding creativity (+2).

## Tips for Success

- Test your code in small sections before running the entire program.
- Save your work regularly in the app.
- Use safe objects for obstacles (no liquids, sharp items, or fragile objects).
- Focus on making your course fun, original, and achievable.

