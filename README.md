# VLSI-LAB-EXPERIMENTS
## AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7 Spartan6 FPGA

## PROCEDURE: 
STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## Logic Diagram :

### Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


### Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


### Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


### Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



### Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



### 8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



## VERILOG CODE:
### Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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
```
### Half Adder
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
### Half Subtractor
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
### Full Adder
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
### Full Subtractor
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
### 8 bit ripple carry adder
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```
## OUTPUT:
### Logic Gates:

#### AND GATE
![Screenshot 2024-02-17 142507](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/a8758c46-a269-4f00-9ef7-44b8e171ce3f)

#### OR GATE
![Screenshot 2024-02-17 143056](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/0d4d8b4c-a494-46cb-9114-346a40fe1354)

#### NAND GATE
![Screenshot 2024-02-17 143955](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/72109513-6be1-451a-aaa6-e31a5430f0ec)

#### NOR GATE
![NORO](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/d2685da3-c7ca-49b1-a32c-eda20a2d971e)

#### XOR GATE
![Screenshot 2024-02-17 144406](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/27cd4c0e-03db-4b45-a963-14dd240cf939)

#### XNOR GATE
![Screenshot 2024-02-17 144811](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/e63c4944-5778-4e13-b26d-5ed5bda23239)

#### NOT GATE
![Screenshot 2024-02-17 145135](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/eee7f73b-0657-4b01-9ea5-7e44a9c97cb0)

### Half Adder
![Screenshot 2024-02-17 134312](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/917254df-914c-4be1-8933-f56982573f05)

### Half Subtractor
![Screenshot 2024-02-17 140409](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/f09eeb8d-022c-4dfd-a7f5-2b645f60d61c)

### Full Adder
![Screenshot 2024-02-17 141614](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/b41a4328-9884-4af0-91be-240cf480c9a8)

### Full Subtractor
![FSUB](https://github.com/Dhinesh0024/VLSI-LAB-EXP-1/assets/160568927/f3dbd397-7ffc-430f-910e-f9e3a9c67c4d)

### 8 Bit Ripple Carry Adder 


## RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.


