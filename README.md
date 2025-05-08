# Pipelined RISC Processor with Branch Prediction

By: **Phạm Lê Ngọc Sơn**

## Project Overview

This project implements a pipelined RISC processor with branch prediction capabilities in Verilog HDL. The processor architecture incorporates modern CPU design techniques including out-of-order execution, branch prediction, and hazard handling to improve performance.

## Architecture Components

### Pipeline Stages

1. **IF (Instruction Fetch) Stage**
   - Fetches instructions from instruction memory
   - Implements branch prediction using Branch Target Buffer (BTB) and Branch History Buffer (BHB)

2. **ID (Instruction Decode) Stage**
   - Decodes instructions and generates control signals
   - Reads from register file
   - Performs immediate extension

3. **EX (Execute) Stage**
   - ALU operations
   - Branch computation
   - Address calculation for load/store instructions

4. **MEM (Memory) Stage**
   - Handles data memory access for load/store operations

5. **WB (Write Back) Stage**
   - Writes results back to register file

### Special Units

- **ROB (Reorder Buffer) Stage**: Enables out-of-order execution while maintaining in-order commit
- **SQ (Store Queue) Stage**: Handles memory store operations
- **MU (Multiply Unit) Stage**: Dedicated hardware for multiplication operations
- **Hazard Unit**: Detects and resolves data hazards in the pipeline
- **Branch Prediction Units**: BTB (Branch Target Buffer) and BHB (Branch History Buffer)

## Key Features

- **Out-of-Order Execution**: Using Reorder Buffer (ROB) to maintain proper program order for commits
- **Branch Prediction**: Implements sophisticated branch prediction to reduce branch misprediction penalties
- **Data Forwarding**: Resolves data hazards by forwarding results between pipeline stages
- **Pipeline Stalling and Flushing**: Mechanisms to handle hazards and branch mispredictions
- **Specialized Execution Units**: Includes dedicated multiply unit for efficient multiplication operations

## Directory Structure

- `.v` files: Verilog source code for the various modules of the processor
- `.dat` files: Test programs to run on the processor
- `.mpf`, `.cr.mti`: ModelSim project files

## Major Files

- `TOP_MODULE.v`: The top-level module connecting all components
- `IF_stage.v`, `ID_stage.v`, etc.: Individual pipeline stage implementations
- `ALU.v`: Arithmetic Logic Unit implementation
- `BTB.v`, `BHB.v`: Branch prediction units
- `hazard_unit.v`: Pipeline hazard detection and resolution
- `register_file.v`: CPU register file
- `data_mem.v`, `instr_mem.v`: Memory modules
- `Test_Program.dat`, `Test_Program2.dat`, `Test_Program3.dat`: Sample test programs

## How to Use

### Requirements

- ModelSim or compatible Verilog simulator

### Simulation Steps

1. Open the ModelSim project (`Capstone1.mpf`)
2. Compile all Verilog files in the project
3. Run the simulation with the testbench `RISC_tb.v`
4. Use the waveform viewer to analyze processor operation

### Running Test Programs

The project includes three test program files:
- `Test_Program.dat`: Basic functionality test
- `Test_Program2.dat`: Branch prediction test
- `Test_Program3.dat`: Complex operations test

To run a different test program, modify the instruction memory initialization in the `instr_mem.v` file to point to the desired test file.

## Performance Analysis

The processor achieves improved performance through:
- Branch prediction to reduce branch misprediction penalties
- Out-of-order execution to maximize instruction-level parallelism
- Specialized execution units for common operations

## Future Enhancements

Potential improvements to the processor design:
- Implementing a cache hierarchy
- Adding more specialized execution units
- Extending the instruction set
- Implementing more advanced branch prediction algorithms


