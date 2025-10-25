# sa2-MPMC
AIM:

To Write an assembly language program in 8051 to generate a 250 ms delay using Timer 1 in Mode 1 and blink an LED connected to Port 0.5 continuously.

APPARATUS REQUIRED:

PERSONAL COMPUTER

KEIL VISION

ALGORITHM:

1. Start the program.
2. Set Port 0 as output.
3. Repeat the following steps forever: Toggle (ON/OFF) the LED connected to P0.5.
Call the 250 ms delay subroutine.
4. In the delay subroutine: Load register R2 = 4 (for 4 × 62.5 ms = 250 ms). Set Timer 1 in Mode 1 (16-bit). Load TH1 = 0BH, TL1 = 0DCH. Start the timer. Wait until the timer overflow flag (TF1) becomes 1. Stop the timer and clear the flag. Decrease R2
and repeat until it becomes zero. Return to the main program.
5. The LED keeps blinking continuously every 250 ms.

PROGRAM:
~~~~~
ORG 0000H
MAIN: MOV P0, #00H
AGAIN: CPL P0.5
ACALL DELAY_250MS
SJMP AGAIN
DELAY_250MS:
MOV R2, #04
NEXT_DELAY:
MOV TMOD, #10H
MOV TH1, #0BH
MOV TL1, #0DCH
SETB TR1
WAIT1: JNB TF1, WAIT1
CLR TR1
CLR TF1
DJNZ R2, NEXT_DELAY
RET
END
~~~~~

OUTPUT

![WhatsApp Image 2025-10-25 at 11 06 01_4d62cf39](https://github.com/user-attachments/assets/17a5f4a2-5d71-46d2-b353-2866219ba41a)

***LED TOGGLING AT P0.5 AT 250MS:***

***ON***

![WhatsApp Image 2025-10-25 at 11 06 02_b7503994](https://github.com/user-attachments/assets/c6899e30-71b5-4a98-bcd7-52fb960a1f31)

***OFF***

![WhatsApp Image 2025-10-25 at 11 06 02_579252e4](https://github.com/user-attachments/assets/ebb699d8-6bb1-4a93-bf97-088db939425a)

***YOU CAN SEE THE LED IS TOGGLING AT 250MS***

RESULT:

Thus The Program to generate a 250ms delay using Timer 1 in Mode 1 and blink an LED connected to Port 0.5 continuously is done and output is shown.




