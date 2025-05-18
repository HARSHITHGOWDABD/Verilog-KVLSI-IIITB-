# CODE 
```
module full_adder_st(s, cout, a, b, cin);  
  input a, b, cin; 
  output s, cout; 
 
  wire n1,n2,n3; 
 
  xor xor1(s,a,b,cin); 
  and and1(n1,a,b); 
  and and2(n2,a,cin); 
  and and3(n3,b,cin); 
  or or1(cout,n1,n2,n3); 
 
 endmodule
```
## TESTBENCH 
```
 module full_adder_bh;  
  reg a, b, cin; 
  wire s,cout; 
 
  full_adder_st fa_dut(s,cout,a,b,cin); 
 
  initial begin 
    $monitor("time=%0t a=%b,b=%b,cin=%b, s=%b ,cout=%b",$time,a,b,cin,s,cout); 
   a=0; 
   b=0; 
   cin=0;  //{cin,a,b}=3'b000 
   #10 a=1; //{cin,a,b}=3'b010 
   #10 b=1; //{cin,a,b}=3'b011 
   #10 cin=1; //{cin,a,b}=3'b111 
   #10 $stop; 
  end // initial 
 
 endmodule
```
### OUTPUT 
```
time=0 a=0,b=0,cin=0, s=0 ,cout=0
time=10 a=1,b=0,cin=0, s=1 ,cout=0
time=20 a=1,b=1,cin=0, s=0 ,cout=1
time=30 a=1,b=1,cin=1, s=1 ,cout=1
```
