Here is the assembly language program to generate 5 Fibonacci numbers using the 8085 microprocessor.
<br><br>
```
LXI H, 3050H       ; Series memory location is 3050H
MVI C, 03H         ; C stores remaining number of terms
MVI B, 00H         ; First Fibonacci number is 0
MVI D, 01H         ; Second Fibonacci number is 1

MOV M, B           ; Store 0 at 3050H
INX H              ; Move to next memory location
MOV M, D           ; Store 1 at 3051H

LP: MOV A, B       ; Copy first number to A
    ADD D          ; Add second number → next Fibonacci number
    MOV B, D       ; Move second number to B
    MOV D, A       ; Store new number in D
    INX H          ; Move to next memory location
    MOV M, A       ; Store Fibonacci number
    DCR C           ; Decrease counter
    JNZ LP         ; Repeat until all numbers are generated

HLT                ; Stop
```
<br><br><br>
**Explanation**<br>
The Fibonacci series starts with: 0, 1, 1, 2, 3, 5, 8...  

Each new number is found by adding the previous two numbers.


