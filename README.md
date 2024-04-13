# VLSI-LAB-EXPERIMENTS
AIM:

   To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: 

   Xilinx 14.7 Spartan6 FPGA

PROCEDURE: 

STEP:1 Start the Xilinx navigator, Select and Name the New project.

STEP:2 Select the device family, device, package and speed. 

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. 

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window.

STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.

STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 

STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.

STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

STEP:12 Load the Bit file into the SPARTAN 6 FPGA 

# Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

# verilog code:
# logic gate:
```
module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b);  
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
# half adder:
```
# output
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/290ac22f-57c3-4aaa-807b-f3e2bcbf5d26)

Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)
# truth table:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/50797694-ee71-4883-bcf6-96d1436d7904)

# verilog code:
# half adder:
```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule
```
# output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/ab49185b-602a-4e78-8e0b-a899085e6783)

Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)
# truth table:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/5b4e265a-7396-49fb-8650-6c226357e757)

# verilog code:
# full adder:
```
module fulladder(sum, cout, a,b,c);
input a,b,c;
output sum, cout;
wire w1,w2,w3,w4,w5;
xor x1(w1,a,b);
xor x2(sum,w1,c);
and al(w2,a,b);
and a2(w3,b,c);
and a3(w4,a,c);
or o1(w5,w2,w3); 
or o2(cout,w5w4);
endmodule
```
# output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/3256b11f-db14-41e7-9dc6-943470244286)

Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)
# truth table:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/0df7298a-d114-4578-9da6-c1403d72012f)

# verilog code:
# half subtractor:
```
module hs(diff,borrow,a,b);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
# full subtractor:
```
# output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/21bac1fb-b49c-40d6-b34f-812b1f9c3cae)





Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)
# truth table:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/b385a923-a779-4918-829c-135706fff4db)

# verilog code:
# full subtractor:
```
module fs(a,b,bin,d,out);
input a,b,bin;
output d,out;
assign d=a^b^bin;
assign out=(~a&b)|((~a^b)&bin);
endmodule
```
# output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/252c1d5d-7ef1-4809-bd4f-f369b8374abb)

8 Bit Ripple Carry Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)
# truth table:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/31572dae-8123-4b93-88cf-24c2663af458)


# verilog code:
```
module rc(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
module rca(a,b,cin,sum,cout);
input [7:0]a,b;
input cin;
output [7:0]sum;
output cout;
wire w1,w2,w3,w4,w5,w6,w7;
rc rc1(a[0],b[0],cin,sum[0],w1);
rc rc2(a[1],b[1],w1,sum[1],w2);
rc rc3(a[2],b[2],w2,sum[2],w3);
rc rc4(a[3],b[3],w3,sum[3],w4);
rc rc5(a[4],b[4],w4,sum[4],w5);
rc rc6(a[5],b[5],w5,sum[5],w6);
rc rc7(a[6],b[6],w6,sum[6],w7);
rc rc8(a[7],b[7],w7,sum[7],cout);
endmodule
```
# output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160569525/6d8912e5-0065-4e2a-9061-f872e78e64a7)


RESULT:

Hence Logic Gates,Adders and Subtractor is stimulated and synthesised using Xilinx ISE
