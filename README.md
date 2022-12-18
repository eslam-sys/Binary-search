# Binary-search-project

.MODEL SMALL
.STACK
.DATA
ARR DB 127 DUP(?);define array with maximmum size 127 
OCUR DB 128 DUP(0)
number DB 0
SOLVE DB 0
numberplace db 10
KEY DB 0DH;the input key
;Messages defenitions                
WEL DB "WELCOME TO BINARY SEARCH PROGRAM",13,10,"$"
MSG1 DB "KEY IS FOUND AT POSITION $" 
MSG2 DB "KEY NOT FOUND!!! $"
MSG3 DB "ENTER SIZE: $"   
MSG4 DB "ENTER ELEMENT NUMBER  $"
MSG5 DB "____ $"
MSG6 DB "OVERFLOW ENTER AGAIN","$" 
MSG7 DB "NOTSORTED ENTER AGAIN $"
MSG8 DB "Enter Key $"      
MSG9 DB "ZERO SIZE ENTER AGAIN",13,10,"$"
MSG10 DB "NUMBER OF OCURRENCES IS ","$"
INDEX DB 0
SIZE DB 0
OCC DB 0   
messageinvalidcharacter db "Invalid Character$"
messageinputnumber db "Please Input a number $"


.CODE
.STARTUP    
MOV AX,@DATA ;intialize the data segement
MOV DS,AX
STR:
MOV number,0    


LEA DX,WEL ; display welcome messege
MOV AH,09H
INT 21H ;fetch the instruction in 21h addrees
JMP BEGIN






#Enter arr size

CALL ENTER ; call function to inter the size
CMP AL,0
JE  RE
CALL NEWLINE
MOV SIZE,AL


MOV CL,0 



//<<START ENTER LINE FUNCTION>>//


loop_read_number:  MOV AH,01H  
                    
                   INT 21H    
        
                   CMP AL,0DH      ;compare AL with ASCII code of ENTER
                   JE numbercomplete

                   INC CX   

                   CMP AL,30H      ;compare AL with ASCII code of zero 

                   JL invalidcharacter 

                   CMP AL,39h      ;compare AL with ASCII code of 9
                   JG invalidcharacter 




//START PRINT LINE FUNCTION *******************************************// 
PRINT PROC     ;procedure to print a number     
     
    ;initialize count
    PUSH AX
    PUSH BX
    PUSH CX
    PUSH DX
    MOV CX,0
    MOV DX,0
    label1:
        
        CMP AX,0         ; if ax is zero
        JE print1     
        
        MOV BX,10        ;initialize bx to 10      
         
        ; extract the last digit
        DIV BX       ;put the result at AX and the remendier to DX                 
         
        PUSH DX      ;push it in the stack      
        
        INC CX       ;increment the count      
         
        XOR DX,DX    ;set dx to 0
        JMP label1
    print1:
