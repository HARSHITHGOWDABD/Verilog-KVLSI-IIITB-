# SISO
```
module siso_shift_register (
    input clk,         // Clock input
    input reset,       // Synchronous reset
    input serial_in,   // Serial data input
    output serial_out  // Serial data output
);

    reg [3:0] shift_reg;

    // Shift logic
    always @(posedge clk) begin
        if (reset)
            shift_reg <= 4'b0000;                   // Clear the register on reset
        else
          shift_reg <= { serial_in,shift_reg[3:1]}; // Shift MSB and input new bit  Right shift
    end

  assign serial_out = shift_reg[0]; // Output the LSB (or MSB if left shift)

endmodule


//Testbench

`timescale 1ns / 1ps

module siso_shift_register_tb;

    reg clk;
    reg reset;
    reg serial_in;
    wire serial_out;

    // Instantiate the DUT (Design Under Test)
    siso_shift_register uut (
        .clk(clk),
        .reset(reset),
        .serial_in(serial_in),
        .serial_out(serial_out)
    );

    // Clock generation: 10ns period
    always #5 clk = ~clk;

    initial begin
        // Initialize inputs
        clk = 0;
        reset = 1;
        serial_in = 0;

        // Hold reset for a few cycles
        #10;
        reset = 0;

        // Apply serial input bits: 1, 0, 1, 1
        serial_in = 1; #10;
        serial_in = 0; #10;
        serial_in = 1; #10;
        serial_in = 1; #10;

        // Continue shifting with 0s to observe output
        serial_in = 0; #40;

        // Finish simulation
        $finish;
    end

    // Monitor signals
    initial begin
        $monitor("Time=%0t | Reset=%b | Serial In=%b | Serial Out=%b | Shift Reg=%b",
                  $time, reset, serial_in, serial_out, uut.shift_reg);
    end
  
    initial begin
      $dumpfile("dump.vcd");
      $dumpvars(1,siso_shift_register_tb);
    end

endmodule
```
# SIPO
```
module sipo_shift_register (
    input clk,         // Clock input
    input reset,       // Synchronous reset
    input serial_in,   // Serial data input
    output [3:0] parallel_out // Parallel data output
);

    reg [3:0] shift_reg;

    // Shift logic
    always @(posedge clk) begin
        if (reset)
            shift_reg <= 4'b0000;                   // Clear the register on reset
        else
            shift_reg <= {shift_reg[2:0], serial_in}; // Shift left, load serial_in
    end

    assign parallel_out = shift_reg; // Output entire register content

endmodule



//Testbench
`timescale 1ns / 1ps

module sipo_shift_register_tb;

    reg clk;
    reg reset;
    reg serial_in;
    wire [3:0] parallel_out;

    // Instantiate the DUT
    sipo_shift_register uut (
        .clk(clk),
        .reset(reset),
        .serial_in(serial_in),
        .parallel_out(parallel_out)
    );

    // Generate clock: 10ns period
    always #5 clk = ~clk;

    initial begin
        // Initial values
        clk = 0;
        reset = 1;
        serial_in = 0;

        // Reset for a short duration
        #10;
        reset = 0;

        // Input sequence: 1, 0, 1, 1
        serial_in = 1; #10;
        serial_in = 0; #10;
        serial_in = 1; #10;
        serial_in = 1; #10;

        // Hold serial_in low and continue clocking
        serial_in = 0; #20;

        $finish;
    end

    // Monitor outputs
    initial begin
        $monitor("Time=%0t | Reset=%b | Serial In=%b | Parallel Out=%b",
                  $time, reset, serial_in, parallel_out);
    end
  
    initial begin
      $dumpfile("dump.vcd");
      $dumpvars(1 ,sipo_shift_register_tb);
    end

endmodule
```
# PISO 
```
module piso_shift_register (
    input clk,               // Clock input
    input reset,             // Synchronous reset
    input load,              // Load control signal
    input [3:0] parallel_in, // Parallel data input
    output serial_out        // Serial data output
);

    reg [3:0] shift_reg;

    always @(posedge clk) begin
        if (reset)
            shift_reg <= 4'b0000;                  // Clear the register
        else if (load)
            shift_reg <= parallel_in;              // Load parallel input into register
        else
            shift_reg <= {1'b0, shift_reg[3:1]};   // Shift right
    end

    assign serial_out = shift_reg[0]; // LSB shifted out first

endmodule


//Testbench

`timescale 1ns / 1ps

module piso_shift_register_tb;

    reg clk;
    reg reset;
    reg load;
    reg [3:0] parallel_in;
    wire serial_out;

    // Instantiate DUT
    piso_shift_register uut (
        .clk(clk),
        .reset(reset),
        .load(load),
        .parallel_in(parallel_in),
        .serial_out(serial_out)
    );

    // Clock generation (10ns period)
    always #5 clk = ~clk;

    initial begin
        // Initialize inputs
        clk = 0;
        reset = 1;
        load = 0;
        parallel_in = 4'b0000;

        #10;
        reset = 0;

        // Load parallel data (e.g., 4'b1011)
        parallel_in = 4'b1011;
        load = 1; #10;
        load = 0;

        // Observe serial output over 4 clock cycles
        #40;

        $finish;
    end

    // Monitor signals
    initial begin
        $monitor("Time=%0t | Reset=%b | Load=%b | Parallel In=%b | Serial Out=%b",
                  $time, reset, load, parallel_in, serial_out);
    end
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,piso_shift_register_tb);
  end

endmodule
```
# PIPO 
```
module pipo_register (
    input clk,
    input reset,              // Synchronous reset
    input load,               // Load control
    input [3:0] parallel_in,  // Parallel input
    output reg [3:0] parallel_out // Parallel output
);

    always @(posedge clk) begin
        if (reset)
            parallel_out <= 4'b0000;         // Clear output on reset
        else if (load)
            parallel_out <= parallel_in;     // Load data when load is high
    end

endmodule


//Testbench


`timescale 1ns / 1ps

module pipo_register_tb;

    reg clk;
    reg reset;
    reg load;
    reg [3:0] parallel_in;
    wire [3:0] parallel_out;

    // Instantiate DUT
    pipo_register uut (
        .clk(clk),
        .reset(reset),
        .load(load),
        .parallel_in(parallel_in),
        .parallel_out(parallel_out)
    );

    // Clock generation (10ns period)
    always #5 clk = ~clk;

    initial begin
        clk = 0;
        reset = 1;
        load = 0;
        parallel_in = 4'b0000;

        // Hold reset
        #10; reset = 0;

        // Load 1101
        parallel_in = 4'b1101; load = 1; #10;
        load = 0;

        // No load, change input (ignored)
        parallel_in = 4'b0011; #10;

        // Reset the output
        reset = 1; #10; reset = 0;

        // Load new value
        parallel_in = 4'b1010; load = 1; #10;

        $finish;
    end

    // Monitor signals
    initial begin
        $monitor("Time=%0t | Reset=%b | Load=%b | Parallel In=%b | Parallel Out=%b",
                  $time, reset, load, parallel_in, parallel_out);
    end
  
    initial begin
      $dumpfile("dump.vcd");
      $dumpvars(1,pipo_register_tb);
    end

endmodule
```
# UNIVERSAL SHIFT REGISTER 
```
module USR(PO,PI,sel,clk,rst,SI); 
 input [1:0] sel; 
 input [4:0] PI; 
 input  clk, rst,SI; 
 output reg[4:0] PO;  
  
  
 always@(posedge clk) 
 if (rst)  
  PO <= 5'd0; 
 else begin case(sel) 
  
   2'b00 : PO <= PO; 
   2'b01 : PO <= {PO[3:0],SI}; 
   2'b10 : PO <= {SI,PO[4:1]}; 
   2'b11 : PO <= PI;   
   default : PO <= 0; 
  
  endcase 
  end 
 assign SO = (sel == 2'b01) ? PO[4] : PO[0] ; 
 
  
endmodule
```
