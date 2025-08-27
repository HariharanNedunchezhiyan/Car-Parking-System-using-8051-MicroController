ORG 000H
    MOV R0, #10             ; No of free slots for parking, can be extended upto 255
    MOV P2, #00H            ; Setting P2 port as output for controlling the LCD
    MOV P3, #00000011B      ; Making the P3.0 and P3.1 as input to connect sensor
                            ; (P3.0 entrance gate and P3.1 exit gate)

    MOV TMOD, #01H          ; Timer 0 in mode 1 to generate time delay

    MOV B, #38H             ; init. LCD 2 lines,5x7 matrix
    ACALL COMNWRT
    ACALL DELAY

    MOV B, #0EH             ; display on, cursor on
    ACALL COMNWRT
    ACALL DELAY

    MOV B, #06H             ; shift cursor right
    ACALL COMNWRT
    ACALL DELAY

    MOV B, #0CH             ; display on, cursor on
    ACALL COMNWRT
    ACALL DELAY

    MOV B, #01              ; clear LCD
    ACALL COMNWRT
    ACALL DELAY

    MOV B, #80H             ; cursor at line 1, pos.0
    ACALL COMNWRT
    ACALL DELAY

    MOV DPTR, #500H         ; storing DPTR with 500h to show the message
                            ; stored in that location to LCD

LOOP:
    CLR A
    MOVC A, @A+DPTR
    ACALL DATAWRT
    ACALL DELAY
    INC DPTR
    JZ EXT
    SJMP LOOP

EXT:
    ACALL CHECKR0           ; calling CHECKR0 to check the current value of R0

MONITOR:
    MOV B, P3
    MOV R6, B
    CJNE R6, #00000000B, CHECK01
    SJMP MONITOR

CHECK01:
    CJNE R6, #00000001B, CHECK10
    ACALL IN

CHECK10:
    CJNE R6, #00000010B, MONITOR
    ACALL OUT
    SJMP MONITOR

IN:
    CJNE R0, #00H, JP
    RET

JP:
    DEC R0
    ACALL NIENTY_DEGREEIN
    ACALL SERVO_DELAY
    ACALL ZERO_DEGREEIN
    ACALL CHECKR0

L1:
    JNB P3.0, L2
    SJMP MONITOR

L2:
    JNB P3.1, L1
    SJMP MONITOR
    RET

OUT:
    CJNE R0, #10, JP1
    RET

JP1:
    INC R0
    ACALL NIENTY_DEGREEOUT
    ACALL SERVO_DELAY
    ACALL ZERO_DEGREEOUT
    ACALL CHECKR0

L4:
    JNB P3.0, L3
    LJMP MONITOR

L3:
    JNB P3.1, L4
    LJMP MONITOR
    RET

CHECKR0:
    ACALL HXT_TO_DEC

    MOV B, #0C7H
    ACALL COMNWRT
    ACALL DELAY

    MOV A, R1
    CJNE R1, #0, D1
    SJMP D2

D1:
    ACALL CHECK
    ACALL DATAWRT
    ACALL DELAY

D2:
    MOV A, R2
    ACALL CHECK
    ACALL DATAWRT
    ACALL DELAY

    MOV A, R3
    ACALL CHECK
    ACALL DATAWRT
    ACALL DELAY
    RET

HXT_TO_DEC:
    MOV A, R0
    MOV B, #100
    DIV AB
    MOV R1, A

    MOV A, B
    MOV B, #10
    DIV AB
    MOV R2, A
    MOV R3, B
    RET

CHECK:
    CJNE A, #00, CHECK1
    MOV A, #30H
    RET

CHECK1:
    CJNE A, #1, CHECK2
    MOV A, #31H
    RET

CHECK2:
    CJNE A, #2, CHECK3
    MOV A, #32H
    RET

CHECK3:
    CJNE A, #3, CHECK4
    MOV A, #33H
    RET

CHECK4:
    CJNE A, #4, CHECK5
    MOV A, #34H
    RET

CHECK5:
    CJNE A, #5, CHECK6
    MOV A, #35H
    RET

CHECK6:
    CJNE A, #6, CHECK7
    MOV A, #36H
    RET

CHECK7:
    CJNE A, #7, CHECK8
    MOV A, #37H
    RET

CHECK8:
    CJNE A, #8, CHECK9
    MOV A, #38H
    RET

CHECK9:
    CJNE A, #9, NOTEQ
    MOV A, #39H
NOTEQ:
    RET

COMNWRT:
    MOV P1, B
    CLR P2.0
    CLR P2.1
    SETB P2.2
    ACALL DELAY
    CLR P2.2
    RET

DATAWRT:
    MOV P1, A
    SETB P2.0
    CLR P2.1
    SETB P2.2
    ACALL DELAY
    CLR P2.2
    RET

DELAY:
    MOV R4, #20
HERE2:
    MOV R5, #255
HERE:
    DJNZ R5, HERE
    DJNZ R4, HERE2
    RET

ZERO_DEGREEIN:
    MOV TH0, #0FCH
    MOV TL0, #66H
    SETB P3.2
    SETB TR0
WAIT1:
    JNB TF0, WAIT1
    CLR P3.2
    CLR TF0
    CLR TR0
    RET

ZERO_DEGREEOUT:
    MOV TH0, #0FCH
    MOV TL0, #66H
    SETB P3.3
    SETB TR0
WAIT3:
    JNB TF0, WAIT3
    CLR P3.3
    CLR TF0
    CLR TR0
    RET

NIENTY_DEGREEIN:
    MOV TH0, #0FAH
    MOV TL0, #99H
    SETB P3.2
    SETB TR0
WAIT2:
    JNB TF0, WAIT2
    CLR P3.2
    CLR TF0
    CLR TR0
    RET

NIENTY_DEGREEOUT:
    MOV TH0, #0FAH
    MOV TL0, #99H
    SETB P3.3
    SETB TR0
WAIT4:
    JNB TF0, WAIT4
    CLR P3.3
    CLR TF0
    CLR TR0
    RET

SERVO_DELAY:
    MOV R7, #71
AGAIN4:
    MOV TH0, #00H
    MOV TL0, #00H
    SETB TR0
WAIT5:
    JNB TF0, WAIT5
    CLR TF0
    CLR TR0
    DJNZ R7, AGAIN4
    RET

ORG 500H
    DB 'NO OF FREE SLOTS', 0
END
