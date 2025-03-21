# 8-bit Shifter (Shift Left/Right by N-bits)

## Overview
This project implements an **8-bit shifter** designed using Verilog HDL. The shifter can perform both **left** and **right** shifts by a specified number of bits (`N`). The design is fully verified using **UVM (Universal Verification Methodology)** to ensure functionality and correctness.

## Features
- 8-bit input and output.
- Supports both **left** and **right** shifts.
- Shift amount (`N`) is configurable via a 3-bit input (allowing shifts from 0 to 7 bits).
- Implemented in Verilog HDL.
- Verified using a UVM-based testbench with comprehensive coverage.

## Project Structure
```
├── src
│   ├── shifter_8bit.sv           # Main 8-bit shifter design
│   └── shifter_tb.sv             # Testbench for functional verification
├── uvm
│   ├── uvm_env.sv                # UVM environment
│   ├── uvm_agent.sv              # UVM agent
│   ├── uvm_scoreboard.sv         # Scoreboard for result checking
│   └── uvm_test.sv               # UVM test sequences
├── README.md                     # Project documentation
└── Makefile                      # Automation for compilation and simulation
```

## Design Description
### `shifter_8bit.sv`
- **Inputs:**
  - `data_in` [7:0] - 8-bit data input
  - `shift_amount` [2:0] - 3-bit input specifying the number of bits to shift
  - `shift_direction` - 0 for left shift, 1 for right shift
- **Output:**
  - `data_out` [7:0] - 8-bit shifted output

**Logic Explanation:**
- When `shift_direction` = 0, performs a **left shift**.
- When `shift_direction` = 1, performs a **right shift**.
- Shifting is done using the Verilog shift operators (`<<` and `>>`).

### Sample Code Snippet
```verilog
module shifter_8bit (
    input [7:0] data_in,
    input [2:0] shift_amount,
    input shift_direction,
    output [7:0] data_out
);

    assign data_out = (shift_direction) ? data_in >> shift_amount : data_in << shift_amount;

endmodule
```

## Testbench (`shifter_tb.sv`)
- Initializes signals and applies test cases for both left and right shifts.
- Uses `$display` statements to log results.
- Ensures the output matches expected values.

### Sample Testbench Output
```
time=10: data_in=00110011 | shift_amount=2 | direction=0 ----- data_out=11001100
time=20: data_in=00110011 | shift_amount=2 | direction=1 ----- data_out=00001100
```

## UVM Verification
- Utilizes UVM components such as `uvm_agent`, `uvm_driver`, and `uvm_scoreboard`.
- Ensures the design passes various corner cases and achieves 100% functional coverage.

## Simulation Instructions
1. Clone the repository:
   ```bash
   git clone <repo-link>
   cd 8-bit-shifter
   ```
2. Run the testbench:
   ```bash
   make run_tb
   ```
3. For UVM verification:
   ```bash
   make run_uvm
   ```

## Tools Used
- **EDA Playground** (for quick code testing)
- **Verilog HDL** (for design implementation)
- **UVM** (for robust verification)
- **OpenROAD Flow** (for synthesis and implementation)

## Future Improvements
- Add parameterized width for flexible bit-width shifting.
- Implement barrel shifter logic for faster and efficient shifting.

## CONTRIBUTION
JAGDISH BIRADAR 
VIJAYLAXMI
