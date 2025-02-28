# Running the csRISC Processor

## Prerequisites
1. Xilinx ISE Design Suite 14.7
2. AMD-Xilinx Artix-7 FPGA board
3. Memory initialization files (COE files)

## Step-by-Step Instructions

### 1. Project Setup
1. Launch Xilinx ISE 14.7
2. Create a new project:
   - File → New Project
   - Set device properties:
     - Family: Artix-7
     - Device: xc7a100t
     - Package: csg324
     - Speed: -3

### 2. Generate IP Cores
1. Generate Instruction Memory:
   ```tcl
   cd scripts
   source create_instructions.tcl
   ```
2. Generate Data Memory:
   ```tcl
   source create_datastore.tcl
   ```

### 3. Add Source Files
1. Right-click on project → Add Source
2. Add all files from:
   - rtl/core/
   - rtl/memory/
   - rtl/arithmetic/
   - ip_cores/instructions/
   - ip_cores/datastore/

### 4. Memory Initialization
1. Copy your instruction COE file to `sim/memory_init/instr.coe`
2. Copy your data COE file to `sim/memory_init/data.coe`
3. Update IP core configurations to point to these COE files

### 5. Simulation
1. Add testbench files from sim/testbench/
2. Set KGP_RISC_tb as top module
3. Run Behavioral Simulation:
   - Double-click "Simulate Behavioral Model"
   - View waveforms in ISim

### 6. Synthesis and Implementation
1. Set KGP-RISC as top module
2. Run Synthesis:
   - Double-click "Synthesize - XST"
3. Run Implementation:
   - Double-click "Implement Design"
4. Generate Programming File:
   - Double-click "Generate Programming File"

### 7. FPGA Programming
1. Connect FPGA board
2. Open Impact:
   - Tools → iMPACT
3. Configure target device
4. Program FPGA with generated bitstream

## Common Issues and Solutions

1. IP Core Generation Errors:
   - Ensure Xilinx ISE is in system PATH
   - Check COE file paths are correct
   - Verify IP core versions match (7.3)

2. Simulation Errors:
   - Check memory initialization file syntax
   - Verify all source files are added to project
   - Ensure testbench is set as top module

3. Synthesis Warnings:
   - Address unconstrained I/O warnings by adding constraints
   - Check clock definitions in UCF file

## Debug Tips

1. Use ISim waveform viewer to debug:
   - Add key signals to wave window
   - Use markers for important events
   - Check clock and reset behavior

2. Monitor synthesis reports:
   - Check resource utilization
   - Review timing constraints
   - Address critical warnings

3. Use ChipScope (optional):
   - Insert ILA cores for real-time debugging
   - Monitor internal signals during runtime