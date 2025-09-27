# 4Bit-Up-Down-Asynchronous-Reset-Counter-Synthesis

## Aim:

Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

◦ SDC (Synopsis Design Constraint) File (.sdc)

 ### Step 2 : Creating an SDC File

•	In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

•	The SDC File must contain the following commands;

create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

set_clock_transition -rise 0.1 [get_clocks "clk"]

set_clock_transition -fall 0.1 [get_clocks "clk"]

set_clock_uncertainty 0.01 [get_ports "clk"]

set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

ii, iii → Sets Clock Rise and Fall time to 100ps.

iv → Sets Clock Uncertainty to 10ps.

v, vi → Sets the maximum limit for I/O port delay to 1ps.

### Step 3 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :

<img width="1920" height="1080" alt="Screenshot 2025-09-15 092339" src="https://github.com/user-attachments/assets/d39251a8-ddbe-4db1-a124-4cfefdcec99d" />



#### Area report:
![WhatsApp Image 2025-09-27 at 09 36 54_642e8b86](https://github.com/user-attachments/assets/85dca7cd-6b41-4eb3-b8de-ca65d3c723d9)



#### Power Report:
<img width="1920" height="1080" alt="Screenshot 2025-09-15 092608" src="https://github.com/user-attachments/assets/fc5932a2-4595-4646-a5df-48eacbe53c56" />



#### Timing Report: 
![WhatsApp Image 2025-09-27 at 09 36 58_c9af1b76](https://github.com/user-attachments/assets/d0511db7-9906-48e9-af46-74b487991b8e)



#### Result: 

The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.









