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
RISC-V Instructions:
Identify various RISC-V instruction type (R, I, S, B, U, J) and exact 32-bit instruction code in the instruction type format for below RISC-V instructions 

![Screenshot 2024-07-08 192546](https://github.com/kavithareddy1706/TASK-1/assets/173707290/98e91c13-93f6-4b2c-94b2-cd12dafadd55)


![Screenshot 2024-07-08 193209](https://github.com/kavithareddy1706/TASK-1/assets/173707290/738647e4-4c75-4452-a57f-70d1827a03fe)

 
R-type：
The R-type command format is very clear. In the actual encoding process, the arrangement of encoding positions is meaningful. For example, the encoding position of the three register indexes in different instruction formats are always the same. Index of Rd is at 11-7, Index of rs1 is at 19-15, and Index of rs2 is at 24-20. This is their fixed position. Some instructions may not be useful. The index to the partial register. For example, there is no rs2 in the second instruction type I-type, but there are rs1 and rd and their indexes are in the corresponding positions. For another example, in s-type funct3 is at bits 14-12. The opcode is available in all instruction formats, and the position remains unchanged, always bit 0-6.

![Screenshot 2024-07-08 191747](https://github.com/kavithareddy1706/TASK-1/assets/173707290/23ce93ab-c388-463b-b966-208165af79bb)


I-type：
The upper 12 bits of I-type is an immediate number. The opcode is different from other instruction formats because the corresponding specific operations are different, and other parts are very similar to R-type.

![Screenshot 2024-07-08 192846](https://github.com/kavithareddy1706/TASK-1/assets/173707290/5ecddf03-1c33-4095-b810-f6c5d011efc1)


S-type：
The characteristic of S-type instruction is that there is no rd register. In this type of instruction, the immediate is divided into two parts, the first part is in bit11-5, and the second part is in bit4-0. The 5 bits of the immediate 4-0 occupy the position of rd in other instruction formats, and 5-11 occupy the position of funct7. Explain that the command format does not need to write back. That is, read the two values from the two registers and perform the operation together with the immediate, and write the result to the register after the operation is over.

![Screenshot 2024-07-08 192130](https://github.com/kavithareddy1706/TASK-1/assets/173707290/64a896f9-d4a7-41c3-bbb5-6330449f6471)


U-Type:
A 20-bit immediate is provided in the U-type instruction. The final operation result is related to the 20-bit immediate, and the result is written back to the rd register. The opcode determines the type of operation. There are no funct3, rs1, rs2, and funct7 in U-type. This type of instruction structure is very simple.

![Screenshot 2024-07-08 192027](https://github.com/kavithareddy1706/TASK-1/assets/173707290/1d667757-8091-43c4-b641-1fcf0a2f539b)


B-Type: 
B-type instructions are mainly used as branch instructions, but they are conditional Branch. It means to decide whether to jump or not need to depend on whether the condition is valid. The B-type machine code structure is shown in Figure 2-1. The instruction does not include rd register and funct7, but contains rs1, rs2, funct3 and immediate. The immediate is divided into two areas. The encoding of B-type instruction immediate is out of order. The reason is not described in detail here. There is a specific article on the official site explaining why it is out of order. In short, it has been verified that the effect on CPU operation function when the immediate number sequence is in this order is very well. But the immediate is disrupted, so it will be decoded when the CPU executes in the future. After decoding, the CPU needs to restore the disrupted immediate in order. For example, when the CPU gets a B-type instruction, the immediate in it is scrambled, and the CPU needs to arrange the immediate in the order of 12-1 to restore the immediate.

![Screenshot 2024-07-08 192941](https://github.com/kavithareddy1706/TASK-1/assets/173707290/c0dd9fd8-68c2-4fae-afeb-c3c02a8e5869)


J-Type:
The format of this instruction is very similar to U-type, it only have Rd register and immediate and opcode. At the same time, the immediate of J-type is also disrupted. That means that the CPU must first put the immediate numbers together to restore the original immediate numbers when decoding.

![Screenshot 2024-07-08 191941](https://github.com/kavithareddy1706/TASK-1/assets/173707290/c56807d8-65dc-4f23-80d6-aa7cacc30363)

32-bit pattern for the given instructions:

1 -> ADD r1, r2, r3 =>
     32 bit instruction: 0000000_00011_00010_000_00001_0110011

2 -> SUB r3, r1, r2 =>
     32 bit instruction: 0100000_00010_00001_000_00011_0110011

3 -> AND r2, r1, r3 =>
     32 bit instruction: 0000000_00011_00001_111_00010_0110011

4 -> OR r8, r2, r5 =>
     32 bit instruction: 0000000_00101_00010_110_01000_0110011

5 -> XOR r8, r1, r4 =>
     32 bit instruction: 0000000_00100_00001_100_01000_0110011

6 -> SLT r10, r2, r4 =>
     32 bit instruction: 0000000_00100_00010_010_01010_0110011

7 -> ADDI r12, r3, 5 =>
     32 bit instruction: 000000001001_00011_000_01100_0010011

8 -> SW r3, r1, 4 =>
     32 bit instruction: 0000000_00011_00001_010_00100_0100011

9 -> SRL r16, r11, r2 =>
     32 bit instruction: 0000000_00010_01011_101_10000_0110011

10 -> BNE r0, r1, 20 =>
      32 bit instruction: 0000001_00001_00000_001_01000_1100011

11 -> BEQ r0, r0, 15 =>
      32 bit instruction: 0000000_00000_00000_000_11110_1100011

12 -> LW r13, r11, 2 =>
      32 bit instruction: 000000000010_01011_010_01101_0000011

13 -> SLL r15, r11, r2 =>
      32 bit instruction: 0000000_00010_01011_001_01111_0110011

