---
date: 2025-12-9
tags:
  - microcontroller 
---
1. Explain the distinction between a micro-processor, micro-controller and signal-processor.
- A micro-controller is a single-chip computer (CPU plus peripherals) optimized for embedded use, 
with built-in interrupt handling, power saving, and interfaces for sensors and actuators.

- A microprocessor is mainly a high-throughput CPU with large registers and caches, 
typically requiring external peripherals and memory.

- A digital signal processor (DSP) is a processor specialized for signal processing 
and numerical computations, featuring hardware support like fast multiply-and-accumulate units for algorithms such as FFTs.

2. Typical classification criteria for microcontrollers and their meaning
- Type: Micro-controller, micro-processor, DSP, indicates integration level and typical use case.
- Data bus width (4/8/16/32 bit, etc.) tells you about numeric range, performance and memory model.
- Architecture (von Neumann vs. Harvard) shared vs. separate code/data memories and buses.
- Instruction set class (RISC vs. CISC) simple/few fixed-size instructions vs. many complex instructions and addressing modes.
- Performance metrics quantify computational power.
- Power class (ultra-low power, mainstream, high-performance) suitability for battery vs. mains-powered systems.
- Peripheral set (ADC, DAC, timers, comms, etc.) indicates what kind of I/O and functions are integrated.

3. Typical selection criteria for microcontrollers
- Required performance (CPU speed, MIPS/FLOPS, cache, hardware multiplier/FPU).
- Power consumption (sleep/deep-sleep modes, supply voltage, energy profile).
- Memory sizes and types (Flash/ROM for code, RAM for data, external memory interfaces).
- Peripheral set and connectivity ADC/DAC, timers, UART, SPI, IC, CAN, USB, Ethernet, etc.).
- Package and pin-out (pin count, package size, pin compatibility within a family).
- Development ecosystem (compilers, debuggers, IDEs, example projects, libraries, RTOS support).
- Availability & longevity (long-term supply, second source possibilities, upgrade paths).
- Cost (unit price and overall BOM impact).

4. What means RISC and what means CISC architecture? What is their distinction? Which architecture is used by the Cortex-M controllers?
- RISC (Reduced Instruction Set Computing): Few, relatively simple and usually
fixed-length instructions. more efficient implementations.
- CISC (Complex Instruction Set Computing): Many, complex instructions with rich addressing modes; 
single instructions can perform complex operations but are harder to implement efficiently.
- Cortex-M controllers use a RISC-style architecture even though the strict RISC/CISC border is nowadays somewhat blurred.

5. Which microcontroller is used in the class? 
- The class uses an STM32L432KC micro-controller, based on an ARM Cortex-M4 core from STMicroelectronics.

6. How many bus subsystems are built into the micro-controller used in the class?
- The Cortex-M4 core uses three main internal buses: an ICode bus (instruction/code), a data bus 
and a System bus.

7. How much memory and which types of memory are built into the microcontroller 
used in class? What are these memories used for?
- Flash memory: up to 256 kB, used to store program code and constant/read-only data.
- SRAM: 64 kB total, split into 48 kB used for stack, heap and variable (read/write) data at run-time.
- Additionally, there are memory-mapped peripheral registers and optional external memory via QUADSPI, 
used for configuration and extended code/data storage.

8. What are tasks of a CPU execution unit? Sketch the basic building blocks and 
explain it's functional interfaces to the surrounding periphery.
- The execution unit contains the general-purpose registers, the Arithmetic Logic Unit (ALU), 
and the status/program status register(s).

9. What are tasks of a CPU control unit? Sketch the basic building blocks and explain it's functional interfaces to the surrounding periphery.
- The control unit holds the program counter, fetches instructions from program memory. 

10. Explain typical tasks of an Arithmetic Logic Unit. Explain it's relation to the status register. 
What information is maintained within the status-register? Give some examples.
- The ALU performs arithmetic (add, sub, mul, div, shifts, etc.) and logic operations (AND, OR, XOR, NOT, compare).
After each relevant operation, it updates flags in the status register which capture properties of the result 
(e.g. zero, negative, carry, overflow, saturation).
The status register typically holds bits like Z (Zero), N (Negative), C (Carry/Borrow), V (Overflow) and sometimes extra bits (e.g. DSP overflow/saturation or "greater-than-or-equal" indicators), which later instructions and branches can test.

11. Which flags are used by the Cortex-M processors? Explain them.
- N (Negative): result's sign bit is 1 (negative in two's complement).
Z (Zero): result is equal to zero.
C (Carry/Borrow): carry out from addition or borrow from subtraction, also used for shifts.
V (Overflow): signed arithmetic overflow occurred.
Q (Saturation/DSP overflow): saturation occurred in certain DSP operations.
GE[3:0] (Greater-or-Equal flags): used for some SIMD/DSP-style operations to indicate per-byte/half-word comparison results.

12. Illustrate and explain a typical instruction pipeline. What are the benefits and/or drawbacks that are sometimes encountered?
- A simple pipeline splits instruction execution into stages like Fetch Decode Execute (Memory) Write-back, 
with different instructions in different stages at the same time.
Benefit: higher throughput (one instruction completed per cycle once the pipeline is full) 
without increasing clock frequency.
Drawbacks: pipeline hazards (control hazards on branches, data hazards on 
dependencies, resource hazards on shared units) causing stalls/flushes, and overhead to fill/empty the pipeline.

13. Explain typical command types of a CPU.
- Data processing: arithmetic and logic (ADD, SUB, MUL, AND, OR, XOR, shifts, compares).
Data transfer: load/store and move (LDR/STR, MOV, stack operations).
Control flow: branches, jumps, calls, returns, conditional branches (B, BL, BX, etc.).
System/privileged: interrupt control, mode changes, special register access, no-ops, etc.

14. What is a HAL library?
- A HAL (Hardware Abstraction Layer) library is a vendor-provided C library that wraps low-level register accesses of peripherals into portable, 
higher-level functions, simplifying and unifying embedded application development across devices 

15. Illustrate typical bare-bone software architectures and discuss them.
- Super-loop architecture: system initializes once and then runs a single endless loop 
that polls all peripherals and tasks in sequence; simple and fine for non-critical timing, but difficult to guarantee timing when workload varies.
Fore-/background architecture: the endless loop mainly does background work or 
puts the CPU into sleep, while interrupt service routines (ISRs) handle time-critical events in the foreground; this improves responsiveness and power usage but requires careful ISR design and concurrency handling.

IO Questions: 


1. Explain typical operating conditions for a micro-controller 
(operating voltages, frequency, power-consumption, current source capabilities per I/O, temperature ranges).
- Supply voltage e.g. 1.71-3.6 V, max I/O current e.g. 20 mA per pin, 100 mA total, 
clock up to tens of MHz, and power consumption from tens of MHz down to nA in stop/standby; temperature ranges can go from -40 o +125 automotive).

2. What are typical parameters for buttons/switches?
- Temperature range, sealing/harness (water/dust proof), mechanical lifetime (actuation cycles), 
bouncing time, contact and insulation resistance, max operating voltage/current, and required actuation force.

3. What means bouncing in conjunction with buttons?
- When a button is pressed or released, the contacts mechanically bounce, causing rapid 0/1 
transitions instead of a clean edge, so without debouncing the system may see multiple presses.

4. What is a circular- (or ring-) buffer? What is it used for? Which functions are required to operate such a buffer?
- A fixed-size array with head/tail indices that wrap around, used to buffer streams of events (e.g. key presses) between producer and consumer; 
you need functions to initialize, put (cb_put), and get (cb_get) elements (and often to test full/empty).

5. What kinds of LCD displays are frequently encountered in embedded systems products?
- Character LCDs  and graphic LCDs plus similar modules like small OLED or ePaper displays with serial or parallel interfaces.

6. How can you control the brightness of a LED?
- Either change the forward current (via resistor or driver) or, more commonly, 
use PWM and vary the duty cycle to adjust perceived brightness.

7. How can you output a logic level on a pin of a micro-controller using the C language?
- Configure the pin as output in the mode register and then write to the output data register, e.g.:
GPIOA->MODER |= (1U << 14);   // PA7 as output
GPIOA->ODR   |= (1U << 7);    // set PA7 = 1
GPIOA->ODR   &= ~(1U << 7);   // set PA7 = 0

8. Where to find symbolic definitions and addresses of an I/O port? How can these be used?
- Where to find symbolic definitions and how to use them Symbolic register addresses and 
bitfields are in the device header file (e.g. stm32l432xx.h) and the reference manual; 
in C you include the header and then access registers via the provided structs/macros (e.g. GPIOA->MODER, GPIOA->ODR, bit masks).

UART questions:
1. Describe the functionality of an asynchronous serial interface. Illustrate the data transmission. 
What options can be configured? Explain their respective purpose/function.
- Sends data one bit at a time on a data line with frames: idle (1), start bit (0), data bits (LSB first), optional parity bit, 
stop bit(s) (1); configurable options are:
Baud rate (bit time / speed),
Data bits (5-9) (payload size),
Parity (none/even/odd) (simple error check),
Stop bits (1/1.5/2) (minimum idle time for resync),
Bit order (LSB/MSB first) and sometimes inversion / voltage level.

2. Describe the functionality of a synchronous serial interface. 
Illustrate the data transmission and highlight the differences to an asynchronous serial interface.
- Uses separate clock line plus data line(s); data is sampled on clock edges so no start/stop bits are needed, 
usually allowing higher speeds but requiring more wires (examples: SPI, I) compared to asynchronous serial which must self-synchronize via start/stop bits.

3. How is a communication between multiple nodes accomplished using a serial interface?
- Achieved with a shared bus where one node (master) transmits and multiple nodes listen on RX, often using a higher-level protocol or 9-bit "MP mode" 
to mark address bytes so only the addressed node processes the following data.

4. What means 8N1 9600?
- 9600 baud, 8 data bits, N = no parity, 1 stop bit.

5. What is the purpose of a start and stop bit respectively?
- Start bit (0): marks the beginning of a frame and lets the receiver re-sync its timing.
Stop bit(s) (1): mark the end of a frame and guarantee a minimum idle time so the next start bit can be detected reliably.

6. What is the use of a parity bit? How does this work?
- It provides simple error detection by choosing the parity bit so the total number 
of 1-bits in data+parity is even (even parity) or odd (odd parity); a mismatch on the receiver indicates a parity error.

7. How does the interconnect of a serial interface look-like?
- Typically TX X crossed between two nodes plus a common GND; optional extra lines 
(e.g. RTS/CTS) are for flow control, and the electrical levels may be TTL (0-3.3/5 V) or RS-232 (voltages).

8. How is asynchronous data received (synchronized) on a receiver?

9. What happens when a sender transmits another frame before the receiver was able to read the previous one? How can such a situation be managed?
