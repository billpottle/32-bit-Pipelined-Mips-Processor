# 32-bit-Pipenlined-Mips-Processor
In this project we built a 5 stage pipelined processor in software that executed a subset of MIPS instructions. We used transistors to built logic gates, then used the gates to build up larger components. 

Here is a basic overview of the architecture. The processor takes an array of 32 bits representing wires being on or off, and is able to successfully run programs with a clock cycle time of 50ns (20 mHz)
![CPU Overview](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/CPUOverview.jpg)

The processor executes parts of 5 instructions at once through the use of various stages. The **Instruction Fetch (IF) Stage** is reasonsible for fetching which instruction to begin. In the **RD Stage**, the processor decodes which instruction to accomplish.  The **Execute (EX)** stage used the Arithmetic and Logic Unit (ALU) to perform the calculation. **The Memory (MEM) Stage** accesses memory if necessary, and the **WriteBack (WB) Stage** writes the result to memory.  

In the diagrams below, a thick line representes up to 32 wires, and three dots signify a jump between the first and last copy of an element. 

**IF Stage** The If stage is responsible for fetching the instruction from the instruction memory. It uses an AddSub32 to add four to PC. THere is another AddSub32 to add PC+4 to Target for jumps. Two muxes select if PC should be modified by a branch or a jump and then PC is anded with not reset to reset the circuit when reset is high. PCtemp3 is then flopped to PC on the negative clock edge and the instruction memory is read. 
![IF Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/IFetch.jpg)
**RD Stage** Here we calculate all of the branch and jump conditions and extract the immediate and Rs, rt, and rd fields from the instruction.  The immediate field is then sign extended based on control. Then, the instruction continues to the EX stage and the RD stage sends along information needed to write registers based on a jump and link or branch and link. This stage is also responsible for writting data from the WB stage and reading the values of the RS and RT registers. Lui is also performed in this stage
![RD Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/RD.jpg)
**EX Stage** This is the main execute stage. It has one mux that selects if the alu input is comming from an immediate or from a register. This module is also responsible for calculating the variable shift amounts and performing the shifts. Alu operations with immediate or unsigned operations are performed by setting the correct control bits
![EX Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/EX.jpg)
**MEM Stage** This stage contains logic to determine how much of the 32 bit data word we want to store in the register. The resulting bits (for lb,lh,lbu,lhu) are sign extended. This also contains the logic to store a byte to memory. (Ie, the logic to set DMC0 and DMC1.
![MEM Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/MEM.jpg)
**WB Stage** This stage has a mux to determine if we want to write back the result of an Alu operation or the result of a load from memory. The control determines the write signal that should be sent into RD.  
![WB Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/WB.jpg)

Much of the work happens inside the Arithmetic and Logic Unit (ALU). The ALU consists of several sub-sections, which are also used in other parts of the processor. 

ALU Overview

![ALU Overview](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU.jpg)
The AddSub32 unit is responsible for adding and subtracting 32 bit numbers
![ALU AddSub32](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-addsub32.jpg)
The AddSub32 unit uses 32 copies of AddSub
![AddSub](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-addsub.jpg)
The ALU also utilizes the Logic32 element, and single left and right shifts
![logic32](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-logic32.jpg)
Left Shifts and right shifts are used for mathematical operations. 
![ALU-shiftleft](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-shiftleft.jpg)
![ALU-shiftright](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-shiftright.jpg)
