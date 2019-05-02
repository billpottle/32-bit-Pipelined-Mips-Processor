
**testaritmetic.src:** This file tests all of the arithmetic instructions. ALU instructions with 2 registers, ALU instructions with a register and an immediate, shift instructions with a specified shift amount, and shift instructions with a variable shift amount. This should include:

addi,addiu,slti,sltiu,sll,srl,sllv,srlv,srav,add,addu,sub,subu,slt,sltu


**testlogical.src:** This file contains the logical instructions. THis includes some ALU instrutions. We use reg-reg and reg-imm tests. THis includes: 

andi,ori,xori,and,or,xor,nor

**testloadstore.src:** This file tests the load and store operations by initializing a register, and then writing it to memory and then reading it back and writting it to the register. We tested all of the operations here to get all parts of the datapath. These are: 

lb,lh,lhu,lbu,lw,sw,sb,sh

**testbranch.src:** This file tests the rest of the operations (including lui). Success is defined as PC being updated correctly to the jump or branch address. This is the rest of the instructions: 

j, jal, beq, bne, blez, bgtz, jr, jalr, bltz, bgez, bltzal, bgezal, lui. 
