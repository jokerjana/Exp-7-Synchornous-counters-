```
Name : Janarthanan B
Reg no : 212223100014
```

# Exp-6-Synchornous-counters - up counter and down counter 

## AIM: 
To implement 4 bit up and down counters and validate  functionality.

## HARDWARE REQUIRED:  
– PC, Cyclone II , USB flasher

## SOFTWARE REQUIRED:   
Quartus prime

## THEORY 

### UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.

Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, four-bit count:


Four-bit “Up” Counter
![image](https://user-images.githubusercontent.com/36288975/169644758-b2f4339d-9532-40c5-af40-8f4f8c942e2c.png)



### DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter

### Procedure
1.Create a New Project: Open Quartus and create a new project by selecting "File" > "New Project Wizard." Follow the wizard's instructions to set up your project, including specifying the project name, location, and target device (FPGA). 2.Create a New Design File:

Once the project is created, right-click on the project name in the Project Navigator and select "Add New File." Choose "Verilog HDL File" or "VHDL File," depending on your chosen hardware description language. ⦁ Write the Combinational Logic Code:

Open the newly created Verilog or VHDL file and write the code for your combinational logic. 3.Compile the Project: To compile the project, click on "Processing" > "Start Compilation" in the menu. Quartus will analyze your code, synthesize it into a netlist, and perform optimizations based on your target FPGA device. 4.Analyze and Fix Errors:

If there are any errors or warnings during the compilation process, Quartus will display them in the Messages window. Review and fix any issues in your code if necessary. View the RTL diagram. 5.Verification: Click on "File" > "New" > "Verification/Debugging Files" > "University Program VWF". Once Waveform is created Right Click on the Input/Output Panel > " Insert Node or Bus" > Click on Node Finder > Click On "List" > Select All.

Give the Input Combinations according to the Truth Table and then simulate the Output Waveform.


## PROGRAM :

### UP COUNTER :
```
module exp_6(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
	A[2]=(((A[0])&(A[1]))^A[2]);
	A[1]=(A[0])^A[1];
	A[0]=A[0]^1;
end
endmodule
```

### DOWN COUNTER :
```
module EXP_6B(clk,A);
input clk;
output reg[2:0]A;
always @(posedge clk)
begin
	A[2]=(((~A[0])&(~A[1]))^A[2]);
	A[1]=(~A[0])^A[1];
	A[0]=1^A[0];
end
endmodule
```

## RTL RELAIZATION : 

### UP COUNTER:
![image](https://github.com/jokerjana/Exp-7-Synchornous-counters-/assets/147173630/0667f576-4dbe-422f-86f0-19ecb1fce99e)

### DOWN COUNTER:
![image](https://github.com/jokerjana/Exp-7-Synchornous-counters-/assets/147173630/76c49f73-dc09-45bb-9f8f-0baf0fdcf137)


### TIMING DIGRAMS FOR COUNTER :

### UP COUNTER :
![image](https://github.com/jokerjana/Exp-7-Synchornous-counters-/assets/147173630/c7fe0080-6291-4f56-bbea-907c41eaadc2)

### DOWN COUNTER :
![image](https://github.com/jokerjana/Exp-7-Synchornous-counters-/assets/147173630/d66c42e5-2aeb-4be5-83d2-468b8d5003ce)


## TRUTH TABLE :

### UP COUNTER :
![image](https://github.com/jokerjana/Exp-7-Synchornous-counters-/assets/147173630/c6b23084-5d8f-4e49-bce4-80ba915952b1)

### DOWN COUNTER :
![image](https://github.com/Raji1009/Exp-7-Synchornous-counters-/assets/89059861/409de45b-b9cc-4193-9f8a-f91edde7c0c4)


### RESULTS 
By this we have verified the truth table of 4-bit up-counter using verilog.
