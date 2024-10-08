# Digital VLSI SoC Design and Planning
---
Sky130 Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
SKY130_D1_SK1 - How to talk to computers
SKY_L3 - From Software Applications to Hardware

---



# DAY1
## _Processor/SoC:_
    
![processor peripherals](https://github.com/user-attachments/assets/538bb221-9f02-474e-9896-c19dc622d94a)


    

## Left Side Components

### JTAG, UART0, QSPI1, I2C0, clk, reset:
- **JTAG (Joint Test Action Group)**: Used for debugging and testing the chip during development.
- **UART0 (Universal Asynchronous Receiver-Transmitter)**: A serial communication protocol for transmitting and receiving data between devices.
- **QSPI1 (Quad Serial Peripheral Interface)**: A flash memory interface that communicates at high speeds.
- **I2C0 (Inter-Integrated Circuit)**: A multi-master, multi-slave protocol used for communication between integrated circuits.
- **clk**: The clock signal that synchronizes operations across the chip.
- **reset**: Resets the system to a predefined state.

### 1. JTAG-UART FTDI (Left Side):
This block connects the processor to a USB interface for debugging purposes, likely using an FTDI (Future Technology Devices International) chip for communication.

### 2. QSPI1-Flash (Left Side):
This interface is connected to flash memory, which stores non-volatile data (like firmware or configuration settings) for the processor.

### 3. I2C0-EEPROM (Left Side):
A serial communication interface connected to an EEPROM (Electrically Erasable Programmable Read-Only Memory), used to store small amounts of data like configuration parameters that need to be preserved across reboots.

---

## Top, Bottom, and Right Side Components

### 4. SDRAM (Top, Bottom, and Right Side):
**SDRAM (Synchronous Dynamic Random-Access Memory)**: Provides volatile memory for the processor to store data temporarily during execution. The processor can have multiple interfaces connected to SDRAM chips, as shown on the top, bottom, and right sides.

### 5. Direct I2C, QSPI, GPIO (Top Side):
This set of interfaces provides direct communication using I2C and QSPI protocols. The GPIO (General Purpose Input/Output) pins can be used for various control or communication tasks, like driving LEDs, receiving button inputs, or communicating with other peripherals.

### 6. PWM0-5 (Top Side):
**PWM (Pulse Width Modulation)** interfaces are used to control things like motors, LEDs, or servos by varying the duty cycle of the signal.

---

## Bottom Side Components

### 7. VCC/GND (Bottom Side):
Power supply connections for the processor and peripherals. **VCC** provides voltage, and **GND** is the ground reference.

### 8. ADC (Bottom Right):
**ADC (Analog-to-Digital Converter)**: Converts analog signals to digital form. This particular ADC is connected to QSPI3 and multiplexed with GPIOs, indicating that the GPIO pins can switch between general-purpose digital IO and ADC input.

---

## Additional Communication Interfaces (Top Side)

### 9. I2C1, QSPI2, UART1/2 (Top Side):
These are additional communication interfaces available to the processor:
- **I2C1**: Another I2C interface for serial communication with sensors or other ICs.
- **QSPI2**: Another QSPI interface, likely for additional high-speed communication with memory or other peripherals.
- **UART1/2**: Additional UART interfaces for serial communication with external devices.

---

### 10. GPIO (Various Locations):
**GPIO (General Purpose Input/Output)** pins can be used for a variety of input or output tasks. The diagram shows different groups of GPIOs associated with specific communication protocols like I2C and QSPI.

---

# _What is package and its types_ 
![image](https://github.com/user-attachments/assets/2635e6e3-5ccd-493f-89c5-73f748129a08)


1] BGA (Ball Grid Array):

    A] BGA packages use tiny solder balls arranged in a grid on the bottom of the chip for electrical connections.
    B] They offer higher pin density and better performance for high-speed applications.
    C] Common in high-performance devices like microprocessors.

2] DIP (Dual In-line Package):

    A] DIP packages have two parallel rows of pins extending perpendicularly from the package.
    B] Suitable for through-hole mounting on PCBs (Printed Circuit Boards).
    C] Often used in older or simpler electronic circuits.

3] QFN (Quad Flat No-lead Package):

    A] QFN is a surface-mount package where leads are exposed at the edges of the package.
    B] It is compact, with excellent electrical performance due to shorter lead lengths.
    C] Common in space-constrained applications like mobile devices.

4] QFP (Quad Flat Package):

    A] QFP packages have leads extending from all four sides of the package.
    B] Used in applications that require a high number of connections, such as microcontrollers and ASICs.
    C] Suitable for surface-mount technology.

5] SOP (Small Outline Package):

    A] SOP packages have leads extending from two sides but are smaller than DIP packages.
    B] Commonly used for memory chips and other ICs in consumer electronics.
    C] Suitable for surface mounting.

6] SOT (Small Outline Transistor):

    A] SOT packages are designed for small transistors and other devices with fewer connections.
    B] Available in different forms, such as SOT23, with three leads.
    C] Frequently used in compact or low-power devices.

7] SOT223:

    A] This package type is used for transistors, diodes, and regulators in power management applications.
    B] It has larger leads than the standard SOT23 to handle higher currents.
    C] Provides better heat dissipation due to its larger footprint.

    
# _What is PADS, DIE, Core, and MACROS_

![PADS](https://github.com/user-attachments/assets/9a6ee6a6-dfa8-49a9-8423-fe687ffc99de)

---

## 1. PADS (Bonding Pads)

### A] Definition:
Pads are small metal areas located at the edges of a die that are used to establish electrical connections between the chip and the external circuitry (typically through bonding wires or bumps).

### B] Purpose:
They serve as the interface between the internal circuitry of the integrated circuit (IC) and the package pins or solder balls in a Ball Grid Array (BGA).

### C] Types:
- **Wire Bond Pads**: Used for wire bonding, where thin gold or aluminum wires are bonded between the pad and the package lead.
- **Flip-Chip Pads**: Used for flip-chip technology where bumps or solder balls connect directly to the PCB.

### D] Importance:
- Critical for signal transmission, power supply, and ground connections between the IC and the outside world.
- Proper pad design is crucial for the reliability and performance of the chip.

---

## 2. DIE (Semiconductor Die)

### A] Definition:
The die is the small piece of silicon wafer that contains the actual circuitry of the integrated circuit (IC) after the wafer has been fabricated and cut.

### B] Purpose:
The die holds the essential components such as transistors, resistors, capacitors, and other electronic components required to form the functional integrated circuit.

### C] Fabrication:
During semiconductor manufacturing, a large silicon wafer is processed to create thousands of identical ICs, each on a single die.  
Once the wafer is complete, it is diced (cut) into individual dies, which are then packaged to form the final IC product.

### D] Importance:
The die is the core functional part of the IC. Its layout and design dictate the performance of the chip.

---


## 3. Core (in IC Design)

### Definition:
The core refers to the central part of the integrated circuit (IC) that contains the functional circuitry responsible for executing the intended tasks. It is the heart of the IC where the logic gates, transistors, and other components are placed.

---

## 4. MACROS (Hard Macros & Soft Macros)

![PADS](https://github.com/user-attachments/assets/6b7b21ed-ae98-4c01-8559-12a9d8e2917f)

### A] Definition:
Macros refer to pre-designed blocks of functionality in an integrated circuit design, typically used in the design of complex systems like ASICs (Application-Specific Integrated Circuits) and SoCs (System on Chip).

### B] Types:

1. **Hard Macros**:  
   Fixed design blocks with predefined placement and routing. They are technology-dependent, optimized for performance, and cannot be changed during placement or routing.  
   - **Examples**: IP cores for memory (e.g., SRAM, ROM), standard cells like logic gates, and analog blocks like PLLs or ADCs.

2. **Soft Macros**:  
   Flexible design blocks described in RTL (Register Transfer Level), allowing modifications during the design process.  
   - **Examples**: IP cores for processors, bus interfaces, or configurable logic blocks.

### C] Purpose:
Macros help in reusing pre-designed, pre-verified blocks to reduce the design time and effort for complex ICs.

### D] Importance:
Using hard or soft macros allows designers to integrate proven, reliable functionalities into their design while saving time and improving efficiency.
    
# _Foundry, Lithography System, and Photolithography_

## 1. Foundry

### a. Definition:
A **foundry** is a manufacturing facility where silicon wafers are processed to fabricate integrated circuits (ICs). These facilities use highly specialized equipment to create semiconductor devices based on designs provided by fabless semiconductor companies.

### b. Function:
The primary role of a foundry is to produce ICs by following a set of fabrication steps that include deposition, etching, doping, and photolithography. Foundries do not design chips themselves but manufacture them based on specifications provided by their clients (fabless companies).

### c. Examples of Foundries:
- **TSMC** (Taiwan Semiconductor Manufacturing Company)
- **Samsung Foundry**
- **GlobalFoundries**

### d. Importance:
Foundries are essential to the semiconductor industry, as they allow fabless companies to focus on design, leaving manufacturing to specialized facilities. This separation of design and production enables faster innovation and cost savings.

---

## 2. Lithography System

### a. Definition:
A **lithography system** is a machine used in semiconductor manufacturing to transfer intricate circuit patterns from a mask (or reticle) onto the surface of a silicon wafer using light or another form of energy.

### b. Types of Lithography:
- **Optical Lithography**: Uses ultraviolet (UV) light to pattern wafers.
- **Extreme Ultraviolet (EUV) Lithography**: Uses extremely short wavelengths of light (13.5 nm) to achieve finer resolution in advanced nodes (7nm or below).
- **Electron Beam Lithography**: Uses a focused beam of electrons to write patterns directly on the wafer, commonly used for prototype or low-volume production.

### c. Components:
- **Light Source**: Generates light or energy beams (e.g., UV or EUV light).
- **Mask/Reticle**: Contains the pattern to be transferred to the wafer.
- **Projection Lens**: Focuses and reduces the image of the mask onto the wafer surface.

### d. Importance:
Lithography is a critical step in defining the size and shape of circuit features on a chip. As semiconductor technology advances, achieving smaller, more precise features becomes increasingly difficult, making improvements in lithography systems essential for future semiconductor technology.

---

## 3. Photolithography

### a. Definition:
**Photolithography** is a process used in semiconductor manufacturing to transfer geometric shapes from a photomask to the surface of a silicon wafer using light. It is a key part of the IC fabrication process, allowing patterns to be etched into the wafer to form transistors, interconnects, and other components.

### b. Steps in Photolithography:

1. **Coating the Wafer**: A layer of photoresist (a light-sensitive material) is applied to the wafer's surface.
2. **Exposure**: The wafer is exposed to light through a mask, which contains the circuit pattern. The light causes chemical changes in the exposed parts of the photoresist.
3. **Development**: The exposed wafer is developed, washing away either the exposed or unexposed parts of the photoresist (depending on whether a positive or negative photoresist is used).
4. **Etching**: The pattern created by the remaining photoresist is used as a stencil to etch the desired patterns into the wafer.
5. **Removal**: The remaining photoresist is removed, leaving the etched pattern on the wafer.

### c. Types of Photoresist:
- **Positive Photoresist**: The exposed areas of the photoresist become soluble and are removed during development.
- **Negative Photoresist**: The exposed areas become insoluble and remain after development, while the unexposed areas are removed.

### d. Importance:
Photolithography is critical for creating the small, intricate patterns on a silicon wafer that define a chip's functionality. It determines the feature size of transistors, interconnects, and other components, which directly affects the performance and power consumption of the final IC.

-------------------------------------------------------------------------------------------------        


# Stopwatch Application Workflow : 


![apps_to_hardware](https://github.com/user-attachments/assets/556b3dd8-3836-4ff2-8f08-7ca66807fa9b)


This project shows the flow of a Stopwatch application from the user's interaction to hardware execution. The flow is divided into three main stages: **Application Software**, **System Software**, and **Hardware**.

## 1. Application Software (Stopwatch App)

### Example:
The Stopwatch application, running on a laptop or computer, allows users to interact with the system through simple actions such as:
- **Start**
- **Pause**
- **Reset**

### Functionality:
This application serves as the interface for the user, taking input commands and performing tasks like starting, pausing, or resetting the timer.

---

## 2. System Software

The system software bridges the application software and the hardware, ensuring smooth communication and efficient resource management.

### Components:
- **Operating System (OS):**
  - The OS manages key system resources such as the CPU, memory, and input/output devices.
  - It is responsible for running the stopwatch application while handling background tasks like I/O operations and memory allocation.
  - Common operating systems include macOS, Windows, and Linux.

- **Compiler:**
  - The compiler translates the high-level code (e.g., C, C++, Java) from the application software into machine-level instructions.
  - These instructions are packaged into an executable file (e.g., `.exe` for Windows).

- **Assembler:**
  - The assembler takes the compiler-generated instructions and converts them into binary machine code (e.g., `1010100101...`).
  - This machine code consists of low-level instructions that can be directly executed by the hardware.

---

## 3. Hardware

Once the machine code is prepared, the hardware executes it.

### Components:
- **Processor:**
  - The processor executes the machine code instructions and performs the necessary operations, such as updating the stopwatch display or starting/stopping the timer.

- **Digital Circuits:**
  - Supporting components, such as clocks (`Clk`), inputs (`Din`), and outputs (`Dout`), help manage data flow and timing during execution.

---

## Summary of the Flow:

1. The **user** interacts with the Stopwatch application (Application Software).
2. The **operating system** (System Software) manages resources and communicates between the app and the hardware.
3. The **compiler** translates high-level code (C, C++, Java) into low-level instructions.
4. The **assembler** converts these instructions into binary machine code.
5. The **hardware** executes the binary instructions to perform tasks like displaying the stopwatch or updating the time.


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
# _ASIC Design Flow Overview_

![image](https://github.com/user-attachments/assets/abe34205-3877-47b0-832d-12a1ab76d5fb)

1. _Register Transfer Level (RTL)_
   
  a. Starting Point:
        The design is described using a high-level hardware description language like Verilog or VHDL.
   
  b. Function:
        The RTL describes how data flows between registers and how the logic components operate within the design.


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
2. _Synthesis (Synth)_

    ![image](https://github.com/user-attachments/assets/d99c5088-c1b4-478f-964f-d72baad3b15e)

Input: RTL description.
Output: Gate-level netlist.
Process:
The synthesis tool converts the RTL design into a gate-level netlist, consisting of logic gates and flip-flops.
The netlist is technology-mapped to the specific standard cells from the technology library (provided by the PDK, or Process Design Kit).

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

3. _Floor Planning + Power Planning (FP + PP)_

   ![image](https://github.com/user-attachments/assets/ae647052-a92e-41ae-907c-df12c1688e96)
  
Input: Gate-level netlist.
Process:
This stage defines the physical layout of the design on the chip, positioning key blocks, I/O pins, and the power distribution network.
Power planning ensures that every part of the design receives sufficient power for proper operation.

 ![image](https://github.com/user-attachments/assets/fcbcf920-80af-4975-a903-67e50599234c)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

4. _Placement (Place)_

![image](https://github.com/user-attachments/assets/1a18556f-1644-417b-8dc7-5ccf8199f9a7)

Input: Gate-level netlist and floorplan.
Process:
Placement tools arrange the logic gates and flip-flops into specific physical locations on the chip.

The goal is to minimize chip area, reduce wire lengths, and meet timing constraints.

Placement is performed in two stages: Global Placement (where cells may overlap) and Detailed Placement (where cells are optimally placed following placement rules).

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5. _Clock Tree Synthesis (CTS)_

   ![image](https://github.com/user-attachments/assets/17cce477-4879-4390-b546-4894ce7cee53)

Process:
A clock tree is synthesized to distribute the clock signal uniformly across the chip.
This ensures that all flip-flops receive the clock signal simultaneously, avoiding clock skew issues and ensuring timing synchronization.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

6. _Routing (Route)_
   
   ![image](https://github.com/user-attachments/assets/d226d089-6630-4d92-a832-dd21ea67158c)

Process:
Routing tools connect the placed gates using metal wires based on the netlist.
This step must follow design rules, optimize performance, and address signal integrity concerns like crosstalk and electromagnetic interference.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

7. _Sign-off_
   
Process:
Sign-off is the final verification stage before the design goes to manufacturing. This includes:
a. Timing closure: Ensuring the design meets timing constraints.

b. Power analysis: Verifying that the power distribution is sufficient.

c. Signal integrity checks: Checking for issues like crosstalk and electromigration.

Only once the design passes all these checks can it proceed to fabrication.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

8. _GDSII (Graphic Data System II)_
Output:
The final step produces the GDSII file, which contains the full physical layout of the chip.
This file is sent to the semiconductor foundry for fabrication.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# _OpenLaneThe Open-Source Infrastructure Platform for Silicon Development_

![image](https://github.com/user-attachments/assets/713a0a85-651c-4ae3-a4cf-2f40297be282)

OpenLane is an innovative silicon implementation platform that supports open-source tools such as Yosys, OpenROAD, Magic, KLayout, along with other open-source and proprietary utilities. Since 2020, OpenLane has been used for every Open MPW and chipIgnite shuttle. OpenLane integrates and abstracts the various steps of silicon implementation, allowing users to harden their projects using simple configuration files

---
# _OpenLANE ASIC Flow_

![openlane flow](https://github.com/user-attachments/assets/85dfc54c-8f15-4479-8a9a-c04cfd7b30a7)



## 1. Design RTL
- The flow starts with the **Register Transfer Level (RTL)** design, described using a hardware description language like Verilog. The RTL describes the behavior of the circuit, including the movement of data between registers and the logic operations.

## 2. RTL Synthesis (Yosys + abc)
- **Input**: RTL description.
- **Process**: The RTL is synthesized into a gate-level netlist using the Yosys synthesis tool and abc logic optimization tool.
- **Output**: A gate-level netlist consisting of logic gates (AND, OR, etc.) and flip-flops, mapped to a specific technology library.

## 3. Static Timing Analysis (STA) - OpenSTA
- **Process**: Static Timing Analysis (STA) is performed using **OpenSTA** to verify that the design meets the required timing constraints.

## 4. Design for Testability (DFT)
- **Process**: Design for Testability (DFT) inserts test structures into the circuit to facilitate fault detection and improve the test coverage of the chip.

## 5. Floorplanning, Placement, CTS, and Optimization (OpenROAD App)
- **Floorplanning**: Defines the physical layout of key blocks, I/O pins, and the power distribution network.
- **Placement**: Gates from the synthesized netlist are placed in specific locations on the chip to minimize area and wire length while meeting timing constraints.
- **Clock Tree Synthesis (CTS)**: A clock tree is synthesized to distribute the clock signal evenly across the design, minimizing clock skew.
- **Optimization**: Various optimization techniques are applied to improve the design in terms of power, performance, and area (PPA).
- **Special Scripts**: Fake antenna diodes are inserted and swapped to handle antenna effects in the design.

## 6. Logical Equivalence Check (LEC) - Yosys
- **Process**: LEC ensures that the post-synthesis netlist functionally matches the original RTL design, guaranteeing no unintended changes have occurred during synthesis.

## 7. Detailed Routing (TritonRoute)
- **Process**: The detailed routing step connects the standard cells in the design according to the netlist, using metal layers for signal routing. TritonRoute ensures the routed design adheres to design rules and meets signal integrity requirements.

## 8. RC Extraction and STA
- **RC Extraction**: Extracts the parasitic resistance (R) and capacitance (C) of the routing, which can impact performance.
- **STA (OpenSTA)**: Another round of STA is performed with the extracted parasitics to ensure timing closure.

## 9. Physical Verification (Magic & Netgen)
- **Process**: Physical verification is performed using **Magic** and **Netgen** tools. This ensures the design follows manufacturing design rules and that the layout matches the intended functionality.

## 10. GDSII Generation (Magic)
- **Output**: The final step produces the GDSII file, the standard format for IC layout, which is sent to the semiconductor foundry for chip fabrication.

---

# _Fault Tool in Design for Test (DFT)_

![fault](https://github.com/user-attachments/assets/d332638b-28e4-4274-b885-e69ac3fdd5ad)


The **FAULT** tool is used in the **Design for Test (DFT)** methodology to identify and simulate potential defects in digital circuits during testing. It is crucial for ensuring that integrated circuits (ICs) are thoroughly tested, reducing the likelihood of faults after production.

## Key Functions

1. **Scan Insertion**:
   - Adds **scan chains** to the circuit, which allow test data to be shifted in and out, making it easier to test the internal components of the chip.

2. **ATPG (Automatic Test Pattern Generation)**:
   - Automatically generates test patterns aimed at detecting faults, such as **stuck-at faults** (where a signal is stuck at logic 0 or 1), by simulating expected circuit behavior.

3. **Test Patterns Compaction**:
   - Reduces the number of test patterns without compromising on fault coverage, ensuring efficient testing with fewer resources.

4. **Fault Coverage**:
   - Measures how well the test patterns detect faults in the circuit. A high fault coverage percentage indicates effective testing.

5. **Fault Simulation**:
   - Simulates faults in the circuit to check whether the generated test patterns can accurately detect and diagnose the faults.

## Benefits

- **Enhanced Testability**: Makes complex circuits easier to test by inserting scan chains.
- **Comprehensive Fault Detection**: Ensures that faults like stuck-at faults and other errors are detected during testing.
- **Efficient Testing**: Optimizes the test process by reducing the number of test patterns while maintaining fault coverage.
- **Reliability**: Improves chip reliability by ensuring high fault coverage and early detection of potential defects.


---
# _OpenROAD Tool_

![image](https://github.com/user-attachments/assets/06e2339f-1d1f-4108-82cc-dcbbb0bed725)

OpenROAD (Open Runtime for Open-source Automated Design) is an open-source **physical implementation** tool used in the automated design of integrated circuits (ICs). It automates the **Place and Route (PnR)** process, which is a critical stage in physically laying out circuits on a silicon chip.

## Where is OpenROAD Used?
OpenROAD is used in the **physical design** stage of the **VLSI (Very-Large-Scale Integration)** design flow. It maps synthesized netlists (logical circuit descriptions) into physical layouts.

## Key Features of OpenROAD
OpenROAD automates several crucial steps in the physical implementation process:

1. **Floor/Power Planning**
   - Defines the physical area of the chip and ensures the power network is properly designed to supply power to all circuit components.

2. **Decoupling Capacitors and Tap Cells Insertion**
   - Decoupling capacitors stabilize the power supply, and tap cells ensure well ties and bulk connections to avoid latch-up in CMOS circuits.

3. **Placement (Global and Detailed)**
   - Cells are placed on the floorplan of the chip. The process involves:
     - **Global Placement**: Roughly positioning the cells.
     - **Detailed Placement**: Refining the placement for optimization.

4. **Post-Placement Optimization**
   - Optimizes the layout for better performance, reduced congestion, and power efficiency after placement.

5. **Clock Tree Synthesis (CTS)**
   - Synthesizes a clock distribution network to ensure the clock signal reaches all parts of the design efficiently and without timing issues.

6. **Routing (Global and Detailed)**
   - Wires the connections between the cells:
     - **Global Routing**: Rough routing of connections.
     - **Detailed Routing**: Fine-tuned routing to create precise physical connections.
---

# _RTL2GDS OpenLANE ASIC Flow Practical implementation_

---
Day 1 Labs
---

# Basic Linux Commands

1. ## ls
            Command: ls [options] [directory]
            Description: Lists the contents of a directory. If no directory is specified, it               lists the contents of the current directory.
            Options:
            
            -l: Displays detailed information (permissions, owner, size, etc.).
            -a: Includes hidden files.
            -r: Reverses the order of the listing.

---
2. ## pwd
        Command: pwd
        Description: Prints the full pathname of the current working directory.
---

3. ## mkdir
        Command: mkdir [directory_name]
        Description: Creates a new directory with the specified directory_name.
---
4. ## ls -ltr
        Command: ls -ltr
        Description: Lists the contents of the directory in long format (-l), sorted by                 modification time, in reverse order (-tr). This is useful for viewing the most                 recently modified files at the end of the list.
---
5. ## help
        Command: help [command]
        Description: Displays information about the built-in shell commands. If no command is          specified, it shows a list of all available commands.
--- 

6. ## man
        Command: man [command]
        Description: Displays the manual page for the specified command, providing detailed usage
---
7. ## cp
        Command: cp [source] [destination]
        Description: Copies files or directories from the source to the destination.
---

8. ## rm
        Command: rm [file]
        Description: Removes (deletes) the specified file or directory.
--- 
# _Steps for partical LAB 1:_ 
---

This guide provides step-by-step instructions to run OpenLane inside a virtual machine.

## Steps

1. **Go to Virtual Machine**
   - Start your virtual machine if it's not already running.

2. **Open the Command Line Terminal**
   - Press `Ctrl + Alt + T` to open the terminal window.

3. **Navigate to the OpenLane Directory**
   - Use the `cd` command to move to the OpenLane directory:
     ```bash
     cd Desktop/work/tool/openlane_directory/openlane
    ![cd](https://github.com/user-attachments/assets/96b2a08e-7796-4314-a1b9-7656e2091adf)
     ```


4. **Start Docker**
   - In the command line, type `docker` to ensure Docker is running:
     ```bash
     docker
     ```
     

5. **Run OpenLane in Interactive Mode**
   - Type the following command to start OpenLane in interactive mode:
     ```bash
     ./flow.tcl -interactive
    ![package](https://github.com/user-attachments/assets/0b46c9b7-1f20-467a-b0cc-156a35af3e51)
   ```
---

## Design Setup Stage 
    prep -design picorv32a
![prep](https://github.com/user-attachments/assets/9dd967dc-cac6-4f7c-b7d0-ae7068740ff5)
---
    run_synthesis 
![synthesis_successful](https://github.com/user-attachments/assets/92f26452-5677-4f5c-871a-84804bb05e0b)
---

 
      Flop Ratio 
 ![flop_ratio](https://github.com/user-attachments/assets/fa3216a4-9b26-41d8-b1c1-59b847f9fa0f)

 ![flop_ratio_percentage](https://github.com/user-attachments/assets/096c0133-6bc4-42f7-a984-45ce738743f1)
---

# _DAY2_Good floorplan vs bad floorplan and introduction to library cells_
---

Theory : 

1. ## Aspect Ratio (Ar): Aspect ratio refers to the ratio of a layout's height to its width.
    Aspect Ratio = Width/Height
​
    If you specify a ratio of 1, the height and width are the same and therefore the core is a square.

2. ## Utilization Factor : Utilization factor refers to the ratio of the area occupied by standard cells or logic elements to the total available area in a given design block or chip
        Formula:
        Utilization Factor =     Area occupied by standard cells
                           ------------------------------------------------------
                               Total available area in the block or chip

       A core utilization of 0.5, for example, means that 50% of the core area is used for cell placement and 20 percent is available for routing.

3. TAP Cell :

        A tap cell (or well tap cell) is a special type of cell used in the physical design of integrated circuits (ICs) to maintain proper connectivity between the substrate (bulk silicon) and the power/ground network,            ensuring that the substrate or well is properly biased.

        Prevent Latch-up: Tap cells are used to prevent a phenomenon called latch-up, where parasitic structures in CMOS technology can form a low-impedance path between the power and ground rails, leading to circuit               malfunction. By ensuring that the n-wells and p-wells are properly connected to the appropriate voltage levels (VDD or GND), tap cells help mitigate latch-up.
   
5. In OpenLane priority order for floorplan is :  1] PDK file that is used for Design.
                                                  2] Design file : config.tcl
                                                  3] System Default : floorplan.tcl
   
# _LAB2_ : 
    Screenshot of run_floorplan : 
    Step performed : 
        1. cd Desktop/work/tools/openlane_working_dir/openlane
    
        2.    docker
        3.    ./flow.tcl -interactive 
        4.    prep -design picorv32a
        5.    run_synthesis
        6.    run_floorplan
![1](https://github.com/user-attachments/assets/04bc144f-fba4-4164-8d8a-88f4866f4dd2)
![3](https://github.com/user-attachments/assets/75dd1bd1-1336-4066-9e63-9774d7cb9e94)

Floorplan def :
![4](https://github.com/user-attachments/assets/4c7618a6-ada0-46e0-a447-6463060f1529)

Now we need to enter into magic tool , so command is 

    magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &

![magic1](https://github.com/user-attachments/assets/779610c7-46e4-4ece-a23a-3fe0b8e7cbe6)

# _Steps_
 
 Align the design to the middle of the screen:

    While in the GUI, first press S on the keyboard to select the whole design.
    Then press V on the keyboard to align the design to the middle of the screen.

Zoom to a particular area:

    To zoom into a specific area, left-click the mouse to select the area you want to zoom into.
    Then, right-click and press Z on the keyboard to zoom in on the selected area.

View details of a cell:

    To check the details of any cell in the design, move the cursor over that cell and press S to select it.
    Open the tkcon window and enter the command what.
    The details of the selected cell will be displayed.

![magic2](https://github.com/user-attachments/assets/93fe039b-e811-4035-bf57-b40899a5017d)

![magic3](https://github.com/user-attachments/assets/d681c958-0ab9-4bf8-bdf9-d3f9b11f547d)
---

TAP Cell
![tapcell](https://github.com/user-attachments/assets/92b62508-8974-4e17-bbe8-0a74e4811d1b)

---

BuF Standard cell 

![buf](https://github.com/user-attachments/assets/cb54a907-f48c-47e4-a98b-3f9d467cb010)

---

nand Standard cell

![nand2](https://github.com/user-attachments/assets/c2426189-08e0-4f0f-83f2-f2a0f5592fc2)

---

Placement in 

    Physical Design (PD) is an essential step in the VLSI design flow where the synthesized netlist is converted into a physical layout. 
    In placement, one of the key stages in PD, the standard cells are positioned within the chip’s floorplan according to the timing, power, and area constraints. 
    The goal is to minimize wirelength, ensure proper signal timing, and meet design rules for manufacturability.

---


Types of Placement :

1. _Global Placement_ :

        Global placement is very first stage of the placement where cells are placed inside the core area for the first time looking at the timing and congestion.
       The goal is to generate a rough placement solution that provides a global view of the entire netlist, even if it violates some placement constraints such as cell overlap or routing constraints.
       In this phase, cell overlap is allowed, and detailed design rules (like spacing or DRCs) are not enforced yet.

---

2. _Detailed Placement_

        After the Global Placement, the next step is Detailed Placement, where the cell positions are fine-tuned, ensuring that all overlaps are removed, cells are aligned to the placement grid,
       and design rules are strictly enforced. This step is critical to ensuring that the design is ready for routing.
---

# _LAB2 Placement_

   Placement command : 
           
           run_placement

  _output_ :
      
![run_placement](https://github.com/user-attachments/assets/d1f64092-21ba-48a2-8ba2-5f72d42bb81b)

---

Generated placement def in magic
    ![placement_magic](https://github.com/user-attachments/assets/40982159-3529-4788-8517-7ef04841893b)

---

Placement of Standard Cells:
    ![placement_standardcells](https://github.com/user-attachments/assets/d8848157-fb16-419e-8c60-443d76d53fd1)


---

Placement of sky130_fd_sc_hd__mux2_1

![palcement_mux](https://github.com/user-attachments/assets/eb2be77a-827e-4e9d-ac7a-fbde518b76ab)

    
---


# _LAB3_Design library cell using Magic Layout and ngspice characterization_

---
   
       1.  Cloning custom inverter standard cell design from github repository:
![cloning](https://github.com/user-attachments/assets/886171ba-bd17-44b4-bd94-3481c0494744)

---

       2. Copying magic tech file to vsdstdcelldesign

![skytech130](https://github.com/user-attachments/assets/b5e5825c-fd40-4ac7-8d0d-7391e1180c3b)

---
       3. opening custom inverter in magic tool
          
         command :   magic -T sky130A.tech sky130_inv.mag &

![magic -T sky](https://github.com/user-attachments/assets/f02c2f0c-1dc9-4e2c-8a25-e9301c8eedeb)

---

NMOS in custom inverter in magic tool : 
![nmos](https://github.com/user-attachments/assets/d9b90fe4-7438-4f16-bc3d-4b8f11534c94)

---

PMOS in custom inverter in magic tool : 
![pmos](https://github.com/user-attachments/assets/5c6649a1-f523-42dd-8589-fa59fd1a1054)

---

nwell 
![nwell](https://github.com/user-attachments/assets/088f99f4-c19e-47d8-b02d-d94d8d37dfa5)

---

poly :
![poly](https://github.com/user-attachments/assets/b5f52529-cde8-46e3-bf7b-4a64eab2eedd)

---

Spice extraction of inverter in magic.

    commands follow :
    1. pwd
    2. extract all
    3. ext2spice cthresh 0 rthresh 0
    4. ext2spice

![commands_run](https://github.com/user-attachments/assets/0e961af0-a4a8-4ad1-9e23-9f2fb2e53674)

---

Measuring layout Grid : 
![box](https://github.com/user-attachments/assets/9d088bc6-0a8f-44bf-9ffe-5fda6cb64f49)

---
spice file
![vim sky](https://github.com/user-attachments/assets/a8f63c6d-0b84-4bc4-8305-b034d1d9beed)


---

Download or install  ngspice 

    sudo apt-get install ngspice

command to run spice file

    1. # Command to directly load spice file for simulation to ngspice
          1.  ngspice sky130_inv.spice

          2.  plot y vs time a 

output : 
![output ngspice](https://github.com/user-attachments/assets/0e22fac0-2ee1-4145-8453-7041ece28c78)

![waveform spice](https://github.com/user-attachments/assets/51076c93-717f-49cc-859a-bae110703c0a)


---

Rise Time 

        
        The rise transition time, or rise time, is the time it takes for a signal to transition from a low state (usually 22% of its maximum value) to a high state (usually 80% of its maximum value).
        Calculate Rise Time:

    Subtract the time at 10% from the time at 90% to get the rise time.

            Rise Time = T80%−T20%

            80 % of 3.3V is 2.64 
            20 % of 3.3V is 0.66
            
![risetime](https://github.com/user-attachments/assets/584a19f1-a17f-4e01-9b64-67e9f0912361)

_80 Percent of 3.3V is 2.64_

![80%2 64](https://github.com/user-attachments/assets/229045cd-8a80-4e79-94e7-5151a9119c89)

_20 Percent of 3.3V is 0.660_

![80% 660](https://github.com/user-attachments/assets/f81af92a-6572-4805-b553-4d1ba589d6d9)

_Rise Transition time = 6.16096 - 4.03964  = 2.12132ps_
![risetime calculation](https://github.com/user-attachments/assets/8f61236c-f1be-4c32-8e61-ad07e843092d)


---

Fall Time : 
        
        The fall time of a signal is the time it takes for the signal to change from a high voltage level (often 80% of the initial value) to a low voltage level (often 20% of the initial value).
            
        Calculate the fall time: Subtract the time at the 80% point from the time at the 20% point.

            Fall Time=T80%−T20%

_80 Percent of 3.3V is 2.64_

![falltransition2 64 80%](https://github.com/user-attachments/assets/9e0372ec-acde-4ace-9cab-463a17197d23)

_20 Percent of 3.3V is 0.660_
![fall transition 20 % 0 66](https://github.com/user-attachments/assets/53eab6db-a824-44c9-bc52-cffb5a5b5b3d)

 _FAll Transition time = 2.09-2.03  = 0.03 = 30ps_
![fall 80-20](https://github.com/user-attachments/assets/39e194b1-30b1-4877-9662-d3a0690b355c)

    
---


_Rise Cell Delay :_
      
       Rice Cell Delay= Tout50%​ − Tin50%​
       Rice Cell delay =  2.12414 - 2.06000 =  0.06414 = 64.14ps
![cell delay 50rise , fall](https://github.com/user-attachments/assets/98b93fbb-69c6-4952-b077-0d7b3d114009)

![cell delay 50%](https://github.com/user-attachments/assets/d5facef0-18ef-47d8-b46b-a9a3acdfad84)

---

_Fall Cell Delay_

         Fall Cell Delay = Tout 50% - Tin 50%
                         = 4.02667 - 4.00483 
                         = 0.02184
                         = 21.84 ps
![cellfalldelay terminal](https://github.com/user-attachments/assets/2cf260a3-106b-4c27-99d6-15bceb4740b5)

![cellfalldelay](https://github.com/user-attachments/assets/6557fbf2-2aa4-45a3-b4f9-8706400e7446)


---

# _Lab introduction to magic and steps to load sky130 tech-rules_

      1.  Go to home directory
      2.  download the lab files
              wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
      3. extract it
              tar xfz drc_tests.tgz
      4. Go to - cd drc_tests
      5. to view .magicrc file
         command : gvim .magicrc
      6. Command to open magic tool in better graphics ->  magic -d XR &
![sky130techrules](https://github.com/user-attachments/assets/f3782388-ceed-471b-8d03-e6b7223e6daf)


![magicrcfile](https://github.com/user-attachments/assets/9f82d770-ff02-47ca-8ae0-4a00926da5cf)

---
_load_poly_

![loading poly](https://github.com/user-attachments/assets/f9c7deb0-a386-46d3-b6b0-944848bf7836)


---

# _DAY#_LAB6_to fix poly.9_

    Poly resistor spacing to poly or spacing (no overlap) to diff/tap   0.480µm
    
    poly.9 rule no drc violation even though spacing < 0.48u

![poly9error_before](https://github.com/user-attachments/assets/93decf87-6514-40e8-834c-5629a2f332a7)

![drc why](https://github.com/user-attachments/assets/633e3734-dfde-4c0b-b84c-71a7448bf79f)


---

commands to enter :

    Commands to run in tkcon window

    1. To Load updated tech file
        -> tech load sky130A.tech

    2. re-run drc check to see updated drc errors
        -> drc check

    3. Selecting region displaying the new errors and getting the error messages 
        -> drc why

solving poly.2 error - Spacing of poly to poly

    Before correcting
    
![polyspacing 2](https://github.com/user-attachments/assets/8323eef5-b509-4e7d-a014-0a62832dba68)

    after correcting
![poly 2corrected](https://github.com/user-attachments/assets/1dd7445e-addd-4119-872f-748472af204b)

---


# (nwell.4)
	

    All n-wells will contain metal-contacted tap (rule checks only for licon on tap) .

    Incorrectly implemented nwell.4 rule no drc violation
    
    commands inserted in sky130A.tech file to update drc
![nwelltapped](https://github.com/user-attachments/assets/1b0444c0-6211-4d8b-ae11-36bb3503bc68)

![variants](https://github.com/user-attachments/assets/d0677ad3-143e-418e-b29b-f4f13b913322)



    After correction showing drc error
![nwell rmissing](https://github.com/user-attachments/assets/6b649f47-556a-4125-aea1-9530bb0c2e4f)

---

# _DAY4- Pre-Layout Timing Analysis_

	1. Generate lef from the layout.
 
 1st Requuirement : The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
 tracks.info of sky130_fd_sc_hd

![sky_130A_track_info](https://github.com/user-attachments/assets/5115610c-e9c7-495f-b3b2-077c6baeedd4)

 tkcon window to set grid as tracks of locali layer
![grid_command_terminal](https://github.com/user-attachments/assets/fe126ea2-2f7c-4abf-a80f-6857a3687a9a)

input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks.
![after_grid](https://github.com/user-attachments/assets/32f79c44-dab1-4e4c-819b-b8f4be85cb2f)


---

2nd Requirement
	width of the standard cell must be odd multiple of the xpitch or xdirection
![horizontal_width](https://github.com/user-attachments/assets/215b233b-c51b-4839-8bcd-a74ac8072ea2)

 W i d t h   o f   s t a n d a r d   c e l l = 1.38   u m = 0.46 ∗ 3 

---
3rd Requriement 
	Hight of the standard cell must be even multiple of the ydirection or ypitch

![vertical_height](https://github.com/user-attachments/assets/f70e95a7-7c17-48a8-a4f0-55a26be88107)

H I G H T   o f   s t a n d a r d   c e l l = 1.38   u m = 0.46 ∗ 3 

---
Defining the Port 
![A_locali](https://github.com/user-attachments/assets/2a38a90c-b100-4b09-8b61-f951e7e7ac34)
![y_locali](https://github.com/user-attachments/assets/c9b6dd3d-4105-4a11-935e-fd51c28e53ac)
![vPWR](https://github.com/user-attachments/assets/7f1f2a34-2a7c-4531-920b-ec20da9b309d)
![VGND](https://github.com/user-attachments/assets/44181246-dc51-4f5a-a4f0-118068f6b8ee)


NEW Layout
![new_mag](https://github.com/user-attachments/assets/215484a3-ae96-455e-8bc7-2a390840e140)


 tkcon window to save the layout with custom name and new lef file
 ![lef_write_with all](https://github.com/user-attachments/assets/0147b96b-a224-4b31-9e40-54cf6bdfa200)
---

SKY_L3 - Introduction to timing libs and steps to include new cell in synthesis

	1. Copy the new lef file to  /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
	2. Copy lib files "sky130_fd_sc_hd.lib" from vsdstdcelldesign/lib to /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

Edit 'config.tcl' 

  	set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
	set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
	set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
	set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

	set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
 
 ![configedit](https://github.com/user-attachments/assets/79774496-72b2-45c5-a62d-adc537ff2ab5)

openlane flow synthesis with newly inserted custom inverter cell.

	steps
 	1. go to openlane directory : cd Desktop/work/tools/openlane_working_dir/openlane
  	2. docker
   	3. ./flow.tcl -interactive
    	4. package require openlane 0.9
        5. prep -design picorv32a -tag 11-09_16-08 -overwrite
	6. set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
 	7. add_lefs -src $lefs
  	8. echo $::env(SYNTH_STRATEGY)
   	9. set ::env(SYNTH_STRATEGY) "DELAY 3"
    	10. echo $::env(SYNTH_BUFFERING)
     	11. echo $::env(SYNTH_SIZING)
      	12. set ::env(SYNTH_SIZING) 1
        13. echo $::env(SYNTH_DRIVING_CELL)
	14. run_synthesis
	15. run_floorplan 
 		we will get error after error 
   		1. init_floorplan
     		2. place_io
       		3. tap_decap_or
	 16 run_placement
  	17 magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![synth_overwrite](https://github.com/user-attachments/assets/f4f8f5be-b54d-4143-ab1f-0f3e036b5e02)

	total negative slack =-711.59   and wrost negative slack = -23.89.
![synthesis completed](https://github.com/user-attachments/assets/d8945cb4-4dc1-4024-848e-440913c13368)

 after this performed steps are from 5 to 14 
 ![zero _negative slack](https://github.com/user-attachments/assets/45ff0442-cc79-43da-ac51-0054f022661c)

Now we got TNS and WNS = 0

Now we perform floorplan 
	run_floorplan
 ![run_floorplan](https://github.com/user-attachments/assets/211c24f8-2bf4-432d-8621-53b3a68b92df)
![error](https://github.com/user-attachments/assets/d0a4d661-c330-4897-9581-4db4c9b6dc65)

after getting error run following commands

	1. init_floorplan
	2. place_io
	3. tap_decap_or

![init_floorplan](https://github.com/user-attachments/assets/7dd207eb-cdc5-46f3-a72c-9aacd4550f01)
![tap_decap](https://github.com/user-attachments/assets/4197501d-032c-4f80-9959-ca21ae778ec5)

Run_placement
![run_placement](https://github.com/user-attachments/assets/d489e725-24d0-4a20-9004-3df4b07d8e27)
![run_placement_complete](https://github.com/user-attachments/assets/6a99138e-6762-4292-ba33-9fd9ec003943)


 load placement def in magic in other terminal
 
![magic](https://github.com/user-attachments/assets/3178192e-fe35-4ebb-8f9d-0b8fccb98432)

![vsdinv](https://github.com/user-attachments/assets/fcc38ff7-9a09-422c-82f2-38e9eb81becf)

---
	 tkcon window to view internal layers of cells

![expand](https://github.com/user-attachments/assets/2b868a31-917a-4845-8b1b-0bf315050a50)

---

New created pre_sta.conf for STA analysis in openlane directory

![pre_sta,conf](https://github.com/user-attachments/assets/65b23ef4-2caf-4d34-94ae-db122328daea)

my_base.sdc for STA analysis in openlane/designs/picorv32a/src

![my_sdc](https://github.com/user-attachments/assets/836ce71a-0d5d-4b46-9c7f-1ad763a83963)

output of pre_sta.conf is equal to synthesis stage

![openlaneoutput_negativeslace](https://github.com/user-attachments/assets/a0542931-4f42-44de-ac2a-9be371af96f0)

Here vsdinverter gate  is driving 4 fanouts

![or_gate_drive_strength_2_fanout_4](https://github.com/user-attachments/assets/ece2b905-229f-401a-9aa8-3002a3c075b8)

command to optimize 

	1. report_net -connections _10566_
	2. replace_cell _10566_ sky130_fd_sc_hd__or3_4
 	3. report_checks -fields {net cap slew input_pins} -digits 4

Befor optimizing

![newslackviolated_23 90](https://github.com/user-attachments/assets/e101f3ee-5860-458d-ad39-a5e65dc7828a)


After optimizing slack reduced
![newslack_afteroptimizing](https://github.com/user-attachments/assets/fecfb920-a039-418e-a4dc-6028c88dbee3)

or gate
![new_orgate_4fanout_before_optimize](https://github.com/user-attachments/assets/90ea3c92-022f-4ee1-89ce-ea5d98b00015)



Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
	
 	1. report_net -connections _11675_
	2.replace_cell _14514_ sky130_fd_sc_hd__or3_4
	3.report_checks -fields {net cap slew input_pins} -digits 4
before total slack
![befor_11675_total slack](https://github.com/user-attachments/assets/5d2ad9c8-a017-4c5c-a515-dd4bbe8049ef)

after optimizaiton 
![new_11675_delayreduced](https://github.com/user-attachments/assets/ec5f7127-ca64-4b40-aecb-6e10cbf5053f)

or gate _11675_
before
![new_11675_before](https://github.com/user-attachments/assets/7ab9f400-3e64-4f64-abaa-0b39680c35ca)
after
![new_11675_delayreduced](https://github.com/user-attachments/assets/84ecb9d5-3632-4271-9764-3bfe95ba152b)


We started ECO fixes at wns -23.90 and now we stand at wns 23.1405we reduced around 0.7595ns of violation
---


Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

![oldnetlist](https://github.com/user-attachments/assets/c9e9ede3-28fe-44e1-86e3-98a59c45bf0f)

Commands to write verilog
	
 	1.help write_verilog
  	2.write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/09-09_05-51/results/synthesis/picorv32a.synthesis.v
	3. exit
 Screenshot of commands run
 
 ![write_Verilog](https://github.com/user-attachments/assets/9f9c2873-c84e-48b5-a46b-0249bb7f248c)

 Verified that the netlist is overwritten by checking that instance _14675_
![11675](https://github.com/user-attachments/assets/5a21f734-4cbe-4e59-9ba4-9558e56cb041)

---

we confirmed that netlist is replaced and will be loaded in PnR  , since we want to go with  0 violation design we will continuing with the clean design .
![slackzero](https://github.com/user-attachments/assets/2175ef0a-6405-4fbf-809d-fc2205f46840)

placement done 
![placementdone](https://github.com/user-attachments/assets/7690a971-24fd-4e06-86c9-ef97e8d4e4e3)

running _ cts
![run_Cts](https://github.com/user-attachments/assets/2f7731cf-a91c-43a0-8166-80d1e61327e9)

generated cts file in "/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/09-09_05-51/results/synthesis" 
![cts_generated](https://github.com/user-attachments/assets/23e30600-812b-40b2-b452-30db6ca739da)

---
#_POST_CTS_

commands performed 
	
 	1. openroad
![1_openroad](https://github.com/user-attachments/assets/f76680b5-dfda-406f-914f-d47d732d1066)

  	2. read_lef /openLANE_flow/designs/picorv32a/runs/09-09_05-51/tmp/merged.lef
![2_read_lef ](https://github.com/user-attachments/assets/5ce81d93-ae1d-4a2b-87ba-9a2848bf4906)

    	3. read_def /openLANE_flow/designs/picorv32a/runs/09-09_05-51/results/cts/picorv32a.cts.def
![4_read_def](https://github.com/user-attachments/assets/22f78503-0bfd-4425-ad03-75017b1089e3)

 	4. write_db pico_cts.db
![6_write_db pico_cts db](https://github.com/user-attachments/assets/7053030f-7d16-4d43-a570-a8d67799b441)
  
	5. read_db pico_cts.db
![8_read_db pico_cts db](https://github.com/user-attachments/assets/98607303-3960-4ece-9089-6382a638d93e)
	
 	6. read_verilog /openLANE_flow/designs/picorv32a/runs/09-09_05-51/results/synthesis/picorv32a.synthesis_cts.v
![9_read_verilog](https://github.com/user-attachments/assets/90553625-3604-452e-afcc-1c620de7c0e2)
  
  	7. read_liberty $::env(LIB_SYNTH_COMPLETE) 
![read_liberty $::env(LIB_SYNTH_COMPLETE)](https://github.com/user-attachments/assets/226a94b1-b0c2-4af1-8487-54c8f0ed992b)

    	8. link_design picorv32a
![10_link_design picorv32a](https://github.com/user-attachments/assets/d9c63f0b-1b72-42d8-9ef5-9f62615a045f)

    	9. read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
![11_read_sdc ](https://github.com/user-attachments/assets/f00bb0c1-5d86-492e-8525-3ac3d179328b)

	10. set_propagated_clock [all_clocks]
![12_set_propagated_clock](https://github.com/user-attachments/assets/c3474d38-40da-4614-a861-74e1dfe963f5)

	11. report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
![13_report_checks_output](https://github.com/user-attachments/assets/fa5e5e2c-f55c-4b97-bff0-31b56757779c)

 	exit

#_removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'_

command for removing 
	    
     	1. echo $::env(CTS_CLK_BUFFER_LIST)
      	2. set ::env(CTS_CLK_BUFFER_LIST)  lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0
	3. echo $::env(CTS_CLK_BUFFER_LIST)
 ![14_removed_clk_buf1](https://github.com/user-attachments/assets/6feed76b-c69e-40c2-9ee9-bb3f8b7b6eba)

 Before running cts :
 
 	1. echo $::env(CURRENT_DEF)
	2. set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/09-09_05-51/results/placement/picorv32a.placement.def
![run_cts_before_placement_Cts](https://github.com/user-attachments/assets/00ed93b6-35d3-47d7-ba49-8668a24b4f98)
![running_cts_afterplacement_def](https://github.com/user-attachments/assets/971ffd45-6d7d-484f-8136-c7df6581f039)

completed running cts 
![completed run_cts_2ndtime](https://github.com/user-attachments/assets/cc108d71-e2b5-4be1-bef4-b4c2fe145fe8)
![read_def_2ndtime](https://github.com/user-attachments/assets/338fbfdf-2755-436d-8312-bbb96ef3acd5)

![Screenshot from 2024-09-13 16-15-31](https://github.com/user-attachments/assets/70a58477-4c32-421a-ade2-040ad9e93e40)
![hold](https://github.com/user-attachments/assets/72ce163f-952e-445d-abae-c174c37cd7d7)

![slack timing](https://github.com/user-attachments/assets/58f6f87a-91ce-4fc9-8a31-fed9a0261f40)

![alldone](https://github.com/user-attachments/assets/df046b6e-4aea-444c-87b5-b8fd27e5c9a7)


---

# _Sky130 Day 5 - Final steps for RTL2GDS using tritonRoute and openSTA_

---

SKY_L1 - Lab steps to build power distribution network

command used : 

 	1. Go to openlane directory : cd Desktop/work/tools/openlane_working_dir/openlane
	2. Type : Docker
 	3. Invode openlane : ./flow.tcl -interactive
  	4. package require openlane 0.9
	5. prep -design picorv32a -tag 09-09_05-51 
 	6. echo $::env(CURRENT_DEF)
  
![1](https://github.com/user-attachments/assets/f51883d8-c04e-4e94-976d-6583d9012301)

	7. gen_pdn
 	
![gen_pdn](https://github.com/user-attachments/assets/b0901c20-a811-4993-9eae-24180c6a1399)

![gen_success](https://github.com/user-attachments/assets/2ec5693f-49cd-4701-9129-f0c544c8fbcb)


![pdf def](https://github.com/user-attachments/assets/8916cee8-11e2-446d-b5da-ab998b22985d)

	Def file generated :
![deffilegeneratded](https://github.com/user-attachments/assets/51004449-0291-4d52-a8ce-8b658c293ce6)

	pdn def in magic 

![magic](https://github.com/user-attachments/assets/6031f0c0-78ee-4838-91ee-a629fdcb1b69)

	running routing using - command - "run_routing"	
 
![runrouting](https://github.com/user-attachments/assets/14b53fed-a947-4a22-9a9f-712f338ec7e1)

![rouutinggg1](https://github.com/user-attachments/assets/30f07431-1808-4bd6-8d36-4cbf6bec4f4d)

![rouutinggg1](https://github.com/user-attachments/assets/bf173ce5-b4a2-470b-a8d1-170b323e82bf)


Fast route guide file 

![guide](https://github.com/user-attachments/assets/6fac3c73-7aa9-4657-97bf-853214264d34)

completion of routing

![fjinish](https://github.com/user-attachments/assets/6e02497f-a5eb-4279-8af4-0a856a3cf617)

zero violations

![Screenshot from 2024-09-14 21-58-19](https://github.com/user-attachments/assets/1dfa25cf-8187-4b88-a5f6-e2434498fc44)


