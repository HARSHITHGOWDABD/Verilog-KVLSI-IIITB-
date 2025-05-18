# CODE
```
module halfadder(s, cout, a, b);  
  input a, b; 
  output reg s, cout; 
 
  always@(a,b) 
    begin 
   s=a^b; 
    cout=(a&b); 
  end 
 
 endmodule
```
# NOTE
```
1.In bhavioral modelling for design output is declared as reg but in test bench input as reg
```
# TESTBENCH
```
module full_adder_bh;  
  reg a, b, cin; 
  wire s,cout; 
 
  halfaddder dut(s,cout,a,b); 
 
  initial begin
    for (integer i=0;i<2**2;i++)
        begin
           {b,a}=i;
          #2;
        end
  end


  initial begin
    $monitor("time=%0d , a=%b , b=%b  , s=%b , cout=%b",$time,a,b,s,cout); 
  end 
 
 endmodule
```
# OUTPUT
```
time=0 , a=0 , b=0  , s=0 , cout=0
time=2 , a=1 , b=0  , s=1 , cout=0
time=4 , a=0 , b=1  , s=1 , cout=0
time=6 , a=1 , b=1  , s=0 , cout=1
```
