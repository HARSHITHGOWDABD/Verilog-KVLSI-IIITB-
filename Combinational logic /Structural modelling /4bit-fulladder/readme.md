# 4 BIT ADDER FULL ADDER
```
// Code your design here
 module full_adder_bh(s, cout, a, b, cin);  
  input a, b, cin; 
  output reg s, cout; 
 
  always@(a,b,cin) begin 
   s=a^b^cin; 
   cout=(a&b)|(a&cin)|(b&cin); 
  end 
 
 endmodule 

 module full_adder_4bit_st(s,cout,a,b,cin);  
  input [3:0]a, b; 
  input cin; 
  output [3:0]s; 
  output cout; 
 
  wire n1,n2,n3; 
 
  full_adder_bh fa1(s[0],n1,a[0],b[0],cin); 
  full_adder_bh fa2(s[1],n2,a[1],b[1],n1); 
  full_adder_bh fa3(s[2],n3,a[2],b[2],n2); 
  full_adder_bh fa4(s[3],cout,a[3],b[3],n3); 
 endmodule
```
# NOTE
```
1. See the working of the repeat loop
```
# TESTBENCH
```
// Code your testbench here
// or browse Examples
 module full_adder_4bit_bh_tb; 
  reg [3:0]a, b; 
  reg cin; 
  wire [3:0]s; 
  wire cout; 
 
 full_adder_4bit_st dut(s,cout,a,b,cin); 
 
 initial 
   $monitor("time=%0d , a=%b , b=%b , cin=%b , s=%b  cout=%b",$time,a,b,cin,s,cout); 
 
 initial begin 
  a=0; 
  b=0; 
  cin=0; 
   repeat(1) begin 
   #10 a=a+1; 
     repeat(2) begin 
    #10 b=b+1; 
       repeat(2) 
      #10 cin=~cin; 
   end // repeat(16) 
  end // repeat(16) 
 end 
 
 
 endmodule
```
# OUTPUT 
```
time=0 , a=0000 , b=0000 , cin=0 , s=0000  cout=0
time=10 , a=0001 , b=0000 , cin=0 , s=0001  cout=0
time=20 , a=0001 , b=0001 , cin=0 , s=0010  cout=0
time=30 , a=0001 , b=0001 , cin=1 , s=0011  cout=0
time=40 , a=0001 , b=0001 , cin=0 , s=0010  cout=0
time=50 , a=0001 , b=0010 , cin=0 , s=0011  cout=0
time=60 , a=0001 , b=0010 , cin=1 , s=0100  cout=0
time=70 , a=0001 , b=0010 , cin=0 , s=0011  cout=0
```
