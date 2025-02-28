# csRISC - 32-bit RISC Processor

A 32-bit mini RISC processor implementation targeting AMD-Xilinx Artix-7 FPGA.

## Overview

csRISC is a custom 32-bit RISC processor designed for the Artix-7 FPGA platform. It features a streamlined instruction set, dedicated arithmetic units including Carry Lookahead Adders (CLA), and separate instruction and data memories implemented using Xilinx Block RAM IP cores.

### Key Features

- 32-bit RISC architecture
- Target FPGA: Xilinx Artix-7 (xc7a100t-csg324-3)
- Dedicated ALU with CLA implementation
- Separate instruction and data memory using Block RAM
- Register file with multiple read/write ports
- Branch prediction mechanism

## Hardware Requirements

- AMD-Xilinx Artix-7 FPGA (xc7a100t-csg324-3)
- Xilinx ISE Design Suite 14.7

## Project Structure

- `rtl/`: RTL source files
  - `core/`: Core processor components
  - `memory/`: Memory interface modules
  - `arithmetic/`: Arithmetic units including CLA
  - `utils/`: Utility modules
- `ip_cores/`: Xilinx IP core configurations
- `sim/`: Simulation testbenches
- `synth/`: Synthesis constraints and reports
- `scripts/`: Build and simulation scripts

## Resource Utilization

- Slice Registers: 1,057 (1% of available)
- Slice LUTs: 1,276 (2% of available)
- Block RAM: Used for instruction and data memory

## Building and Simulation

1. Open Xilinx ISE 14.7
2. Add source files from respective directories
3. Generate IP cores for memories
4. Run synthesis, implementation, and bitstream generation

## Implementation Details

### Memory Configuration
- Instruction Memory: Xilinx Block Memory Generator v7.3
- Data Memory: Xilinx Block Memory Generator v7.3

### Arithmetic Units
- 16-bit Carry Lookahead Adder with augmented 4-bit CLA blocks
- Dedicated Lookahead Carry Unit
