# CODE 
```
module cla_4bit_dataflow (A,B,Cin,Sum,Cout);
  input [3:0] A, B;
  input Cin;
  output [3:0] Sum;
  output Cout;


  wire [3:0] G, P;
  wire C1, C2, C3;

  // Generate and Propagate signals of first full adder 
  assign G[0] = A[0] & B[0];       // carry
  assign G[1] = A[1] & B[1];
  assign G[2] = A[2] & B[2];
  assign G[3] = A[3] & B[3];

  assign P[0] = A[0] ^ B[0];       //sum
  assign P[1] = A[1] ^ B[1];
  assign P[2] = A[2] ^ B[2];
  assign P[3] = A[3] ^ B[3];

  // Carry equations
  assign C1 = G[0] | (P[0] & Cin);
  assign C2 = G[1] | (P[1] & G[0]) | (P[1] & P[0] & Cin);
  assign C3 = G[2] | (P[2] & G[1]) | (P[2] & P[1] & G[0]) | (P[2] & P[1] & P[0] & Cin);
  assign Cout = G[3] | (P[3] & G[2]) | (P[3] & P[2] & G[1]) |
                (P[3] & P[2] & P[1] & G[0]) |
                (P[3] & P[2] & P[1] & P[0] & Cin);

  // Sum bits
  assign Sum[0] = P[0] ^ Cin;
  assign Sum[1] = P[1] ^ C1;
  assign Sum[2] = P[2] ^ C2;
  assign Sum[3] = P[3] ^ C3;

endmodule
```
# TESTBENCH
```
module test ;
  reg  [3:0] A, B;
  reg Cin;
  wire [3:0] Sum;
  wire Cout;
  
  cla_4bit_dataflow dut(A,B,Cin,Sum,Cout);
 
  initial begin 
    for (integer i=0; i<2**8;i++)
      begin
        {Cin,B,A}=i;
        #2;
      end
  end
  
  initial begin
    
    $monitor("simtime=%0d,A=%b,B=%b,Cin=%b ,Sum=%b,cout=%d",$time,A,B,Cin,Sum,Cout);
  end
  
endmodule
  ```
# NOTE 
