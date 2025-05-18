# FULLADDER BY USING BEHAVIORAL MODELLING 
```
module fulladder(s, cout, a, b, cin);  
  input a, b, cin; 
  output reg s, cout; 
 
  always@(a,b,cin) begin 
   s=a^b^cin; 
   cout=(a&b)|(a&cin)|(b&cin); 
  end 
 
 endmodule
```
# TESTBENCH
```
module full_adder_bh;  
  reg a, b, cin; 
  wire s,cout; 
 
  fulladder dut(s,cout,a,b,cin); 
 
  initial begin
    for (integer i=0;i<=2**3;i++)
        begin
           {cin,b,a}=i;
          #2;
        end
  end


  initial begin
    $monitor("time=%0d , a=%b , b=%b , cin=%b , s=%b , cout=%b",$time,a,b,cin,s,cout); 
  end 
 
 endmodule
```
# OUTPUT 
```
time=0 , a=0 , b=0 , cin=0 , s=0 , cout=0
time=2 , a=1 , b=0 , cin=0 , s=1 , cout=0
time=4 , a=0 , b=1 , cin=0 , s=1 , cout=0
time=6 , a=1 , b=1 , cin=0 , s=0 , cout=1
time=8 , a=0 , b=0 , cin=1 , s=1 , cout=0
time=10 , a=1 , b=0 , cin=1 , s=0 , cout=1
time=12 , a=0 , b=1 , cin=1 , s=0 , cout=1
time=14 , a=1 , b=1 , cin=1 , s=1 , cout=1
time=16 , a=0 , b=0 , cin=0 , s=0 , cout=0
```
