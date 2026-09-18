Here is the assembly language program to multiply two 8-bit numbers using repeated addition.
<br><br>
```
MVI C, 00H         ; C will store the carry
MVI B, 25H         ; B is 25H, number of times to add
MVI D, 10H         ; D is 10H, number to be added
MVI A, 00H         ; A starts from 00H

LP3: ADD D         ; Add 10H to A
     JNC LP        ; If there is no carry, continue
     INR C         ; If carry occurs, increase C by 1

LP:  DCR B         ; Decrease the counter
     JNZ LP3       ; Repeat until B becomes 00H

STA 2070H          ; Store lower byte of result at 2070H
MOV A, C           ; Move higher byte (carry) to A
STA 2071H          ; Store higher byte at 2071H

HLT                ; Stop the program
```
<br><br><br>
**Explaination**<br>
This program performs multiplication by using repeated addition instead of a multiplication instruction and the result is stored as a 16-bit number.  
Here, 25H is the number of times the addition will be performed, and 10H is the number that is repeatedly added.  
  
So the program is basically doing: 10H + 10H + 10H + ... (25H times)  
The result is calculated in the A register. Since A can hold only 8 bits, sometimes the addition produces a carry. The carry is counted in register C. After all additions are completed, the result is divided into two parts. The lower 8 bits are stored at 2070H, while the higher 8 bits (carry) are stored at 2071H.
