
# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.       
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                             
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.       
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                            
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.                      
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.       
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.       
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.       
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.       
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.       

## Encoder
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)
### Verilog code:
```
module encoder(d,a,b,c);
input [7:0]d;
output a,b,c;
or(a,d[4],d[5],d[6],d[7]);
or(b,d[2],d[3],d[6],d[7]);
or(c,d[1],d[3],d[5],d[7]);
endmodule
```
### Output Waveform:
![image](https://github.com/NMRohith/VLSI-LAB-EXP-2/assets/163638659/89f8d4cf-4159-48bd-b7b8-4c1a54ba0251)

## Decoder
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)
### Verilog code:
```
module decoder_8(a,b,c,y);
input a,b,c; 
output[7:0]y; 
and gl(y[0],(~a),(~b),(~c)); 
and g2(y[1],(~a),(~b),(c)); 
and g3(y[2],(~a),(b),(~c));
and g4(y[3],(~a),(b),(c));
and g5(y[4],(a),(~b),(~c));
and g6(y[5],(a), (~b), (c));
and g7(y[6], (a), (b), (~c)); 
and g8(y[7], (a), (b), (c));
endmodule
```
### Output Waveform:
![image](https://github.com/NMRohith/VLSI-LAB-EXP-2/assets/163638659/eaf21b89-10f4-4a38-b460-b75d1620ef76)

## Multiplexer
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)
### Verilog code:
```
module mux(a,b,c,d,s0,s1,y);
input a,b,c,d,s0,s1;
output y;
assign y=s1 ?(s0?d:c):(s0?b:a);
endmodule
```
### Output Waveform:
![image](https://github.com/NMRohith/VLSI-LAB-EXP-2/assets/163638659/27dec667-2cb4-4651-8029-46a86be99035)

## Demultiplexer
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)
### Verilog code:
```
module demux(in,s0,s1,s2,d0,d1,d2,d3,d4,d5,d6,d7);
input in,s0,s1,s2;
output d0,d1,d2,d3,d4,d5,d6,d7;
assign d0=(in & ~s2 & ~s1 &~s0),
d1=(in & ~s2 & ~s1 &s0),
d2=(in & ~s2 & s1 &~s0),
d3=(in & ~s2 & s1 &s0),
d4=(in & s2 & ~s1 &~s0),
d5=(in & s2 & ~s1 &s0),
d6=(in & s2 & s1 &~s0),
d7=(in & s2 & s1 &s0);
endmodule
```
### Output Waveform:
![image](https://github.com/NMRohith/VLSI-LAB-EXP-2/assets/163638659/d3147d91-d757-4c64-9f8b-eb37545723cb)

## Magnitude Comparator
### Logic Diagram:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)
### Verilog code:
```
module magcomp(a,b,l,g,e);
input [3:0]a,b;
output reg l,g,e;
always @(*)
begin
if(a>b)
begin
     l=1'b0;
     g=1'b1;
     e=1'b0;
end
else if(a<b)
begin
     l=1'b1;
     g=1'b0;
     e=1'b0;
end
else
begin
     l=1'b0;
     g=1'b0;
     e=1'b1;
end
end
endmodule
```
### Output Waveform:
![image](https://github.com/NMRohith/VLSI-LAB-EXP-2/assets/163638659/f657099b-5ecd-4d1b-a02e-3c3baa9dcea2)

  
## Result
Hence ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR are simulated and synthesised using Xilinx ISE.
