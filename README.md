# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

![Screenshot 2025-05-06 094114](https://github.com/user-attachments/assets/2fa2ae84-f2a2-458a-b93b-1a7457b390a9)

**PROGRAM**
```
module ripple (
input clk,    
input reset,   
output [3:0] q 
);
// Internal signals for flip-flops
reg [3:0] q_int;


assign q = q_int;

always @(posedge clk or posedge reset) begin
    if (reset) 
        q_int[0] <= 1'b0; 
    else 
        q_int[0] <= ~q_int[0];
end


genvar i;
generate
    for (i = 1; i < 4; i = i + 1) begin : ripple
        always @(posedge q_int[i-1] or posedge reset) begin
            if (reset) 
                q_int[i] <= 1'b0; 
            else 
                q_int[i] <= ~q_int[i]; 
        end
    end
endgenerate
endmodule
```

 Developed by:GOKUL S RegisterNumber:212224230075
*/

**RTL LOGIC FOR 4 Bit Ripple Counter**

![image](https://github.com/user-attachments/assets/de0ba021-81ef-4544-859e-82e87e66539c)


**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![image](https://github.com/user-attachments/assets/59261d50-6ed6-43fa-812e-a7da92881bff)


**RESULTS**

Implementation of 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables
