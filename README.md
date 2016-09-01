# mit-cheat-sheet

MIT Instructions Cheat Sheet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

MOV: Move
		2 operands
		1 byte operation
		e.g MOV Rd, Rs copies data from source to destination

MVI: Move Immediate
		load a constant into a register
		loads 8 bits of the second byte into the register specified
		e.g MVI A, 82H

OUT: Output to port
		send a databyte to an output device

IN:  Input from port
		read a databyte from an output device
		e.g IN 00H

HLT: Halt 
		Stop Processing and wait
		e.g OUT 01H

NOP: No Operation
		Do not perform any operation

Arithemetic OPerations:
**********************

ADD: Add
		This is a 1 byte instruction
		Adds content of register into accumulator
		e.g ADD C : Acc <- Acc + C

ADI: Add Immediate
		This is a 2 byte instruction
		Adds the second byte(constant) to the contents of the accumulator

SUB: Subtract
		This is a 1 byte instruction
		Subtracts the content of register from accumulator
		e.g SUB C : Acc <- Acc - C

SUI: Subtract Immediate
		This is a 2 byte instruction
		Subtracts the second byte rom the contents of the accumulator

INR: Increment
		This is a 1 byte instruction
		Increase the contents of register by 1
		All flags accept the CY are affected

DCR: Decrement
		This is a 1 byte instruction
		Decreases the contents of register by 1		
		All flags except the CY are affected

Logic Operations:
*****************

ANA: Logical AND 
		with Accumulator
		This is a 1 byte instruction
		Operand is a Register

ANI: AND Immediate 
		with Accumulator 				
		This is a 2 byte instruction
		Operand is Constant

ORA: Logically OR 
		with Accumulator
		This is a 1 byte instruction
		Operand is Register

ORI: OR Immediate 
		with Accumulator
		This is a 2 byte instruction
		Operand is constant

XRA: XOR 
		with Accumulator
		This is a 1 byte instruction

XRI: XOR immediate
		with Accumulator
		This is a 2 byte instruction

CMA: Complement
		complements contents of accumulator
		This is a 1 byte instruction

Branch Operations:
******************
Uncondtional Jump:

	JMP: Jump
			This is a 3 byte instruction
			second and third bytes specify the higher and lower bytes respectively

Conditional Jump: Check Flag conditions and makes decision to change sequence of program or not

	JC: Jump On Carry
	JNC: Jump On No Carry
	JZ: Jump On Zero
	JNZ: Jump on Non Zero
	JP: Jump on Plus
	JM: Jump on Minus
	JPE: Jump on Even Parity
	JPO: Jump on Odd Parity
	
Additional Data Transfer and 16 bit Arithmetic Instructions:
***********************************************************
From Memory to Microprocessor:

	LXI Rp: load Register Pair Immediate
				loading 16 bit data in register pairs
				e.g LXI H, 2050H ---> H[ 20 ][ 50 ]L

	LDAX B/D: Load Accumulator Indirect
				This is 1 byte instruction
				copies data from memory location into accumulator
				addressing mode is indirect

	LDA 16bit: Load Accumulator Direct
				This is a 3 byte instruction
				It copies data from the memory location specified by 16 bit data
				addressing mode is indirect

From Microprocessor to Memory

	STAX B/D: Store Accumulator Indirect
				Copies data from the accumulator to the memory location specified by BC or DE

	STA	16bit: Load 8-bit data in memory
				This is a 3 byte instruction
				copies data from the accumulator into the memory location specified by the 16 bit operand.

Arithmetic Operations Related to 18 bits or Register Pairs
**********************************************************

INX Rp: Increment Register Pair
			This is a 1 byte instruction.
			contents of the two registers are taken as a single 16 bit number and increases the contents by 1.

DCX Rp: Decrement Register Pair
			This is a 1 byte instruction.
			It decreases the 16 bit contents of register pair by 1


Logic Operations Rotate
***********************

RLC: Rotate Accumulator left
		Each bit is shifted to the adjacent left position. Bit D7 become D0.
		CY flag is modified according to bit D7.

RAL: Rotate Accumulator left through carry
		Each bit is shifted to the adjacent left position. Bit D7 becomes carry bit, carry bit is shifted to D0.
		Carry flag is modified

vice versa for RRC and RAR.

Logic Operations Compare:
************************

CMP R/M: Compare with Accumulator
			This is a 1 byte instruction
			Compares data byte in register or memory
			if A < R/M : CY Flag is set, zero flag is reset.
			if A = R/M : Zero flag is set, CY flag is reset.
			if A > R/M : CY flag and Zero flags are reset.

CPI 8bit: Compare Immediate with Accumulator
			This is a 2 byte instruction
			Compares second byte with A
			same flags set as above operation

What actually happens:
CMP R/M = data at A - data at R/M
			thus when A is smaller, the carry flag is set as borrow is there and zero flag is reset
			when equal the resultant being 0, the zero flag is set and carry flag is reset.
			when A is greater, both flags are reset as neither borrow occurs, nor is the result 0.

			






					 		 
							



General Concepts:
^^^^^^^^^^^^^^^^
Flags: 

CY: flag acts as both carry in addition, and borrow in subtraction.

flags present:
	Carry Flag
	Zero Flag
	Sign Flag
	Parity FLag

Application of Rotate Instructions:

They are used in arithmetic divide and multiply operations for serial data transfer.
