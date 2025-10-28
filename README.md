### **Design and Implementation of an 8-bit SAP-1 Computer**

We designed and implemented an 8-bit computer based on the SAP-1 (Simple-As-Possible) architecture. The project was executed in distinct phases, each focusing on the construction and integration of specific modules using combinational and sequential logic circuits. The implementation was carried out both in simulation using Proteus and on a physical PCB with standard ICs.

### **Phase A: System Timing and Address Management**

In this phase, we constructed the fundamental modules responsible for system timing and managing the program flow.

*   **Clock Pulse Generator:**
    
    *   We designed a clock pulse generator to produce the primary timing signal for the entire computer. This circuit generated a continuous stream of clock pulses that synchronized the operations of all other modules.
        
*   **Program Counter (PC):**
    
    *   We implemented a 4-bit binary program counter capable of counting from 0 to 15.
        
    *   The PC was designed to increment with each clock pulse and place its value onto the system bus.
        
    *   We incorporated control inputs such as **Enable** (to allow counting) and **Reset** (to clear the count to zero) to manage its behavior as required by the control unit.
        
*   **Input Unit and Memory Address Register (MAR):**
    
    *   We constructed the Memory Address Register (MAR) to latch the address present on the bus.
        
    *   The MAR then held this address stable and output it to the RAM module, ensuring the correct memory location was selected for reading or writing.
        
    *   An input unit was also integrated, allowing for manual data entry into the system.
        

### **Phase B: Data Storage and Memory**

This phase involved building the core data storage components of the SAP-1 computer.

*   **Register Bank:**
    
    *   We built several 8-bit registers for temporary data storage and output:
        
        *   **Accumulator (A-register):** This was the primary register for arithmetic operations, holding one of the operands and often the result.
            
        *   **B-register:** This register stored the second operand for ALU operations.
            
        *   **Output Register:** We implemented this register to latch data from the bus and display it, providing a user-visible output.
            
*   **Random Access Memory (RAM):**
    
    *   We constructed the RAM module to store the program instructions and data.
        
    *   Unlike the individual registers, the RAM was organized to hold multiple 8-bit words, each accessible by a unique 4-bit address provided by the MAR.
        

### **Phase C: Instruction Processing and Control**

Here, we developed the modules responsible for controlling the fetch-decode-execute cycle.

*   **Instruction Register (IR):**
    
    *   We implemented the Instruction Register to hold the instruction fetched from memory.
        
    *   The IR was designed to separate the instruction into two parts:
        
        *   The **Opcode** (upper 4 bits), which identified the operation to be performed.
            
        *   The **Operand** (lower 4 bits), which provided the data address or value.
            
*   **Controller / Sequencer:**
    
    *   We designed the Controller/Sequencer, which was the state machine that generated all the necessary control signals.
        
    *   It operated step-by-step, producing the correct sequence of signals (e.g., PC\_INC, MAR\_LOAD, ALU\_SU) during each T-state (clock cycle) to coordinate the actions of the PC, MAR, RAM, registers, and ALU.
        

### **Phase D: The Arithmetic Logic Unit (ALU)**

The final core phase was the construction of the processing engine.

*   **Arithmetic Logic Unit (ALU):**
    
    *   We built the ALU as the computational heart of the SAP-1.
        
    *   Its design was kept simple, supporting two core arithmetic operations: **addition** and **subtraction**.
        
    *   The ALU took one 8-bit input directly from the Accumulator and the other from the B-register.
        
    *   We used a control signal (SU) to select the operation: a low signal for addition and a high signal for subtraction.
        
    *   The output of the ALU was connected back to the data bus, allowing results to be stored back into the Accumulator or the Output Register under the direction of the Controller/Sequencer. This minimal ALU successfully demonstrated the fundamental computational capability of the SAP-1 computer.
