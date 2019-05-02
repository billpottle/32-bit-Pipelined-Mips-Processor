The test files are contained in the source files. In all files we set the vecotrs up and then chose which ones to analyze. We wrote initial values to the registers and then gave instructions and control that set the instructions up. We tried to use instructions that would use all of the different parts of the datapath. Once the instruction decoding was implemented, then we set the control bits based on what we descovered would be necessary in the datapath testing phase. Once we correctly executed the bootcode, we were able to directly include our tests in the file test.s
	The file test.s, combined with the bootcode, tests all implemented MIPS instructions. The file jumps forwards and backwards, and includes code that is not intended to ever be executed. Therefore, if the PC is not updated correctly, then the registers will have a different value in the end. We analyzed all of the registers in irsim and used the included test.src file.
  
**testaritmetic.src:** This file tests all of the arithmetic instructions. ALU instructions with 2 registers, ALU instructions with a register and an immediate, shift instructions with a specified shift amount, and shift instructions with a variable shift amount. This should include:

addi,addiu,slti,sltiu,sll,srl,sllv,srlv,srav,add,addu,sub,subu,slt,sltu


**testlogical.src:** This file contains the logical instructions. THis includes some ALU instrutions. We use reg-reg and reg-imm tests. THis includes: 

andi,ori,xori,and,or,xor,nor

**testloadstore.src:** This file tests the load and store operations by initializing a register, and then writing it to memory and then reading it back and writting it to the register. We tested all of the operations here to get all parts of the datapath. These are: 

lb,lh,lhu,lbu,lw,sw,sb,sh

**testbranch.src:** This file tests the rest of the operations (including lui). Success is defined as PC being updated correctly to the jump or branch address. This is the rest of the instructions: 

j, jal, beq, bne, blez, bgtz, jr, jalr, bltz, bgez, bltzal, bgezal, lui. 
