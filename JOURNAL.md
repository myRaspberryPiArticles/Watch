---
title: "Watch"
author: "Siddhan"
description: "An analog IC chip watch powered with a LiPo and outputs in digital time on segment displays! Analog, or digital!?"
created_at: "2026-11-01"
---

# November 8: Put down parts and wired them on the schematic

Spent the evening afterschool on wiring the schematic with all the parts, including the SG-3030CM oscillator and then the 4013, 4017, 4081 and the 4026 IC chips. I put down all the necessary resistors and capacitors as well.

<img width="806" height="653" alt="Screenshot 2026-11-19 at 20 18 32" src="https://github.com/user-attachments/assets/f3289f05-a47b-45b3-9269-6115cfc4ea00" />

**Total time spent: 3 hours**

# November 10: Segment wrapping logic and SimulIDE creation

This was a very annoying part of the project, as the wiring was consistently wrong and did not work when I tested it in SimulIDE, a schematic simulator. Not to forget, I also spent a lot of time recreating the schematic in the new software I learned about. Finally, at the end of the day in bed I was able to think and write down a good way to get the 4 segment displays to wrap from 23:59 to 00:00, as a clock does.

<img width="223" height="398" alt="Screenshot 2026-11-23 at 19 22 06" src="https://github.com/user-attachments/assets/d16c1895-8644-4eb8-ad2e-40e19771d0f9" />

**Total time spent: 2 hours**

# November 11: Made my thought into the circuit

I implemented my thought of system of wrapping to the circuit, and it worked! It works by using a 74HC08 4x AND gate chip, which detects when certain segments are on the displays. It detects for a 6, by detecting segments E and F on the 00:x0 slot; and also detects for both 2 and 3 on the 0x:00 and x0:00 slots, by using the 3 inputs of: G (on x0:00) for 2; E, F and G for detecting 6 on the 00:x0 display; and finally segments F and G for detecting 4 on 0x:00??? I don't know it is very confusing! Here is a picture of my late night note:

<img width="539" height="640" alt="Screenshot 2026-11-21 at 13 25 24" src="https://github.com/user-attachments/assets/ab4842cc-938c-4b4e-9ab3-887637941a76" />

**Total time spent: 3 hours**

# November 12: SimulIDE integration

I now have fully made the watch circuit work in SimulIDE, and using an oscilloscope, I was able to get the right reading of 1/60 Hz, also known as 1 pulse per minute, and this then feeds into the display block successfully! I merged both systems into 1 SimulIDE file and was able to see the circuit working accurately. Then I moved on assigning footprints carefully, choosing the small 0603 and TSSOP package sizes. After this I played around with placing them in a 35x42 mm rectangle with curved corners, mocking how it should be in real life - also to make sure a case fits. 

<img width="721" height="640" alt="Screenshot 2026-11-21 at 13 31 53" src="https://github.com/user-attachments/assets/a3f163c7-297a-4a49-a5ed-310d42514813" />

**Total time spent: 2 hours**


# November 13: PCB Development

Today I realised how hard it actually was to wire the components when there was no logical placement and it was just all squished together. After realising this I decided to start making a compressed display block. I did this by getting all the components needed for making all 4 displays work, and then wiring the resistors closely, and the CD4026s also squeezed by the displays. I had to move some of the resistors to the bottom of the board to ensure there was enough space. After this I moved the block to a central position in the board and decided where everything else would go.

<img width="300" height="570" alt="Screenshot 2026-11-21 at 13 37 32" src="https://github.com/user-attachments/assets/77b72b40-e4e5-46b2-be11-bd34bcd0111c" />

**Total time spent: 1 hour**


# November 15: PCB Development

I now spent some time on the rest of the components, like the clock circuit and the dividers. This fit in nicely to other space on the PCB and after wiring it up and compressing it, I ensured the DRC was mostly fine. I had to adjust some of the tolerances of the board, and especially the copper planes, just to make sure there are no unnecessary islands. While doing this I learned how to use a 'no fill' zone.

Then I moved on later in the day to finalising removing the parts I didn't want to get soldered by the PCB company from the BOM, and made sure their 3D models were also removed to make sure I get what I see!

<img width="524" height="619" alt="Screenshot 2026-11-21 at 13 40 49" src="https://github.com/user-attachments/assets/86b7b12a-c937-4590-b7b0-0b0b5c9b7e3f" />

**Total time spent: 3 hours**

# November 16: PCB Development

Today I did some minor work on the PCB and added some cool silkscreens to make it look like the exposed circuit I want it to be. I finalised the DRC and got it ready for production on the files side. I ensured the BOM was ready for both JLCPCB and PCBWay, before submitting them and awaiting verification.

<img width="524" height="619" alt="Screenshot 2026-11-21 at 13 44 47" src="https://github.com/user-attachments/assets/df82fd14-9d9e-47a5-b909-696ef16f68ce" />

**Total time spent: 1 hour**
