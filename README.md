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



#Enter arr size

CALL ENTER ; call function to inter the size
CMP AL,0
JE  RE
CALL NEWLINE
MOV SIZE,AL


MOV CL,0 
