---
title: "Watch"
author: "Siddhan"
description: "An analog IC chip watch powered with a LiPo and outputs in digital time on segment displays! Analog, or digital!?"
created_at: "2026-11-01"
---

# November 1: Put down parts and wired them on the schematic

Spent the evening afterschool on wiring the schematic with all the parts, including the SG-3030CM oscillator and then the 4013, 4017, 4081 and the 4026 IC chips. I put down all the necessary resistors and capacitors as well.

<img width="806" height="653" alt="Screenshot 2026-11-19 at 20 18 32" src="https://github.com/user-attachments/assets/f3289f05-a47b-45b3-9269-6115cfc4ea00" />

**Total time spent: 3 hours**

# November 3: Segment wrapping logic and SimulIDE creation

This was a very annoying part of the project, as the wiring was consistently wrong and did not work when I tested it in SimulIDE, a schematic simulator. Not to forget, I also spent a lot of time recreating the schematic in the new software I learned about. Finally, at the end of the day in bed I was able to think and write down a good way to get the 4 segment displays to wrap from 23:59 to 00:00, as a clock does.



**Total time spent: 2 hour**

# November 4: Made my thought into the circuit

I implemented my thought of system of wrapping to the circuit, and it worked! It works by using a 74HC08 4x AND gate chip, which detects when certain segments are on the displays. It detects for a 6, by detecting segments E and F on the 00:x0 slot; and also detects for both 2 and 3 on the 0x:00 and x0:00 slots, by using the 3 inputs of: G (on x0:00) for 2; E, F and G for detecting 6 on the 00:x0 display; and finally segments F and G for detecting 4 on 0x:00??? I don't know it is very confusing! Here is a picture of my late night note:


**Total time spent: 3 hours**
