# FULL ADDER USING DATAFLOW 
```
module halfadder(s, cout, a, b);  
  input a, b; 
  output s, cout; 
 
  assign s=a^b; 
  assign cout=(a&b); 
 
 endmodule
```
## NOTE
```
1.assign statement is used in dataflow modelling for continious asssignment
```
### TESTBENCH
```
module full_adder_bh;  
  reg a, b; 
  wire s,cout; 
 
  halfadder fa_dut(s,cout,a,b); 
 
  initial begin 
    $monitor("time=%0d , a=%b , b=%b, s=%b, cout=%b",$time,a,b,s,cout); 
   a=0; 
   b=0; 
   
   #10 a=1; 
   #10 b=1; 
     
   #10 $stop; 
  end 
 
 endmodule
```
### OUTPUT
```
time=0 , a=0 , b=0, s=0, cout=0
time=10 , a=1 , b=0, s=1, cout=0
time=20 , a=1 , b=1, s=0, cout=1
```
