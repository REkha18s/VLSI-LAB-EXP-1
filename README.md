
# SIMULATION OF LOGIC GATES ,ADDERS AND SUBTRACTORS

**AIM:** 
To simulate Logic Gates ,Adders and Subtractors using Vivado 2023.2.

**APPARATUS REQUIRED:**
VIVADO 2023.2

**PROCEDURE:** 

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.


**LOGIC DIAGRAM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/67dad4cb-4df0-44c5-a634-a16768ed5b13)


**VERILOG CODE** 
```
module logicgate(a,b,andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate);
input a,b;
output andgate,orgate,nandgate,norgate,xorgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
nand(nandgate,a,b);
nor(norgate,a,b);
xor(xorgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```

**OUTPUT WAVEFORM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/a77d28cb-e838-4a36-8654-2912dea2a180)



**HALF ADDER**

**LOGIC DIAGRAM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/c998fe32-299b-47ce-8350-031d1b436c53)


**VERILOG CODE**
```
module half_adder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule 

```

**OUTPUT WAVEFORM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/47e697e7-723b-4e98-9629-fbdd509499c5)


**FULL ADDER**

**LOGIC DIAGRAM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/850b49df-9c27-4df4-97e3-5aec9c54e6df)


**VERILOG CODE**
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule
```
**OUTPUT WAVEFORM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/98c55f9b-a110-4a09-81eb-3004dacb8bc6)


**HALF SUBTRACTOR**

**LOGIC DIAGRAM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/9f666098-5bab-4047-9f7c-52f746e33e9a)



**VERILOG CODE**
```
module halfsub(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor(diff,a,b);
and(borrow,~a,b);
endmodule
```
**OUTPUT WAVEFORM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/4ec4a151-3918-42e1-ab74-3a511dbdc932)

**FULL SUBTRACTOR**

**LOGIC DIAGRAM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/a4751ef0-13b7-4101-b45c-36733aea5dbf)

 
**VERILOG CODE** 
```
module fs(a,b,bin,d,bout);
input a,b,bin;
output d,bout;
wire w1,w2,w3;
xor(w1,a,b);
xor(d,w1,bin);
and(w2,~a,b);
and(w3,~w1,bin);
or(bout,w3,w2);
endmodule
```
**OUTPUT WAVEFORM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/70a48bfc-e34f-46fd-b0ca-6215b9addee2)



**RIPPLE CARRY ADDER**

**LOGIC DIAGRAM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/91de4b4f-8bf7-4745-8778-93db4c3f6d33)


**VERILOG CODE** 
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule

module rca_8bit(a,b,cin,s,cout);
input [7:0]a,b;
input cin;
output [7:0]s;
output cout;
wire [7:1]w;
fulladder f1(a[0], b[0], cin, s[0], w[1]);
fulladder f2(a[1], b[1], w[1], s[1], w[2]);
fulladder f3(a[2], b[2], w[2], s[2], w[3]);
fulladder f4(a[3], b[3], w[3], s[3], w[4]);
fulladder f5(a[4], b[4], w[4], s[4], w[5]);
fulladder f6(a[5], b[5], w[5], s[5], w[6]);
fulladder f7(a[6], b[6], w[6], s[6], w[7]);
fulladder f8(a[7], b[7], w[7], s[7], cout);
endmodule
```

**OUTPUT WAVEFORM**

![image](https://github.com/REkha18s/VLSI-LAB-EXP-1/assets/161815097/d1a5df17-4882-4d08-898c-7382aa5e5de4)


**RESULT:**

 Thus the simulation and implementation of Logic Gates, Adders and Subtractors is done and outputs are verified.
