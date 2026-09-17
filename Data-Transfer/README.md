Here is the assembly language program to transfer 5 bytes of data from one memory location to another using the 8085 microprocessor.
<br><br>
```
LXI H, 2050H       ; Source memory location
LXI D, 2070H       ; Destination memory location
MVI C, 05H         ; 5 bytes will be transferred

LOOP: MOV A, M     ; Load data from source memory into A
      STAX D       ; Store data from A into destination memory
      DCR C        ; Decrease counter
      INX H        ; Move to next source location
      INX D        ; Move to next destination location
      JNZ LOOP     ; Repeat until all 5 bytes are transferred

HLT                ; Stop the program
```
<br><br><br>
**Explanation**<br>
The program copies 5 bytes of data from one memory location to another.  
Source starts at 2050H and destination starts at 2070H.
