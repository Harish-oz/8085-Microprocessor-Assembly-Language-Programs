Here is the assembly language program to find the HCF (Highest Common Factor) of two numbers using the 8085 microprocessor.<br><br>
```
LXI H, 2050H       ; First number is stored at 2050H

MOV A, M           ; Load first number into A
INX H              ; Move to next memory location 2051H
MOV B, M           ; Load second number into B

LP3: CMP B         ; Compare A with B
     JZ DONE       ; If A = B → HCF is found

     JC SWAP       ; If A < B → swap A and B
                   ; So that the larger number stays in A

     SUB B         ; A = A - B
                   ; Subtract smaller number from larger number

     JMP LP3       ; Repeat the process

SWAP: MOV C, B     ; Temporarily store B in C
      MOV B, A     ; Move A into B
      MOV A, C     ; Move old B into A
                   ; Now A is greater than B

      JMP LP3      ; Continue the HCF process

DONE: STA 2052H    ; Store the HCF at memory location 2052H

      HLT           ; Stop the program
```
<br><br><br>
**Explanation**<br>
This program uses the Euclidean algorithm.  

The basic idea is, We will take two numbers and subtract the smaller number from the larger number.  
Keep doing this until both numbers become equal.  
The equal value is the HCF.<br><br> 
For Example<br> 
First number is 18 and the second number is 12, The program works like this:-  
18 - 12 = 6  
12 - 6  = 6  
Now both numbers are equal: 6 = 6  
Therefore, HCF=6
