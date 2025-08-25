# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4200H
MOV B,A
LDA 4201H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY:MVI A,01H
STA 4301H
HLT
```


### Output:
<img width="1897" height="982" alt="image" src="https://github.com/user-attachments/assets/1d669373-a904-41af-8add-790dbcd43594" />

<img width="1902" height="973" alt="image" src="https://github.com/user-attachments/assets/eb09010d-634b-4762-94d2-96bf3cf194ce" />


### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
MOV B,A
MOV A,C
SWAP: SUB B
STA 4300H
HLT
```

### Output:
<img width="1890" height="987" alt="image" src="https://github.com/user-attachments/assets/5e5120c2-f65b-46df-885b-f1eb4b45bb4c" />
<img width="1890" height="978" alt="image" src="https://github.com/user-attachments/assets/8a9bb8a3-6ea3-40de-93c8-b72c4f390dc3" />



### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
MOV B,A
MVI A, 00H
LOOP: ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```

### Output:
<img width="1897" height="979" alt="image" src="https://github.com/user-attachments/assets/b8c67778-6f25-4ed3-94f7-3eb86fa1ed4f" />

<img width="1896" height="968" alt="image" src="https://github.com/user-attachments/assets/df64980b-7d6f-4383-827b-615c3b382f4c" />


### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: MOV A,C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END: MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```


### Output:
<img width="1896" height="967" alt="image" src="https://github.com/user-attachments/assets/bae4da01-22ca-4466-8001-a0f1050894bc" />

<img width="1898" height="998" alt="image" src="https://github.com/user-attachments/assets/1bcf8df1-a332-451b-81d7-0843e507c274" />

## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

