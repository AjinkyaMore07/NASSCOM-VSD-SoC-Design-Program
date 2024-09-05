Digital Soc Design 


![image](https://github.com/user-attachments/assets/fb7c3327-b07b-4e52-8ce2-7e123eada0a2)

DAY1
    Processor/SoC:
    
![processor peripherals](https://github.com/user-attachments/assets/538bb221-9f02-474e-9896-c19dc622d94a)


    

    The central part of the system, which handles computation, control, and data processing. In a System on Chip (SoC), the processor integrates with various components like memory, interfaces, and other peripherals to create a complete system

    JTAG, UART0, QSPI1, I2C0, clk, reset (Left Side):

    A] JTAG (Joint Test Action Group): Used for debugging and testing the chip during development.

    B] UART0 (Universal Asynchronous Receiver-Transmitter): A serial communication protocol for transmitting and receiving data between devices.

    C] QSPI1 (Quad Serial Peripheral Interface): A flash memory interface that communicates at high speeds.

    D] I2C0 (Inter-Integrated Circuit): A multi-master, multi-slave protocol used for communication between integrated circuits.

    E] clk: The clock signal that synchronizes operations across the chip.

    F] reset: Resets the system to a predefined state.
    
3. JTAG-UART FTDI (Left Side):

    This block connects the processor to a USB interface for debugging purposes, likely using an FTDI (Future Technology Devices International) chip for communication.

4. QSPI1-Flash (Left Side):

    This interface is connected to flash memory, which stores non-volatile data (like firmware or configuration settings) for the processor.
   
6. I2C0-EEPROM (Left Side):

    A serial communication interface connected to an EEPROM (Electrically Erasable Programmable Read-Only Memory), used to store small amounts of data like configuration parameters that need to be preserved across reboots.

7. SDRAM (Top, Bottom, and Right Side):

    SDRAM (Synchronous Dynamic Random-Access Memory): Provides volatile memory for the processor to store data temporarily during execution. The processor can have multiple interfaces connected to SDRAM chips, as shown on the top, bottom, and right sides.

7. Direct I2C, QSPI, GPIO (Top Side):

    This set of interfaces provides direct communication using I2C and QSPI protocols. The GPIO (General Purpose Input/Output) pins can be used for various control or communication tasks, like driving LEDs, receiving button inputs, or communicating with other peripherals.

8. PWM0-5 (Top Side):

    PWM (Pulse Width Modulation) interfaces are used to control things like motors, LEDs, or servos by varying the duty cycle of the signal.

9. VCC/GND (Bottom Side):

    Power supply connections for the processor and peripherals. VCC provides voltage, and GND is the ground reference.

10. ADC (Bottom Right):

    ADC (Analog-to-Digital Converter): Converts analog signals to digital form. This particular ADC is connected to QSPI3 and multiplexed with GPIOs, indicating that the GPIO pins can switch between general-purpose digital IO and ADC input.
    
12. I2C1, QSPI2, UART1/2 (Top Side):

    These are additional communication interfaces available to the processor:
        I2C1: Another I2C interface for serial communication with sensors or other ICs.
        QSPI2: Another QSPI interface, likely for additional high-speed communication with memory or other peripherals.
        UART1/2: Additional UART interfaces for serial communication with external devices.

13. GPIO (Various Locations):

    GPIO (General Purpose Input/Output) pins can be used for a variety of input or output tasks. The diagram shows different groups of GPIOs associated with specific communication protocols like I2C and QSPI.
    
