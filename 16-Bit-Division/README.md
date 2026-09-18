Here is the assembly language program to perform 16-bit division by 8-bit divisor using the 8085 microprocessor.
<br><br>
```
LXI B, 0000H       ; BC for Quotient and initially as 0

LHLD 2050H         ; HL for 16-bit Dividend
XCHG               ; DE for Dividend

LHLD 2052H         ; HL for Divisor

LOOP: MOV A, E     ; Load lower byte of Dividend
      SUB L        ; Subtract lower byte of Divisor

      MOV A, D     ; Load higher byte of Dividend
      SBB H        ; Subtract higher byte with borrow
      JC EXIT      ; If Dividend < Divisor, stop

      MOV A, E     ; Load lower byte again
      SUB L        ; Subtract lower byte
      MOV E, A     ; Store result in E

      MOV A, D     ; Load higher byte again
      SBB H        ; Subtract higher byte with borrow
      MOV D, A     ; Store result in D

      INX B        ; Increase Quotient by 1
      JMP LOOP     ; Repeat the division

EXIT: XCHG         ; HL = Remainder
SHLD 2054H         ; Store Remainder at 2054H

MOV H, B           ; Move higher byte of Quotient to H
MOV L, C           ; Move lower byte of Quotient to L
SHLD 2056H         ; Store Quotient at 2056H

HLT                ; Stop the program
```
<br><br><br>
**Explanation**<br>
This program performs division by repeated subtraction.  
The 16-bit dividend is stored at 2050H–2051H, and the divisor is stored at 2052H. The program keeps subtracting the divisor from the dividend until the remaining value becomes smaller than the divisor. Every time the subtraction is successful, the quotient is increased by 1.  
  
For example:    
Dividend = 25    
Divisor  = 6  
then,  
25 - 6 = 19    → Quotient = 1  
19 - 6 = 13    → Quotient = 2  
13 - 6 = 7     → Quotient = 3  
7 - 6  = 1     → Quotient = 4  
Now 1 < 6, so the division stops.  
  
Therefore:  
Quotient  = 4    
Remainder = 1  
