Here is the assembly language program to perform 16-bit addition using the DAD instruction in the 8085 microprocessor.
<br><br>
```
LHLD 2050H        ; Load first 16-bit number into HL
XCHG              ; Move first number from HL to DE

LHLD 2070H        ; Load second 16-bit number into HL
DAD D             ; Add DE to HL

SHLD 2080H        ; Store the 16-bit result at 2080H
HLT               ; Stop the program
```
<br><br><br>
**Explanation**<br>
This program adds two 16-bit numbers using the DAD instruction.  
The first 16-bit number is stored at 2050H–2051H, and the second number is stored at 2070H–2071H. First, LHLD loads the first number into the HL register pair. XCHG then moves this number to the DE register pair, because DAD D adds the value of DE to HL. Next, the second number is loaded into HL.  
The DAD D instruction performs: HL = HL + DE    
The final 16-bit result is then stored at 2080H–2081H using SHLD.
