# HALF ADDER USING STRUCTURAL MODELLING 
```
// Code your design here
//half adder by using structural modelling 
module halfadder(a,b,sum,carry);
  input a,b;
  output sum,carry ;
  and s(carry,a,b);
  xor c(sum,a,b);
  
endmodule
```
## TESTBENCH
```
module test;
    reg a,b;        // input in behav reg
    wire sum,carry; //output in wire
  
  halfadder dut(a,b,sum,carry);
  
     initial begin
         a=1'b0; b=1'b0;
         #10 a=1'b0; b=1'b1;
         #10 a=1'b1; b=1'b0;
         #10 a=1'b1; b=1'b1;
      end
 initial begin 
$monitor("simtime=%0t,a=%0b,b=%0b,sum=%0b,carry=%0b",$time,a,b,sum,carry);
 end

endmodule
```
### NOTE
```
1.$monitor will print whenever the values inside the paranthesis 
```
#### OUTPUT
```
module test;
    reg a,b;        // input in behav reg
    wire sum,carry; //output in wire
  
  halfadder dut(a,b,sum,carry);
  
     initial begin
         a=1'b0; b=1'b0;
         #10 a=1'b0; b=1'b1;
         #10 a=1'b1; b=1'b0;
         #10 a=1'b1; b=1'b1;
      end
 initial begin 
$monitor("simtime=%0t,a=%0b,b=%0b,sum=%0b,carry=%0b",$time,a,b,sum,carry);
 end

endmodule
```
