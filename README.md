# S23 CSCE211 Project 3 ReadMe

Team Members: Nia Sparacino, Bee Ball, Joshua Ramon-Cruz

Team Contributions:

Nia Sparacino: Base-6 and Base-10 Counter Solver, General Collaboration, Support

Bee Ball : Decimal Driver Logic Solving, Simplifying, README, Github Creation, Logisim Evolution Implementation, Logisim Conversion, General Collaboration, Support

Joshua R-C: README, Group Communication, General Collaboration, Support

Implementation Description:

## General Outline:

1) The project description was assessed for execution by understanding the required behavior of the display and subsequent output.

2) Then, the output was achieved by implementing the truth tables in the end by the utilization of Logisim.

## Detailed Process:

Used a clock and X input leading into the base-10 counter and base-6 counter. Of which, the outputs of the base-10 counter A B C D, led to the base-10 display driver. Then, the out of base-10 driver fed into the right-most display.

The out of the base-10 counter, along with the x signal, fed into the base-6 counter, which outputs A B C D, fed directly into another base-10 display driver. The output of the other display driver fed into the left-most display.

## Quirks:

## Counters Summarized:

**J**<sub>A</sub> = B'C'D'x + BCDx'

**K**<sub>A</sub> = D'x +B'Dx' + C'Dx'

**J**<sub>B</sub> = CDx' + AD'x

**K**<sub>B</sub> = CDx' + C'D'x

**J**<sub>C</sub> = A'Dx' + BD'x + AD'x

**K**<sub>C</sub> = Dx' + A'D'x

**J**<sub>D</sub> = 1

**K**<sub>D</sub> = 1

## **1's Counter (Base - 10)**

| A | B | C | D | A\*B\*C\*D<br>x=0 x=1 | V overflow<br>x=0 x=1 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 0<br>0 | 0<br>0 | 0<br>0 | 0<br>1 | 0 0 0 1 1 0 0 1<br>0 0 1 0 0 0 0 0 | 0 1<br>0 0 |
| 0<br>0 | 0<br>0 | 1<br>1 | 0<br>1 | 0 0 1 1 0 0 0 1<br>0 1 0 0 0 0 1 0 | 0 0<br>0 0 |
| 0<br>0 | 1<br>1 | 0<br>0 | 0<br>1 | 0 1 0 1 0 0 1 1<br>0 1 1 0 0 1 0 0 | 0 0<br>0 0 |
| 0<br>0 | 1<br>1 | 1<br>1 | 0<br>1 | 0 1 1 1 0 1 0 1<br>1 0 0 0 0 1 1 0 | 0 0<br>0 0 |
| 1<br>1 | 0<br>0 | 0<br>0 | 0<br>1 | 1 0 0 1 0 1 1 1<br>0 0 0 0 1 0 0 0 | 0 0<br>1 0 |
| 1<br>1 | 0<br>0 | 1<br>1 | 0<br>1 | x x x x x x x x<br>x x x x x x x x | x x<br>x x |
| 1<br>1 | 1<br>1 | 0<br>0 | 0<br>1 | x x x x x x x x<br>x x x x x x x x | x x<br>x x |
| 1<br>1 | 1<br>1 | 1<br>1 | 0<br>1 | x x x x x x x x<br>x x x x x x x x | x x<br>x x |

### **Base - 10 (Continued)**

**A\*** = x'(AD' + BCD) + x(AD +A'B'C'D')

= AD'x' + ADx + A'B'C'D'x + BCDx' = **J<sub>A</sub>A' + K<sub>A</sub>'A**

= A'(B'C'D'x + BCDx') + A(D'X +Dx + BCDx')

**J**<sub>A</sub> = B'C'D'x + BCDx'

**K**<sub>A</sub> = (D'x' + Dx + BCDx')' = D'x +B'Dx' + C'Dx'

---

**B\*** = x'(BC' + BD' + B'CD) + x(AD' + BD + BC)

= B'CDx' + BC'x' BD'x' + BCx +BDx + AD'x = **J<sub>B</sub>B' + K<sub>B</sub>'B**

**=** B'(CDx' + AD'x) + B(C'x' + D'x' + Cx + Dx + AD'x)

**J**<sub>B</sub> = CDx' + AD'x

**K**<sub>B</sub> = (C'x' + D'x' +Cx + Dx + A'D'x)' = **CDx' + A'C'D'x**

---

**C\*** = x'(CD' + A'C'D) + x(AD' + CD + BC'D')

= A'C'Dx' +BC'D'x + CD'x' + CDx + AD'x

= C'(A'Dx' + BD'x + AD'x) + C(D'x' + Dx + AD'x) = **J<sub>C</sub>C' + K<sub>C</sub>'C**

**J**<sub>C</sub> = A'Dx' + BD'x + AD'x

**K**<sub>C</sub> = (D'x' + Dx + AD'x)' =**Dx' + A'D'x**

---

**D\*** = x'D' + xD = D' = **J<sub>D</sub>D' + K<sub>D</sub>'D**

**J**<sub>D</sub> = 1

**K**<sub>D</sub> = 0' = 1

---

### **Base - 10 Counter Overflow**

**V'** = x'(AD) + x(A'B'C'D') = **ADx' + A'B'C'D'x**

## **Base 6 Counter**

| | ABCD | A\*B\*C\* |
| :---: | :---: | :---: |
| 0 | 0 0 0 0<br>0 0 0 1 | 0 0 1<br>1 0 1 |
| 1 | 0 0 1 0<br>0 0 1 1 | 0 1 0<br>0 0 1 |
| 2 | 0 1 0 0<br>0 1 0 1 | 0 1 1<br>0 0 1 |
| 3 | 0 1 1 0<br>0 1 1 1 | 1 0 0<br>0 1 0 |
| 4 | 1 0 0 0<br>1 0 0 1 | 1 0 1<br>0 1 1 |
| 5 | 1 0 1 0<br>1 0 1 1 | 0 0 0<br>1 0 0 |
| 6 | 1 1 0 0<br>1 1 0 1 | x x x<br>x x x |
| 7 | 1 1 1 0<br>1 1 1 1 | x x x<br>x x x |

### **Base - 6 Counter (Continued)**

**A\*** = AC'x' + ACx + BCx' + A'B'C'x = **J<sub>A</sub>A' + K<sub>A</sub>'A**

= A'(BCx' + B'C'x) + A(Cx + C'x' + BCx')

**J**<sub>A</sub> = BCx' + B'C'x

**K**<sub>A</sub> = (Cx + C'x' + BCx')'=**C'x + B'Cx'**

---

**B\*** = AC'x + BC'x' + BCx + A'B'Cx' = **J<sub>B</sub>B' + K<sub>B</sub>'B**

= B'(A'Cx' + AC'x) + B(Cx + C'x' + AC'x)

**J**<sub>B</sub> = A'Cx' + AC'x

**K**<sub>B</sub> = (Cx + C'x' + AC'x)' =**Cx' + A'C'x**

---

**C\*** = C' = **J<sub>C</sub>C' + K<sub>C</sub>'C**

**J**<sub>C</sub> = 1

**K**<sub>C</sub> = 0' = 1
