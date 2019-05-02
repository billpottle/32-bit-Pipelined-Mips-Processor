# 32-bit-Pipenlined-Mips-Processor
In this project we built a 5 stage pipelined processor in software that executed a subset of MIPS instructions. We used transistors to built logic gates, then used the gates to build up larger components. 

Here is a basic overview of the architecture
![CPU Overview](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/CPUOverview.jpg)

The processor executes parts of 5 instructions at once through the use of various stages. The **Instruction Fetch (IF) Stage** is reasonsible for fetching which instruction to begin. In the **RD Stage**, the processor decodes which instruction to accomplish.  The **Execute (EX)** stage used the Arithmetic and Logic Unit (ALU) to perform the calculation. **The Memory (MEM) Stage** accesses memory if necessary, and the **WriteBack (WB) Stage** writes the result to memory.  

In the diagrams below, a thick line representes up to 32 wires, and three dots signify a jump between the first and last copy of an element. 
IF Stage
![IF Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/IFetch.jpg)
RD Stage
![RD Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/RD.jpg)
EX Stage
![EX Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/EX.jpg)
MEM Stage
![MEM Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/MEM.jpg)
WB Stage
![WB Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/WB.jpg)

Much of the work happens inside the Arithmetic and Logic Unit (ALU). The ALU consists of several sub-sections, which are also used in other parts of the processor. 
ALU Overview
![ALU Overview](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU.jpg)
The AddSub32 unit is responsible for adding and subtracting 32 bit numbers
![ALU AddSub32](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-addsub32.jpg)
The AddSub32 unit uses 32 copies of AddSub
![AddSub](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/ALU-addsub.jpg)
MEM Stage
![MEM Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/MEM.jpg)
WB Stage
![WB Stage](https://github.com/billpottle/32-bit-Pipenlined-Mips-Processor/blob/master/images/WB.jpg)
