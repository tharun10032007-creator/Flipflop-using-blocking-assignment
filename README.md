# EXPERIMENT 3: Simulation of All Flip-Flops using Blocking Statement

## AIM
To design and simulate basic flip-flops (SR, D, JK, and T) using **blocking statements** in Verilog HDL, and verify their functionality through simulation in Vivado 2023.1.

## APPARATUS REQUIRED
- Vivado 2023.1
- Computer with HDL Simulator

## DESCRIPTION
Flip-flops are the basic memory elements in sequential circuits.  
In this experiment, different types of flip-flops (SR, D, JK, T) are modeled using **behavioral modeling** with **blocking assignment (`=`)** inside the `always` block.  
Blocking assignments execute sequentially in the given order, which makes it easier to describe simple synchronous circuits.

## PROCEDURE
1. Open **Vivado 2023.1**.  
2. Create a **New RTL Project** (e.g., `FlipFlop_Simulation`).  
3. Add Verilog source files for each flip-flop (SR, D, JK, T).  
4. Add a testbench file to verify all flip-flops.  
5. Run **Behavioral Simulation**.  
6. Observe waveforms of inputs and outputs for each flip-flop.  
7. Verify that outputs match the truth table.  
8. Save results and capture simulation screenshots.

---

## VERILOG CODE

### SR Flip-Flop (Blocking)
```verilog
module sr_ff (
    input wire S, R, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### SR Flip-Flop Test bench 
```
module sr_ff (input clk,input S,input R,output reg Q);
always @(posedge clk)
 begin
    case ({S,R})
      2'b00: Q <= Q;    
      2'b01: Q <= 0;    
      2'b10: Q <= 1;    
      2'b11: Q <= 1'bx; 
 endcase
 end
endmodule
```
#### SIMULATION OUTPUT
  
  ![WhatsApp Image 2025-09-17 at 13 31 56_18d1a24a](https://github.com/user-attachments/assets/ee156742-1d97-4d91-adc2-5998e77f31ea)


### JK Flip-Flop (Blocking)
```verilog
module jk_ff (
    input wire J, K, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### JK Flip-Flop Test bench 


module JK_FF_tb;

reg J;
reg K;
reg clk;
reg rst;
wire Q;


JK_FF uut (
    .J(J),
    .K(K),
    .clk(clk),
    .rst(rst),
    .Q(Q)
);


always #5 clk = ~clk;

initial begin
  
    clk = 0;
    rst = 1;
    J = 0;
    K = 0;


    #10 rst = 0;

    
    #10 J = 0; K = 0;

   
    #10 J = 0; K = 1;

  
    #10 J = 1; K = 0;

    
    #10 J = 1; K = 1;

   
    #10 J = 0; K = 1;

   
    #10 J = 1; K = 1;

    
    #10 rst = 1;
    #10 rst = 0;

   
    #10 J = 1; K = 0;

    #20 $finish;
end

endmodule

```
#### SIMULATION OUTPUT

![WhatsApp Image 2025-09-17 at 13 46 27_9f18addf](https://github.com/user-attachments/assets/6629add4-3a62-446f-bf0e-de4d3338d640)

### D Flip-Flop (Blocking)
```verilog
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### D Flip-Flop Test bench 
```
module dFlipFlop_tb;
reg clk_t,rst_t,d_t;
wire dout_t;
dFlipFlop dut (.clk(clk_t),.rst(rst_t),.d(d_t),.dout(dout_t));
initial
begin
    d_t = 1'b0;
    clk_t = 1'b0;
    rst_t = 1'b1;
    #20
    rst_t = 0;
    d_t = 1'b0;
    #20
    d_t = 1'b1;
end
always
    #20 
    clk_t = ~clk_t;
endmodule
```

#### SIMULATION OUTPUT

![WhatsApp Image 2025-09-17 at 11 19 47_0e41bb35](https://github.com/user-attachments/assets/e14e19e8-f4d7-4421-887b-907075fe1c9f)

### T Flip-Flop (Blocking)
```verilog
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### T Flip-Flop Test bench
```
module T_FF (
    input wire T,
    input wire clk,
    input wire rst,
    output reg Q
);

always @(posedge clk or posedge rst) begin
    if (rst)
        Q <= 0;
    else if (T)
        Q <= ~Q;
    else
        Q <= Q;
end

endmodule
```
#### SIMULATION OUTPUT

![WhatsApp Image 2025-09-17 at 11 34 58_e6e5f797](https://github.com/user-attachments/assets/6abaf00b-cdae-46cd-8f43-d2787ab23abd)

### RESULT

All flip-flops (SR, D, JK, T) were successfully simulated using blocking statements in Verilog HDL.
The outputs matched the expected truth table values, demonstrating correct sequential behavior.
