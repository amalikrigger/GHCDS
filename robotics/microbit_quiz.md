# 🎛️ Micro:bit — Exit Ticket Quiz

**Name:** ______________________________ &nbsp;&nbsp; **Date:** ______________

---

### Multiple Choice

**1. What is the Input → Process → Output pattern?**

A) A way to organize your files on the computer

B) Something comes in (input), code decides what to do (process), something goes out (output)

C) A type of programming language

D) The order you should eat meals

---

**2. What does the accelerometer in a micro:bit detect?**

A) Temperature changes

B) Motion, shaking, and tilt

C) Sound and music

D) Wi-Fi signals

---

**3. What file type do you download from MakeCode to load onto the micro:bit?**

A) .mp3

B) .pdf

C) .hex

D) .jpg

---

### Short Answer

**4. You want to build a program where pressing Button A shows a happy face and pressing Button B shows a sad face. What two blocks would you need from the "Input" category?**

______________________________________________________________________________

---

**5. Explain the difference between the `on start` block and the `forever` block. When would you use each one?**

______________________________________________________________________________

______________________________________________________________________________

---

**6. Design your own micro:bit project idea in 2-3 sentences. What input(s) would it use, what would the processing logic be, and what would the output be?**

______________________________________________________________________________

______________________________________________________________________________

______________________________________________________________________________

---

## Answer Key (Teacher Copy)

1. **B** — Input (something comes in like a button press), Process (code makes a decision), Output (something happens like an LED display change). This is the foundation of all computing.

2. **B** — Motion, shaking, and tilt. The accelerometer detects physical movement and orientation. Phones use the same sensor to know when you rotate the screen.

3. **C** — .hex files. This is the compiled program that the micro:bit can run. You drag it onto the MICROBIT drive to load it.

4. `on button A pressed` and `on button B pressed`. Inside each, you'd put a `show icon` block with the appropriate face.

5. `on start` runs ONCE when the micro:bit first powers on or is reset — use it for setup (showing a welcome message, initializing variables). `forever` runs continuously in a loop, over and over — use it for things that need to keep checking or updating (reading a sensor, updating a display, monitoring for changes).

6. Any reasonable project idea that identifies input(s), processing logic, and output. Example: "A noise-level meter (V2) that uses the microphone (input) to measure how loud the room is (process), and shows a bar graph on the LEDs — more LEDs lit up = louder (output). If it gets too loud, it shows a warning icon."
