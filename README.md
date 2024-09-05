# Digital VLSI SoC Design and Planning
---
Sky130 Day 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
SKY130_D1_SK1 - How to talk to computers
SKY_L3 - From Software Applications to Hardware

---


![image](https://github.com/user-attachments/assets/fb7c3327-b07b-4e52-8ce2-7e123eada0a2)

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
