# VLSI SOC DESIGN 

   <details>
 <summary>INTRODUCTION OF CHIPS</summary>
      
   ## CHIP NAME:` QFN - 48 `
![Screenshot (14)](https://github.com/user-attachments/assets/9e4a187f-ad04-4e36-820a-37372000c6a3)



- Each side of this has 12 pins.
- chip is connected to each pins.


  ![Screenshot (15)](https://github.com/user-attachments/assets/eb160ae7-5324-4d1a-8662-423b7dc3e66f)
   
 important components of this chips are  PADS, core, dies.
  - <ins>CORE</ins> is area where all the digital logic chips are embedded.
  - <ins>PADS</ins> is used to send the signals inside the chip and vise versa.
  - <ins>DIE</ins> is used entire size of the chip where all pins  are embedded.

![Screenshot (18)](https://github.com/user-attachments/assets/bc17abfb-f80c-47c7-92dc-8ff4c6c86f3d)


- A typical chip contains of SoC(RISC-V) , SRAM, ADC, DAC, PLL, GPIO, SPI.
- SRAM, PLL, ADC, DAC  are called ` FOUNDRY IP'S `(factory where all the chips are manufactured).
- FOUNDRY IP's has some files which will help us to communicate the parts present  in the chip (Foundry IP parts).
- MACROS's are digital logic components contains of  RISCV (Soc), SPI, GPIO  Bank.
- IP's (Intellilectual Property )is an intelligent technique to built the building blocks.

</details>

<details>
<summary>INTRODUCTION TO RISC-V ARCHITECTURE</summary>

![Screenshot (19)](https://github.com/user-attachments/assets/b1930879-780a-4052-a572-5fe76917728b)

- RISC V is Instruction set architecture (eg.C-program has to be typed on the hardware which has a particular layout )
- The C-program is compiled on the assembly launguage program.
- The assembly launguage program later on converted to machine launguage (eg 0101110)  Hexadecimal--> binary.
- The interface that present between the RISCV  and layout is HDL( Hardware Description Launguage).

</details>

<details>
<summary>SOFTWARE APPLICATION TO HARDWARE IMPLEMENTATION</summary>

Interaction between the software apps and HardWare happens by the help of System software .

![Screenshot (19)](https://github.com/user-attachments/assets/abacd6ff-7437-495c-9bfd-2aad14de8ea6)

### components of system software

 #### OS -> COMPILER -> ASSEMBLER
 1. <mark>OS</mark> - Operating System
   -Handles i/o operations
   - Allocate Memory
   - Low level system functions

 2. <mark>COMPILER</mark>
    -converts c,c++ VB, Java, to instructions depends on what kind of hardware it is (eg..exe file).

 3. <mark>.ASSEMBLER</mark>
   - converts instrction set  into machine launguage (eg 101011)

 ![Screenshot (22)](https://github.com/user-attachments/assets/4230546d-cf87-4026-a798-da9f708b70ae)


 - The instructions set from the compiler act as a interface from C launguage to the HardWare machine launguage .
 - HardWare only understands 0 and 1.
 - output of the assembler is binary.
 - first the instruction set specification will be converted to binary by assembler then the RTL of the H/W  will add the specs from instructions set in the  form of binary.
 - Then it is synthesized by netlist from RTL  and then implemented by H/W.

</details>
 
 <details>
<summary>SOC DESIGN AND OPENLANE</summary>

## INTRODUCTION TO ALL COMPONENTS OF OPENSOURCE DIGITAL ASIC DESIGN

![Screenshot (102)](https://github.com/user-attachments/assets/89fb4085-3508-496b-8300-744588779981)

- <mark>ASIC</mark> is the combination of RTL designs, EDA tools , PDK datas.
- <mark>PDK</mark> (Process Design Kit)  is the interface between fabrication and designers.
- it is the collection of file used to model a fabrication process for the EDA tools used to design and IC.
           (eg 1. process design rules : DRC, LVS
               2. Device models.
               3. Digital standared cell libraries.
               4. i/o libraries. 
- OSU (Operating System Unit) team reported 327 MHz - post layout clock frequency for a single cycle RV32i CPU.
- A pipelined version can achieve > 1 GHz clock 130nm fast.

</details>


<details>
<summary>SIMPLIFIED RTL TO GDS FLOW</summary>

![Screenshot (28)](https://github.com/user-attachments/assets/69930102-65c7-4d44-8bb9-c9eca7271cc8)

1. ### SYNTHESIS
    - converts RTL to a circuit out of components from the standard cell library.
    - standard cell have a regular layout , each has different views/models.
          ->Electrical : HDL, SPICE.
          -> Layout.
2. ### FLOOR PLANNING DN POWER PLANNING
    - <mark>chip floor planning</mark> : partition the chip in between different system building blocks & place the i/o pads.
    - <mark>macro floor planning</mark> : it focuses on dimensions pin locations , row definitions.
    - <mark> power planning</mark> power unit is constructed typically . it ensures power is gone to all the parts. eg.power pads (vdd, vss),power straps ,power
      rings.
      
3. ### PLACEMENT
     - place the cells on the floor plan rows, aligned with the sites.
     - usually done in two steps : global & detailed.
        1.<mark>global placement</mark> tends to find optimal position to place cells, but the cells may overlap.
        2.<mark>detailed placement</mark> inthis position from the golbal placements is slightyly altered.

4. ### CTS (Clock Tree Synthesis)
     - creates a clock distribution network with minimum skew(zero is hard to achieve)
     - it is always good in shape.
     - it is usually in tree shape.       
5. ### ROUTING
     - implement the interconnect using the available metal layers.
     - to each metal layer the PDK finds thickness pitch.
     - metal tracks form a routing grid.
     - routing grid is huge.
     - divide and conquer.
   there are two types <mark>Global and detailed routing</mark>
       1. <mark>global routing</mark> :generates routing guides.
       2. <mark>detailed routing</mark> :uses the routing guide to implement the actual wiring.
          
6. ### SIGN-OFF
    - <Mark>Physical verification</mark> 
         - DRC (Design Rule Check).
         - LVS (Layout Vs Schematic).
    - <mark>timing verification</mark>
          - STA (Static Timing Analysis).
      
    </details>

    <details>
       <summary>INTRODUCTION TO OPENLANE AND ASIC DESIGN FLOW</summary>

    - <mark>OPENLANE</mark> started as an opensource flow for a true open source tape out expriment.
    - <mark>strive</mark> is a family of open everything SoC's (eg openPDK, open EDA, open RTL).
    - its main goal is to produce a clean GDS Iwith no human intervention (no-human-in-the-loop).clean means no DRC , LVS violations,no timing violations.
    - Tuned for SKYWATER 130nm open pdk.

----


 ## DETAILED ASIC DESIGN FLOW

 ![Screenshot (36)](https://github.com/user-attachments/assets/bcebd51f-9483-451d-8248-02b8eb5b585c)


- The flow starts with RTL synthesis and ends with GDS II  format.but to function it needs PDK.
- the RTL is fed to yosys with design constrains.
- the RTL translates into logic circuit using generic components.
- the circuit can be optimised and mapped into cells from this and thers library using ABC  .
- The design exploration utility is also used for registration testing.

after the testing follows the fabrication.
   -DFT used for
   1.scan insertion
   2.ATPG(Automatic Test Pattern Generation).
   3.test patterns compaction.
   4.fault coverage
   5.fault simulation
   
- After this PnR (place and routing) will come also called as automated pnr.
- this followed by synthesis ,this step is also called as LEC(Logic Equivalence Checking).
- everytime the netlist is modified ,verification will be performed.
-  post placement optimisation and CTS modifies the netlist
       

  
   
