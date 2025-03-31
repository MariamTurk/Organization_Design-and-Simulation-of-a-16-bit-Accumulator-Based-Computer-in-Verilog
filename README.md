# Design and Simulation of a 16-bit Accumulator-Based Computer in Verilog

This project involves designing and implementing a simple 16-bit accumulator computer using Verilog. It covers the design of the memory, CPU, and the complete system, including simulation of custom instructions and arithmetic operations.

## 📚 Course Information
- **Course**: ENCS2380 – Computer Organization and Microprocessors  
- **Semester**: Spring 2023  
- **Instructor**: Dr. Yazan Abu Farha  
- **University**: Birzeit University  
- **Group Members**:  
  - [Your Name]  
  - [Partner Name(s)]  

## 📘 Project Overview

This project simulates a basic computer architecture using:
- A **16-bit memory** system
- A **CPU** with an accumulator (AC), instruction register (IR), and program counter (PC)
- An **Arithmetic Logic Unit (ALU)** with status flags (Zero, Negative, Carry, Overflow)
- An **instruction set** that includes Load, Store, ADD, Sub, Mul, Div, and Branching operations

### 📐 Instruction Format
- **16-bit instruction**: `Opcode (4 bits) | Mode bit (1 bit) | Address/Immediate (11 bits)`
- **Mode Bit**:  
  - `M = 1`: Memory address mode  
  - `M = 0`: Immediate constant (signed, 2's complement)

### 🧮 Supported Instructions
| Instruction | Opcode | Description                       |
|------------|--------|-----------------------------------|
| Load       | 0001   | Load data into AC from memory     |
| Store      | 0010   | Store AC into memory              |
| ADD        | 0011   | Add memory data to AC             |
| Sub        | 0100   | Subtract memory data from AC      |
| Mul        | 0101   | Multiply memory data with AC      |
| Div        | 0110   | Divide AC by memory data          |
| Branch     | 0111   | Jump to a specific memory address |
| BRZ        | 1000   | Branch if Zero Flag is set        |

## 🧠 Implementation Modules

### 1. Memory Module
- Implemented using a register array: `reg [15:0] memory[0:N-1];`
- Supports read/write operations via MAR (address) and MBR (data buffer)

### 2. CPU Module
- Registers: AC, PC, IR
- ALU with status flags
- Control Unit manages execution cycles for each instruction
- Interacts with memory through address and data lines

### 3. Top-Level System
- Combines CPU and Memory into one complete system
- Can be instantiated as a Verilog schematic or top module

## 🧪 Simulations

### ✅ Task 1: Simple Program
- Program to compute: `MEM[12] = MEM[10] + MEM[11]`
- Machine Code: Load [10] -> 0001 1 00000001010 ADD [11] -> 0011 1 00000001011 Store [12] -> 0010 1 00000001100


### ✅ Task 2: Arithmetic Expression
- Expression: `Y = (A + B * C - 5) / (D + E + 1)`
- Memory-mapped variables:  
- A = MEM[20] = 2  
- B = MEM[21] = 3  
- C = MEM[22] = 5  
- D = MEM[23] = 8  
- E = MEM[24] = -5  
- Y = MEM[25]

- Assembly instructions and corresponding machine code are stored from memory address 0
- PC initialized to 0 for execution
- Simulation verifies result stored at address 25

### 🖼️ Simulation Output
- All instruction executions are validated using waveform snapshots in a Verilog simulator (e.g., ModelSim, Vivado)
- Correctness of results confirmed by inspecting final memory states

## 📎 Files Included
- `memory.v`: Memory module implementation
- `cpu.v`: CPU design
- `top.v`: Top-level system design
- `testbench.v`: Testbench for simulation
- `waveforms/`: Snapshot images of simulation output
- `Project_Report.pdf`: Project documentation and discussion

## 🧩 Future Improvements
- Add support for more complex instructions (e.g., bitwise operations, conditional branching)
- Expand memory size beyond 64 cells
- Implement pipeline stages or multi-cycle execution
- Create GUI or script for loading programs into memory

## 📜 License
This project is for academic use only. All rights reserved by the authors.

