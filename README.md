# Developed by: Roopak C S
# Register Number: 212223220088 
# EXP-6 Synchornous-counters - up counter and down counter 
## Aim: 
To implement 4 bit up and down counters and validate  functionality.
## Equipments required:
Hardware required:
PC, Cyclone II , USB flasher

Software required:
Quartus prime

## Theory:
### Up Counter:
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



### Down Counter: 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.
![image](https://user-images.githubusercontent.com/36288975/169644844-1a14e123-7228-4ed8-81a9-eb937dff4ac8.png)


4-bit Count Down Counter
## Procedure:
1.Create a new project in Quartus2 software . 

2.Name the project as uc for upcounter and dc for down counter.

3.Create a new verilog hdl file in the project file.

4.Name the module declare as dc and uc for down counter and upcounter. 

5.Within the module declare input and output variables.

6.Create a loop using if-else with condition parameter as reset.

7.End the loop. 

8.End the module

## Program: 
### Up Counter:
````
module upcounter(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3 = (q1&q2)^q3;
q2 = q1^q2;
q1 = 1^q1;
end
endmodule
````
### Down Counter:
````
module downcounter(clk,q1,q2,q3);
input clk;
output reg q1,q2,q3;
always@(posedge clk)
begin
q3 = ((~q1)&(~q2))^q3;
q2 = (~q1)^q2;
q1 = 1^q1;
end
endmodule
````
## Output:
### Truth Table:
#### Up Counter:
![292232607-b94207e2-8bd7-46eb-adbd-9099c856823c](https://github.com/Hafeezuldeen/Exp-7-Synchornous-counters-/assets/144979314/4c0d7e64-63b8-470f-a5fd-6fd98807cbee)
#### Down Counter:
![292233455-5de2a377-f527-4dd1-9bf5-4a3c1cd286bc](https://github.com/Hafeezuldeen/Exp-7-Synchornous-counters-/assets/144979314/85fc4456-147c-483b-af07-c9fc684dc021)

### RTL logic for up and down counter:
#### Up Counter:
![upcounter](https://github.com/RoopakCS/Exp-7-Synchornous-counters-/assets/139228922/b9ae1e13-4049-4a47-a3d6-87c4d4987ac3)
#### Down Counter:
![downcounter](https://github.com/RoopakCS/Exp-7-Synchornous-counters-/assets/139228922/4997a05f-96af-460c-809c-674ff3b09a93)


### Timing diagrams for up and down counter:  
#### Up Counter:
![WhatsApp Image 2023-12-27 at 14 02 12_13c00fad](https://github.com/RoopakCS/Exp-7-Synchornous-counters-/assets/139228922/e82482c1-b02c-486d-9364-12010173ea06)
#### Down Counter:
![WhatsApp Image 2023-12-27 at 14 04 54_104af7c7](https://github.com/RoopakCS/Exp-7-Synchornous-counters-/assets/139228922/9c716603-67f0-48f7-88ab-27d5a7c9707e)








## Result:
Thus synchornous counters up counter and down counter circuit are studied and the truth table for different logic gates are verified.

