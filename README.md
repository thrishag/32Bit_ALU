# Exp-No:3 - 32 Bit ALU Design - Write Verilog Code and Verify the Functionality using Test-bench ( Using Frontend tool - nclaunch in cadence).

**Aim:** <br>
<br>
&emsp;&emsp;Write a verilog code for 32 bit ALU supporting four logical and four arithmetic operations,use case statement and if statement for ALU behavioral modeling.

&emsp;&emsp;To Verify the Functionality using Test Bench.<br>
<br>

**Tool Required:** <br>
<br>
&emsp;&emsp;Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)<br>
<br>

**Design Information and Bock Diagram:** <br>
<br>
&emsp;&emsp;The ALU will take in two 32-bit values, and control line. An Arithmetic unit does the following task like addition subtraction, multiplication and logical operations. As the input is given in 32 bit we get 32 bit output. The arithmetic will show only one output at a time so a selector is necessary to select one of the operator.<br>
<br>

![image](https://github.com/user-attachments/assets/e574788c-253f-46da-8468-298fe2844f7a)

<br>

**<p align="center">Fig 1 : Block Diagram of 32 Bit ALU** 

<br>

**Creating a Work space:** <br>
<br>
&emsp;&emsp;Create a folder in your name (Note: Give folder name without any space) and Create a new sub-Directory name it as Exp3 or alu_32bit for the Design and open a terminal from the Sub-Directory.<br>
<br>

**Creating Source Codes:** <br>
<br>
&emsp;&emsp;In the Terminal, type gedit <filename>.v (ex: gedit alu_32bit.v). 

&emsp;&emsp;A Blank Document opens up into which the following source code can be typed down. 

&emsp;&emsp;(Note : File name should be with HDL Extension)<br>
<br>

**a)To Verify the Functionality using Test Bench** <br>
<br>

**Source Code – Using Case Statement:**


```


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
3'b100:y=a+b; //Addition
3'b101:y=a-b; //Subtraction
3'b110:y=a*b; //Multiply
default:y=32'bx;
endcase
end
endmodule

```

&emsp;&emsp;Use Save option or Ctrl+S to save the code or click on the save option from the top most right corner and close the text file.
<br>

**Creating Test bench:** <br>
<br>
&emsp;&emsp;Similarly, create your test bench using gedit <filename_tb>.v or <filename_tb>.vhdl to open a new blank document (alu_32bit_tb_case).<br>
<br>

**Test Bench:**
```

module alu_32bit_tb_case;
reg [31:0]a;
reg [31:0]b;
reg [2:0]f;
wire [31:0]y;
alu_32bit_case test2(.y(y),.a(a),.b(b),.f(f));
initial
begin
a=32'h00000000;
b=32'hFFFFFFFF;
#10 f=3'b000;
#10 f=3'b001;
#10 f=3'b010;
#10 f=3'b011;
#10 f=3'b100;
#10 f=3'b101;
#10 f=3'b110;
#10;$stop;
end
endmodule

```

&emsp;&emsp;Use Save option or Ctrl+S to save the code or click on the save option from the top most right corner and close the text file.<br>
<br>
**Functional Simulation:** <br>
<br>
&emsp;&emsp;Invoke the cadence environment by type the below commands 

&emsp;&emsp;&emsp;&emsp;tcsh (Invokes C-Shell) 

&emsp;&emsp;&emsp;&emsp;source /cadence/install/cshrc (mention the path of the tools) 

&emsp;&emsp;&emsp;&emsp;(The path of cshrc could vary depending on the installation destination)
      
&emsp;&emsp;After this you can see the window like below 
<br>

![Picture1](https://github.com/user-attachments/assets/685a95cf-0843-4bf9-841f-f2d21b737da1)

<br>

**<p align="center">Fig 2: Invoke the Cadence Environment**

<br>

&emsp;&emsp;To Launch Simulation tool 

&emsp;&emsp;&emsp;&emsp;linux:/> nclaunch -new& // “-new” option is used for invoking NCVERILOG for the first time for any design 

&emsp;&emsp;&emsp;&emsp;or

&emsp;&emsp;&emsp;&emsp;linux:/> nclaunch& // On subsequent calls to NCVERILOG 

&emsp;&emsp;It will invoke the nclaunch window for functional simulation we can compile,elaborate and simulate it using Multiple Step .

<br>

![Picture2](https://github.com/user-attachments/assets/0f120a86-c3a1-440c-a2b0-74ecf93c4519)

<br>

**<p align="center">Fig 3: Setting Multi-step simulation**

<br>

&emsp;&emsp;Select Multiple Step and then select “Create cds.lib File” as shown in below figure 

&emsp;&emsp;Click the cds.lib file and save the file by clicking on Save option 

<br>

![10_6_2024 2_48_15 PM](https://github.com/user-attachments/assets/7f774714-7d5d-40b8-97c3-0c39573770b4)

<br>

**<p align="center">Fig 4:cds.lib file Creation**

<br>

&emsp;&emsp;Save cds.lib file and select the correct option for cds.lib file format based on the HDL Language and Libraries used. 

&emsp;&emsp;Select “Don’t include any libraries (verilog design)” from “New cds.lib file” and click on “OK” as in below figure .

&emsp;&emsp;We are simulating verilog design without using any libraries 

&emsp;&emsp;A Click “OK” in the “nclaunch: Open Design Directory” window as shown in below figure 

<br>

![Screenshot 2024-10-05 085242](https://github.com/user-attachments/assets/99961b87-6afb-4942-9bcf-4d8808cf056c)

<br>

**<p align="center">Fig 5: Selection of Don’t include any libraries**

<br>

&emsp;&emsp;A ‘NCLaunch window’ appears as shown in figure below

&emsp;&emsp;Left side you can see the HDL files. Right side of the window has worklib and snapshots directories listed. 

&emsp;&emsp;Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation .

&emsp;&emsp;To perform the function simulation, the following three steps are involved Compilation, Elaboration and Simulation. 

<br>

![Screenshot 2024-10-05 085312](https://github.com/user-attachments/assets/c1d66c70-e898-48b9-8b2c-f731fe860597)

<br>

**<p align="center"> Fig 6: Nclaunch Window**

<br>

**Step 1: Compilation:** <br>
<br>
&emsp;&emsp;Process to check the correct Verilog language syntax and usage 

&emsp;&emsp;Inputs: Supplied are Verilog design and test bench codes 

&emsp;&emsp;Outputs: Compiled database created in mapped library if successful, generates report else error reported in log file <br>
<br>

**Steps for compilation:** <br>
<br>
&emsp;&emsp;1. Create work/library directory (most of the latest simulation tools creates automatically)
   
&emsp;&emsp;2. Map the work to library created (most of the latest simulation tools creates automatically)
   
&emsp;&emsp;3. Run the compile command with compile options
   
&emsp;&emsp;i.e Cadence IES command for compile: ncverilog +access+rwc -compile fa.v 

&emsp;&emsp;Left side select the file and in Tools : launch verilog compiler with current selection will get enable. Click it to compile the code 

&emsp;&emsp;Worklib is the directory where all the compiled codes are stored while Snapshot will have output of elaboration which in turn goes for simulation 

<br>

![Screenshot 2024-10-05 085639](https://github.com/user-attachments/assets/f1a68c5c-41fd-4e7f-965a-aca05848b385)

<br>

**<p align="center"> Fig 7: Compiled database in worklib**

<br>

&emsp;&emsp;After compilation it will come under worklib you can see in right side window

&emsp;&emsp;Select the test bench and compile it. It will come under worklib. Under Worklib you can see the module and test-bench. 

&emsp;&emsp;The cds.lib file is an ASCII text file. It defines which libraries are accessible and where they are located. It contains statements that map logical library names to their physical directory paths. For this Design, you will define a library called “worklib”
<br>

**Step 2: Elaboration:** <br>
<br>
&emsp;&emsp;To check the port connections in hierarchical design

&emsp;&emsp;Inputs: Top level design / test bench Verilog codes 

&emsp;&emsp;Outputs: Elaborate database updated in mapped library if successful, generates report else error reported in log file 
<br>

**Steps for elaboration:**  <br>
<br>
&emsp;&emsp;Run the elaboration command with elaborate options 

&emsp;&emsp;1.It builds the module hierarchy

&emsp;&emsp;2.Binds modules to module instances 

&emsp;&emsp;3.Computes parameter values

&emsp;&emsp;4.Checks for hierarchical names conflicts

&emsp;&emsp;5.It also establishes net connectivity and prepares all of this for simulation

&emsp;&emsp;After elaboration the file will come under snapshot. Select the test bench and simulate it.

<br>

![Screenshot 2024-10-05 085728](https://github.com/user-attachments/assets/3ed91b3e-c76b-4366-aa70-0b70c600502e)

<br>

**<p align="center">Fig 8: Elaboration Launch Option**

<br>

**Step 3: Simulation:** <br>
<br>
&emsp;&emsp;Simulate with the given test vectors over a period of time to observe the output behaviour. 

&emsp;&emsp;Inputs: Compiled and Elaborated top level module name 

&emsp;&emsp;Outputs: Simulation log file, waveforms for debugging 

&emsp;&emsp;Simulation allow to dump design and test bench signals into a waveform 

&emsp;&emsp;Steps for simulation – Run the simulation command with simulator options


![Picture6](https://github.com/user-attachments/assets/29ed6d1e-5949-4e7a-8611-34f126030463)

<br>

**<p align="center">Fig 9: Design Browser window for simulation**

<br>

![Picture7](https://github.com/user-attachments/assets/e2342407-785d-497f-9b8e-a96ee3ec4871)

<br>

**<p align="center"> Fig 10:Simulation Waveform Window**

<br>

![Picture8](https://github.com/user-attachments/assets/af1b0083-5727-41db-b3ed-c744ed0be547)

<br>
**<p align="center">  Fig 11:Simulation Waveform Window**
<br>
**Result:** <br>
<br>
&emsp;&emsp;The functionality of a 4bit_up-down asynchronous reset Counter was successfully verified using a test bench and simulated with the nclaunch tool.
