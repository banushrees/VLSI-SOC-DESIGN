# VLSI SOC DESIGN 

   <details>
 <summary># DAY -1 INCEPTION OF OPEN SOURCE EDA, OPENLANE AND SKY130PDK</summary>

 <details> 
 <summary>## INTRODUCTION OF CHIPS AND RISCV ARCHITECTURE</summary>
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
--------

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

![Screenshot (28)](https://github.com/user-attachments/assets/455d0c0f-c1d1-4d68-b934-6648a216dbcd)



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
       
</details>

<details>
  <summary>INTRODUCTION TO OPEN TOOLS EDA TOOLS</summary>
  
  TOOL USED : <MARK>OPENLANE</OPENLANE>

  - ### 1.COMMON LINUX COMMANDS USED
      1.  ``cd`` --> change the directory (level up or level down).
      2. `` ls -ltr ``--> list the files present in the folder in chronological order
      3. ``ls --help`` --. to list all the switches and commands(infomatter)

  
![Screenshot (74)](https://github.com/user-attachments/assets/ece6ee34-bc8c-4a18-9262-80754c8fa97b)

- ``OPEN -PDK`` -->> They are compatable used for working with commercial purpose (not to work with EDA's).
- ``lib-ref`` --> contains all the process specific files.
- ``lib -tech`` --> contains all the files specific to tools.
- ``tech-lef`` --> contains all lab information files.

![Screenshot (77)](https://github.com/user-attachments/assets/7b190523-9eb0-495f-bd0e-c4926e0de72d)

- in this library file all the synthesis report will be available
- ``tt``- temperature, ``v`` - voltage.

-----

## 2. DESIGN PREPARATION STEPS

- In this path `` cd /desktop/work/tools/openlane_working_dir/openlane  `` type  ``docker`` to initiate the openlane working file.
- in this design setup state is performed.
- after this type ``./flow.tcl -interactive`` to open OPENLANE.
-  to download the package for further steps type``package require openlane 0.9`` todownload all the packages

  
![Screenshot (78)](https://github.com/user-attachments/assets/8001542b-6f5e-4cf2-b504-be6a3ce373e6)

![Screenshot (83)](https://github.com/user-attachments/assets/4f8b3fc8-c7b7-4309-aa97-b262f9084d9c)


- ``merge lef.py`` is used to merge all the LEF technology file into one folder.
- here the mergedd -LEF will be seen.

  ![Screenshot (86)](https://github.com/user-attachments/assets/29d9605f-85ce-4ea7-901a-ff391f2b0d58)
  

  ![Screenshot (87)](https://github.com/user-attachments/assets/782a7599-c68a-40d1-bf99-f3147de47cdb)

  
  ![Screenshot (88)](https://github.com/user-attachments/assets/96b93215-95bc-47f9-bf52-b195bbe8a77f)

  

-----------

## 3. REVIEW OF FILES AFTER DESIGN PREPARATION AND SYNTHESIS
- after the design preparation , the new run files will be added in the ``picorv32a``.

  ![Screenshot (80)](https://github.com/user-attachments/assets/1ba66d6f-601c-4806-a06d-1dde9baddf2c)
  

- after running , the timing stamp of the processed design files will be stored in the ``tmp`` file.

  ![Screenshot (84)](https://github.com/user-attachments/assets/d5215b61-ee39-45c9-be65-a5eb6eb1bc6c)

- in the below picture all the results , synthesis, report files will be seen inside the stamp file.

![Screenshot (89)](https://github.com/user-attachments/assets/ce585e03-c248-4a19-a1db-d122ecbf5c81)

- In the stamp file ``cofig.tcl`` , all the libraries will be shown.
     - command ``less config .tcl ``.

  ![Screenshot (91)](https://github.com/user-attachments/assets/64a4e0d3-3e97-407d-8b90-928b6778631d)


  ![Screenshot (90)](https://github.com/user-attachments/assets/3b59ecf6-d53c-41d7-812c-edf59df4b5fa)


  - the command files will also be shown in ``less cmds.log``.
 
    ![Screenshot (92)](https://github.com/user-attachments/assets/c26c51c4-6dd6-4193-8a9f-8286cda9bf3f)

 - in the main window the synthesis file will be downloaded ``run_synthesis``.

   
   ![Screenshot (93)](https://github.com/user-attachments/assets/2175472c-08f7-42ac-994d-3c8a3d85788c)

------------

## 4. SYNTHESIS STEPS

- for eg: d flip flop we are calculating the clock percentage.
- d flip flop : 1613.
- total number of cells : 14876.
- the clock percentage = 10.98 %.

![Screenshot (94)](https://github.com/user-attachments/assets/3991fa84-378b-4f3a-a62e-6fb658ed192d)

- to check the results go to time stamp 

![Screenshot (95)](https://github.com/user-attachments/assets/ecc34fe8-08f3-4bd5-a7f5-8630a79ea6c6)


![Screenshot (96)](https://github.com/user-attachments/assets/625f6d70-c4ff-4842-bd78-b838ab3e64c0)

- to check the reports ``less 1_yosys_4.stat.rpt``.
  
![Screenshot (98)](https://github.com/user-attachments/assets/aef1f978-4c52-41e6-9d07-4076dc24ba42)

- to check the report of the timing. ``less 2_openstat.rpt``

![Screenshot (99)](https://github.com/user-attachments/assets/318a6b64-9959-4e2e-89c7-de47c3656195)

![Screenshot (100)](https://github.com/user-attachments/assets/b877087f-94e9-4976-9fab-d859ce64b9eb)

</details>



  




    

