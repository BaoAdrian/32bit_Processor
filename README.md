# 32bit_Datapath_Controller
32-bit processor with Datapath and Controller designed to support various operations.


<h1> Latest Adjustments </h1>
<ul>

  <li> 10/27/2018 - Modify and implement logic for Mux32Bit2to1, PCAdder, and ProgramCounter Modules. Testbenches included for all of them with their respecitve waveforms produced (Behavioral and Post-Synthesis) included in their folders. </li>
  <li> 10/28/2018 - Modify and implement logic for Sign Extension Module. Testbench ran and verified with included waveforms produced (Behavioral and Post-Synthesis Simulations). </li>
  <li> 11/01/2018 - Implement 32-Bit ALU Logic for various arithmetic operations including: </li>
  <ul>
    <li> ADD/SUB/MULT </li>
    <li> AND/OR </li>
    <li> A&ltB, A==B, A!=B </li>
    <li> Bitwise Shifting: A&lt&ltB, A&gt&gtB </li>
    <li> Bitwise Right Rotation A ROTR B </li>
  </ul>
  <li> 11/09/2018 - Updated ALU32Bit Module and TestBench to include all test cases provided in specifications. The following ALU32Bit Modules were updated: </li>
  <ul>
    <li> MULT </li>
    <li> A << B </li>
    <li> A >> B </li>
    <li> A ROTR B </li>
    <li> CLO </li>
    <li> CLZ </li>
  </ul>
  <li> 11/09/2018 - Implemented TestBench for InstructionMemory and DataMemory Modules with their Post-Synthesis Simulation waveforms included in their respective folders. </li>

</ul>

<br>

<h1> Task0 - DataPath Components Implementation </h1>
<p> Eight DataPath Components implemented including: 32-Bit 2x1 Multiplexor, PCAdder, Program Counter, Sign Extension, 32x32 Register File, 32-Bit ALU with 13 supported operations, Instruction Memory, and Data Memory. </p>

<h3> 32-Bit 2x1 Mux Module </h3>
<ul>
  <li> The mux takes two 32-Bit inputs and based on the selector (sel) input, will allow either inA or inB to pass through:
    
``` Verilog
      
always @ (sel) begin
  if (sel)
     out <= inA;
  else
     out <= inB;
end
      
```
      
  
  </li>
  <li> Behavioral and Post-Synthesis Functional Simulations yeilded the following waveform: </li>
  <br>
</ul>
  <img src = "Mux32Bit2to1/32Bit2to1Mux_Waveform.PNG" width = "900" height = "200" hspace = "10" alt = "32-Bit 2x1 Mux Waveform"/>
  
  
  
  
  
<h3> PCAdder Module </h3>
<ul>
   <li> A hardwired Adder that adds 4 to the input PCResult and sets that outcome to the output PCAddResult </li>
   <li> Behavioral and Post-Synthesis Functional Simulations yeilded the following waveform: </li>
   <br>
</ul>
  <img src = "PCAdder/PCAdder_Waveform.PNG" width = "900" height = "200" hspace = "10" alt = "32-Bit 2x1 Mux Waveform"/>





<h3> Program Counter Module </h3>
<ul>
   <li> A Counter that at each Posedge of the Clk, will assign the output PCResult to either all 0's or the 32-Bit input Address, depending if Reset is active. </li>
   <li> Behavioral and Post-Synthesis Functional Simulations yeilded the following waveform: </li>
   <br>
</ul>
  <img src = "Program Counter/ProgramCounter_Waveform.PNG" width = "900" height = "200" hspace = "10" alt = "32-Bit 2x1 Mux Waveform"/>






<h3> Sign Extension Module </h3>
<ul>
   <li> Module that analyzes the most significant bit and extends the value if necessary depending on the value of the MSB. If the MSB is 0, it will extend the input, in, from 16-bits to 32-bits by creating a new output and assign [15:0] to the current values of in and populate the values of bits [31:16] with all 0's. On the other hand, if MSB is 1, it will create a new output and assign [15:0] to the current values of in and populate the values of bits [31:16] with all 1's. </li>
  
```Verilog
assign out = {{16{in[15]}}, in};
```
   <li> Behavioral and Post-Synthesis Functional Simulations yeilded the following waveform(s): </li>
   <br>
</ul>
  <img src = "Sign Extension/SignExtension_Waveform(1).PNG" width = "900" height = "200" hspace = "10" alt = "32-Bit 2x1 Mux Waveform"/>
  <img src = "Sign Extension/SignExtension_Waveform(2).PNG" width = "900" height = "200" hspace = "10" alt = "32-Bit 2x1 Mux Waveform"/>
  <img src = "Sign Extension/SignExtension_Waveform(3).PNG" width = "900" height = "200" hspace = "10" alt = "32-Bit 2x1 Mux Waveform"/>
