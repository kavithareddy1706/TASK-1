TASK-1 
To write a C Program to count the sum of numbers from 1 to n
Here is the program for counting the sum of numbers

![C PROGRAM](https://github.com/kavithareddy1706/TASK-1/assets/173707290/0a146378-fa6a-4fd3-a664-de07930febaa)

Output of the program is given below

![RESULT OF C PROGRAM](https://github.com/kavithareddy1706/TASK-1/assets/173707290/6d02b966-a7ba-4778-86d4-95e8acbf2df7)

Running the program using RISC-V

![CALCULATION OF RISC V PROCESSOR](https://github.com/kavithareddy1706/TASK-1/assets/173707290/6851096b-57e3-4e27-ac75-b97c0bdc0b18)
![USING FAST INSTURCTIONS](https://github.com/kavithareddy1706/TASK-1/assets/173707290/d26e3533-153d-42f9-af78-c9f335e7e702)

TASK-2
Write a C program for a 7 segment display driver

![C PROG FOR 7 SEGMENT](https://github.com/kavithareddy1706/TASK-1/assets/173707290/a36bc53e-8019-4a9c-8758-3e3adcedf0a2)

The below image shows the output

![OUTPUT](https://github.com/kavithareddy1706/TASK-1/assets/173707290/a46c8944-1199-4e75-808e-b77004d54952)

TASK-3
SPIKE Simulation and observation with -O1 and -Ofast.

Code-:

![C PROGR](https://github.com/kavithareddy1706/TASK-1/assets/173707290/208da79d-7b41-4a11-af97-02d07c80a749)

Outputs in C language GCC and RISC-V GCC:

![O1](https://github.com/kavithareddy1706/TASK-1/assets/173707290/347dbd02-296c-4af2-bdfd-b6bbd17cbad0)

In "O1" Mode

![O1m](https://github.com/kavithareddy1706/TASK-1/assets/173707290/e9210af2-8531-431d-945d-8a878c9b8e58)

![O1-2m](https://github.com/kavithareddy1706/TASK-1/assets/173707290/bd227202-cbec-440b-8970-11a91025ed87)

In "Ofast" Mode

![Of1](https://github.com/kavithareddy1706/TASK-1/assets/173707290/801a492e-25cb-48b1-af0f-3083f04c6f5d)

![Of2](https://github.com/kavithareddy1706/TASK-1/assets/173707290/e2151f00-5754-4298-a5d8-6b9097bcc568)

TASK-4
RISC-V Instructions
Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions 

 ADD r1, r2, r3
 SUB r3, r1, r2
 AND r2, r1, r3
 OR r8, r2, r5
 XOR r8, r1, r4
 SLT r10, r2, r4
 ADDI r12, r3, 5
 SW r3, r1, 4
 SRL r16, r11, r2
 BNE r0, r1, 20
 BEQ r0, r0, 15
 LW r13, r11, 2
 SLL r15, r11, r2
 
R-type：
The R-type command format is very clear. In the actual encoding process, the arrangement of encoding positions is meaningful. For example, the encoding position of the three register indexes in different instruction formats are always the same. Index of Rd is at 11-7, Index of rs1 is at 19-15, and Index of rs2 is at 24-20. This is their fixed position. Some instructions may not be useful. The index to the partial register. For example, there is no rs2 in the second instruction type I-type, but there are rs1 and rd and their indexes are in the corresponding positions. For another example, in s-type funct3 is at bits 14-12. The opcode is available in all instruction formats, and the position remains unchanged, always bit 0-6.

![Screenshot 2024-07-08 191747](https://github.com/kavithareddy1706/TASK-1/assets/173707290/23ce93ab-c388-463b-b966-208165af79bb)


I-type：
The upper 12 bits of I-type is an immediate number. The opcode is different from other instruction formats because the corresponding specific operations are different, and other parts are very similar to R-type.

S-type：
The characteristic of S-type instruction is that there is no rd register. In this type of instruction, the immediate is divided into two parts, the first part is in bit11-5, and the second part is in bit4-0. The 5 bits of the immediate 4-0 occupy the position of rd in other instruction formats, and 5-11 occupy the position of funct7. Explain that the command format does not need to write back. That is, read the two values from the two registers and perform the operation together with the immediate, and write the result to the register after the operation is over.

U-Type
A 20-bit immediate is provided in the U-type instruction. The final operation result is related to the 20-bit immediate, and the result is written back to the rd register. The opcode determines the type of operation. There are no funct3, rs1, rs2, and funct7 in U-type. This type of instruction structure is very simple.

B-Type
B-type instructions are mainly used as branch instructions, but they are conditional Branch. It means to decide whether to jump or not need to depend on whether the condition is valid. The B-type machine code structure is shown in Figure 2-1. The instruction does not include rd register and funct7, but contains rs1, rs2, funct3 and immediate. The immediate is divided into two areas. The encoding of B-type instruction immediate is out of order. The reason is not described in detail here. There is a specific article on the official site explaining why it is out of order. In short, it has been verified that the effect on CPU operation function when the immediate number sequence is in this order is very well. But the immediate is disrupted, so it will be decoded when the CPU executes in the future. After decoding, the CPU needs to restore the disrupted immediate in order. For example, when the CPU gets a B-type instruction, the immediate in it is scrambled, and the CPU needs to arrange the immediate in the order of 12-1 to restore the immediate.

J-Type
The format of this instruction is very similar to U-type, it only have Rd register and immediate and opcode. At the same time, the immediate of J-type is also disrupted. That means that the CPU must first put the immediate numbers together to restore the original immediate numbers when decoding.
