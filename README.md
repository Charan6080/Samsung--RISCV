# Samsung-RISCV

The program is based on the RISC-V architecture and uses open-source tools to teach people about VLSI chip design and RISC-V. The instructor for this internship is Kunal Ghosh Sir.

##  Basic Details

**Name:**  Charan S    
 **College:** Dayananda Sagar College Of Engineering   
**Email ID:** charanmanu64@gmail.com  
**GitHub Profile:** [[Charan6080](https://github.com/Charan6080?tab=repositories)]

---------------------------------------------------------------------------------------------------------------

<details>
<summary><b>Task 1:</b> Task 1 :</b> This Task involves reviewing C-based and RISC-V-based lab videos and performing the compilation of C code using both GCC and the RISC-V compiler</summary>

### C Language based LAB
We need to follow the specified steps to compile any **.c** file on our machine:  
1. Open the bash terminal and navigate to the directory where you want to create your file. Then run the following command:

	```
	leafpad sum1ton.c
	```  
2. This will open the leafpad, allowing you to write in the file you created. Enter the C code to calculate and print the sum of n numbers. After completing your code, press ```Ctrl + S``` to save your file, and then press ```Ctrl + W``` to close the editor.   
3. On your terminal, run the following command:

	```
	gcc sum1ton.c
	./a.out
	```
 ![C Code compiled on gcc Compiler](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%201/C%20based.jpg)
 
### RISC-V based LAB
We need to compile the code again, but this time using the RISC-V GCC compiler. Follow the steps provided:  
1. Open the terminal and run the given command:  

	```
	cat sum1ton.c
	```
![cat Command](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%201/RISC%20v.jpg)

2. Use the **cat** command to display the entire C code in the terminal. Afterwards,compile the code using the RISC-V -O1 GCC compiler:  

	```
	riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
	```
3. The following command is used to display the file details of ```sum1ton.c``` in reverse chronological order, showing the most recently modified files last, 	 along with information such as file permissions, ownership, size, and the timestamp of the last modification:

	```
	ls -ltr sum1ton.c
 	```
 4. To execute the C code on your terminal, use the following command:    

	```
	riscv64-unknown-elf-objdump -d sum1ton.o
	```
![Objdump using -O1 format](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%201/Riscv%201.jpg)

5. The Assembly Language code generated from the C code will be displayed in the terminal. Type ```/main``` to locate the main section of our code.Type ```/q``` to quit from the Objdump.


6. Similarly to the second step, run the following command to compile the code using the RISC-V -Ofast GCC compiler. The subsequent steps will display the 	 
generated assembly code, and you can type ```/main``` to locate the main section of our code:

	```
	riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
	```
 ![Objdump using -Ofast format](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%201/Riscv%202.jpg)

 ### *Descriptions of the keyword used in command above *  
* **-mabi=lp64:** Specifies the ABI (Application Binary Interface) as ```lp64```, which supports 64-bit integers, long, and pointer sizes. This ABI is intended for 64-bit RISC-V architecture.  
* **-march=rv64i:** Defines the target architecture as ```rv64i```, which represents the 64-bit RISC-V base integer instruction set, ensuring compatibility with the 64-bit architecture.  
* **riscv-objdump:** A disassembler tool for RISC-V binaries that provides insights into the code structure, assisting in debugging.  
* **-Ofast:** The option -Ofast in the command ```riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c``` is a compiler optimization flag used with the GNU Compiler Collection (GCC). This flag is used to instruct the compiler to optimize the generated code for maximum speed. The use of ```-Ofast``` is typically chosen for applications where execution speed is critical and where deviations from standard behavior are acceptable. However, it's important to test thoroughly, as this level of optimization can introduce subtle bugs, especially in complex calculations or when strict compliance with external standards is required.  
* **-O1:** A basic optimization level that balances improved execution speed and reduced code size with minimal impact on compilation time. It is suitable for applications requiring moderate optimization without extensive resource usage.  
</details>

----------------------------------------------------------------------------------------------------------------

<details>
<summary><b> Task 2 :</b> Performing SPIKE simulation and debugging the C code using Spike's debugging mode </summary> 

  ### Testing the Spike Simulator  
The aim is to execute the ```oddoreven.c``` program using both the ```gcc compiler``` and the ```riscv compiler```, conforming that both compilers produce identical output on the terminal. To compile the code with the **gcc compiler**, use the command below:
  
```
gcc oddoreven.c  
./a.out
```

And to compile the code using **RISCV Compiler**, use the following command: 
 
```
spike pk oddoreven.o
```
 Open the debugger in another terminal by using the following command.

```
$ spike -d pk sum_1ton.o
```

* The debugger will be opened in the terminal. Now, debugging operations can be performed as shown in the following snapshot.

![Spike Simulation and Debugging](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%202/Compiled%20C%20code%20using%20spike.png)

#### The following snapshots display the RISCV objdump output generated using the **-O1** and **-Ofast** optimization options.

RISCV Objdump with -O1

![Objdump in -O1](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%202/Objdump%20O1%20format.png)

RISCV Objdump with -Ofast 

![Objdump in -Ofast](https://github.com/Charan6080/Samsung--RISCV/blob/main/TASK%202/Objdump%20Ofast%20format.png)
</details>

----------------------------------------------------------------------------------------------------------------


<details>
	
<summary><b> Task 3 :</b> RISC-V Instruction Types </summary>

### RISC-V Registers
RISC-V is a widely adopted open-source instruction set architecture that features 32 registers, each 32 bits wide. 

### Saved, Temporary, and Argument Registers
The remaining registers are divided into saved, temporary, and argument categories:

- **Saved Registers (s0-s11)**: These registers (x8, x9, x18-x27) store variables that need to be preserved across function calls.
- **Temporary Registers (t0-t6)**: These registers are used for intermediate calculations and temporary data storage.
- **Argument Registers (a0-a7)**: These registers (x10-x17) are used to pass arguments to functions and store return values.

![image](https://github.com/user-attachments/assets/af936f03-ded7-4d6a-9e4b-38cf37695620)

RISC-V instructions are all 32 bits in length , and they are categorized into six main instruction formats: R-type, I-type, S-type, B-type, U-type, and J-type. These formats determine how the instruction fields are laid out.
### 1.R-Type (Register-Register Instructions)
R-type instructions are used for arithmetic and logical operations between two registers. They operate on two source registers (rs1 and rs2) and store the result in a destination register(rd).
![image](https://github.com/user-attachments/assets/e01d8bbe-710e-4927-8fec-51f162d384ca)

- funct7: Used to specify variations of the instruction (e.g., add vs. sub).
- rs1, rs2: Source registers.
-funct3: Determines the operation type (e.g., addition, subtraction, etc.).
-rd: Destination register.
-opcode: Specifies the instruction class (0110011)
- - Example: add a0, a1, a2

### 2. I-Type (Immediate Instructions)
I-type instructions involve operations between a register (rs1) and an immediate value, with the
result stored in a destination register (rd). These are also used for loads and certain
control-flow instructions.
![image](https://github.com/user-attachments/assets/3d035720-dc62-45d5-9a2c-2a6b263ade74)
- imm[11:0]: 12-bit immediate value (sign-extended if needed).
- rs1: Source register.
- funct3: Determines the operation type.
- rd: Destination register.
- opcode: Specifies the instruction class.0010011
- -Example: addi a0, a1, 10

### 3.S-Type (Store Instructions)
S-type instructions store data from a register into memory at an address computed from a base
register (rs1) and an immediate offset.
![image](https://github.com/user-attachments/assets/eb224238-c0ef-42ca-82d0-c42ed8293320)
- imm[11:5] & imm[4:0]: Immediate value split into two fields.
- rs2: Register whose data is being stored.
- rs1: Base address register.
- funct3: Specifies the type of store (e.g., byte, word).
- opcode: Specifies the instruction class.
- Example: sw a2, 8(a0),0100011

### 4. B-Type (Branch Instructions)
B-type instructions perform conditional branches based on comparisons between two registers
(rs1 and rs2) and an offset for the target address.
![image](https://github.com/user-attachments/assets/7f138e24-cb0c-4506-9875-c4b3b14a2670)
- imm: Immediate value for the branch target address (split into imm[12|10:5] and
- imm[4:1|11]).
- rs2: Second comparison register.
- rs1: First comparison register.
- funct3: Specifies the type of comparison (e.g., equal, less than).
- opcode: Specifies the instruction class.1100011

### 5.U-Type (Upper Immediate Instructions)
U-type instructions are used to load a 20-bit immediate into the upper 20 bits of a register (rd).
![image](https://github.com/user-attachments/assets/d6269585-d85a-4675-b13f-4ae4ed1ea05a)
- imm[31:12]: 20-bit immediate value.
- rd: Destination register.
- opcode: Specifies the instruction class.011011.
- Example: lui a0, 0x12345

### 6.J-Type (Jump Instructions)
J-type instructions perform an unconditional jump to a target address computed using an
immediate offset. The address is relative to the current program counter.
![image](https://github.com/user-attachments/assets/9b35cad7-8fd8-41da-be46-aec4cf712657)
- imm: 20-bit immediate value split across fields.
- rd: Destination register (stores the return address).
- opcode: Specifies the instruction class.1101111
- Example: jal ra, 0x100

32-bit instruction encoding for the 15 unique RISC-V instructions extracted from the objdump.

### 1. lui(Load Upper Immediate)
- Instruction: lui a0, 0x2b
- Format: U-type
- Fields:
- imm[31:12]: 00000000000000101011 (0x2b)
- rd: 10110 (a0)
- opcode: 0110111 (for lui)
- 32-bit Hexadecimal: 0x002b537

### 2. addi (Add Immediate)
- Instruction: addi sp, sp, -32
- Format: I-type
-  Fields:
 - imm[11:0]: 1111111111110000 (-32 in 2's complement)
- rs1: 00100 (sp)
- funct3: 000 (add immediate)
- rd: 00100 (sp)
- opcode: 0010011 (for addi)
- 32-bit Hexadecimal: 0xfe010113

### 3. sd (Store Doubleword)
 - Instruction: sd ra, 24(sp)
 - Format: S-type
 - Fields:
 - imm[11:5]: 0000000 (upper 7 bits of offset 24)
 - rs2: 00001 (ra)
 - rs1: 00100 (sp)
 - funct3: 011 (store doubleword)
 - imm[4:0]: 11000 (lower 5 bits of offset 24)
 - opcode: 0100011 (for store)
 - 32-bit Hexadecimal: 0x00350513

### 4. jal (Jump and Link)
- Instruction: jal ra, 0x10438
- Format: J-type
- Fields:
- imm[20]: 0
- imm[10:1]: 1000010111
- imm[11]: 0
- imm[19:12]: 00000100
- rd: 00001 (ra)
- opcode: 1101111 (for jump)
- 32-bit Hexadecimal: 0x35000ef

### 5. lw (Load Word)
- Instruction: lw a1, 12(sp)
-  Format: I-type
-  Fields: imm[11:0]: 000000001100 (12 in binary)
-  rs1: 00100 (sp)
-  funct3: 010 (load word)
-  rd: 01001 (a1)
-  opcode: 0000011 (for load)
-  32-bit Hexadecimal: 0x00c52083

### 6. andi (AND Immediate)
-  Instruction: andi a5, a1, 1
-  Format: I-type
-  Fields:
-  imm[11:0]: 000000000001 (1 in binary)
-  rs1: 01001 (a1)
-  funct3: 111 (AND operation)
-  rd: 01010 (a5)
-  opcode: 0010011 (for ANDI)
-  32-bit Hexadecimal: 0x00157913

### 7. bnez (Branch Not Equal Zero)
-  Instruction: bnez a5, 0x100fc
-  Format: B-type
-  Fields:
-  imm[12]: 0
-  imm[10:5]: 000011
-  rs2: 00000 (zero)
-  rs1: 01010 (a5)
-  funct3: 001 (BNE)
-  imm[4:1]: 1100
-  imm[11]: 0
-  opcode: 1100011
-  32-bit Hexadecimal: 0x02706e63

### 8. ret (Return from Subroutine)
-  Instruction: ret
-  Format: I-type (special case of jalr)
-  Fields:
-  imm[11:0]: 000000000000
-  rs1: 00001 (ra)
-  funct3: 000
-  rd: 00000 (zero)
-  opcode: 1100111 (for JALR)
-  32-bit Hexadecimal: 0x00008067

### 9. auipc (Add Upper Immediate to PC)
-  Instruction: auipc a5, 0xfff
-  Format: U-type
-  Fields:
-  imm[31:12]: 000000000000111111111
-  rd: 01010 (a5)
-  opcode: 0010111
-  32-bit Hexadecimal: 0x0fff057

### 10. ld (Load Doubleword)
-  Instruction: ld ra, 24(sp)
-  Format: I-type
-  Fields:
-  imm[11:0]: 000000001100 (24 in binary)
-  rs1: 00100 (sp)
-  funct3: 011 (load doubleword)
-  rd: 00001 (ra)
-  opcode: 0000011
-  32-bit Hexadecimal: 0x01852083

### 11. jalr (Jump and Link Register)
-  Instruction: jalr ra, 0(a0)
-  Format: I-type
-  Fields:
-  imm[11:0]: 000000000000 (0 in binary)
-  rs1: 00101 (a0)
-  funct3: 000
-  rd: 00001 (ra)
-  opcode: 1100111
-  32-bit Hexadecimal: 0x000280e7

### 12. beqz (Branch Equal Zero)
-  Instruction: beqz a5, 0x10120
-  Format: B-type
-  Encoding: Similar to bnez but with funct3 = 000 (BEQ).

### 13. add (Add Registers)
-  Instruction: add a0, sp, zero
-  Format: R-type
-  Fields:
-  funct7: 0000000
-  rs2: 00000 (zero)
-  rs1: 00100 (sp)
-  funct3: 000
-  rd: 01010 (a0)
-  opcode: 0110011
-  32-bit Hexadecimal: 0x00004533
  
