# 32Bit-ALU_Synthesis

## Aim:

Synthesize 32 Bit ALU design using Constraints and analyse area and Power reports.

## Tool Required:

Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

Synthesis: Genus

module alu_32bit_case(y,a,b,f);

input [31:0]a;

input [31:0]b;

input [2:0]f;

output reg [31:0]y;

always@(*)

begin

case(f)

3'b000:y=a&b; //AND Operation

3'b001:y=a|b; //OR Operation

3'b010:y=~(a&b); //NAND Operation

3'b011:y=~(a|b); //NOR Operation

3'b100:y=a^b; //XOR Operation

3'b101:y=~(a^b); //XNOR Operation

3'b110:y=~a; //NOT of a

3'b111:y=~b; //NOT of b

endcase

end

endmodule

PROGRAM FOR TCL:
read_libs /cadence/install/FOUNDRY-01/digital/90nm/dig/lib/slow.lib

read_hdl alu_32bit.v

elaborate

read_sdc input_constraints.sdc

syn_generic

report_area

syn_map

report_area

syn_opt

report_area 

report_area > alu_32bit_area.txt

report_power > alu_32bit_power.txt

write_hdl > alu_32bit_netlist.v

gui_show

### Step 1: Getting Started

Synthesis requires three files as follows,

◦ Liberty Files (.lib)

◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

### Step 2 : Performing Synthesis

The Liberty files are present in the library path,

• The Available technology nodes are 180nm ,90nm and 45nm.

• In the terminal, initialise the tools with the following commands if a new terminal is being
used.

◦ csh

◦ source /cadence/install/cshrc

• The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

• Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.

#### Synthesis RTL Schematic :
![WhatsApp Image 2025-05-20 at 10 33 10_1d9d1d4f](https://github.com/user-attachments/assets/742adb7c-0611-435c-9419-20d82f600d7c)


#### Area report:
![WhatsApp Image 2025-05-20 at 10 33 11_50819427](https://github.com/user-attachments/assets/8c5ca07f-5b8a-4ae0-af76-4ffd49fe9bff)


#### Power Report:
![WhatsApp Image 2025-05-20 at 10 33 12_e05e897c](https://github.com/user-attachments/assets/b62741a1-eb8a-4041-aa79-a92621499f1f)

![WhatsApp Image 2025-05-20 at 10 33 12_7435ba73](https://github.com/user-attachments/assets/baf7ef0e-4b31-454b-b453-5140f4fde962)

![WhatsApp Image 2025-05-20 at 10 33 11_1b62427c](https://github.com/user-attachments/assets/f176d497-a6a7-426f-a088-cacf0e767c71)

#### Result: 

The generic netlist of 32 bit ALU  has been created, and area, power reports have been tabulated and generated using Genus.
