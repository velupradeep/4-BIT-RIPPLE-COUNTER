# NAME:PRADEEP V
# REG NO:212223240119
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

1. Increment count on each positive edge of the clock.
2. Reset count to zero when it reaches 15.
3. Generate clock signal (clk).
4. Instantiate the RippleCounter module.
5. Conduct functional testing by displaying the count at each clock cycle for 16 cycles.

**PROGRAM**

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by:PRADEEP V
  RegisterNumber:212223240119
*/

```

module RippleCounter(
   input wire clk,  // Clock input
   output reg [3:0] count // 4-bit counter output
);

// Counter logic
always @(posedge clk) begin
   if (count == 4'b1111) // Reset when count reaches 15
       count <= 4'b0000;
   else
       count <= count + 1; // Increment count
end

endmodule

// Testbench
module RippleCounter_tb;

// Inputs
reg clk;

// Outputs
wire [3:0] count;

// Instantiate the counter
RippleCounter uut(
   .clk(clk),
   .count(count)
);

// Clock generation
initial begin
   clk = 0;
   forever #5 clk = ~clk; // Toggle clock every 5 time units
end

// Stimulus
initial begin
   // Wait for a few clock cycles
   #10;
   
   // Display header
   $display("Time | Count");
   $display("-----------------");
   
   // Functional table testing
   // Increment count 16 times and display the count
   repeat (16) begin
       #5; // Wait for one clock cycle
       $display("%4d | %b", $time, count);
   end
   
   // End simulation
   $finish;
end

endmodule




```

**RTL LOGIC FOR 4 Bit Ripple Counter**
![330489871-a0d3aa3d-b3b0-4ce0-89bb-bfa1a8abde7c](https://github.com/velupradeep/4-BIT-RIPPLE-COUNTER/assets/150329341/c238e087-5ee9-4fa3-8e8c-43f0b3f4c305)



**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
![330489946-a285f70c-c317-4f6e-be38-eef9ecfa250d](https://github.com/velupradeep/4-BIT-RIPPLE-COUNTER/assets/150329341/f1af004b-9cf9-43fc-ba0c-3ddbc2f7fdb0)


**RESULTS**
Thus the program executed succesfully.

