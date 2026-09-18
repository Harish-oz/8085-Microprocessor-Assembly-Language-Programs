Here is the assembly language program to perform addition of two 16-bits using HL and DE registers<br><br>

```
LHLD 2050H       ; Load 16-bit number from 2050H–2051H into HL
                 ; HL is used because it supports 16-bit operations

XCHG             ; Exchange HL with DE
                 ; First number is moved to DE to free HL for next value

LHLD 2070H       ; Load second 16-bit number into HL
                 ; Now HL = second number, DE = first number

DAD D            ; Add DE (first number) to HL (second number)
                 ; Result stored in HL (HL = HL + DE)

SHLD 2080H       ; Store 16-bit result from HL into 2080H–2081H

RST 5            ; Stop execution
```
