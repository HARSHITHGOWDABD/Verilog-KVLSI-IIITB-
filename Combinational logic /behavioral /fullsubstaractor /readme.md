# CODE IN BEHAVIORAL
```
module full_sub(diff,brrow , a, b, cin);  
  input a, b, cin; 
  output reg diff, brrow; 
 
  always@(a,b,cin) begin 
   diff=a^b^cin; 
   brrow=(a&b)|(a&cin)|(b&cin); 
  end 
 
 endmodule
```
# TEST BENCH
```
module full_substractor;  
  reg a, b, cin; 
  wire diff, brrow; 
 
  full_sub dut(diff,brrow , a, b, cin); 
 
  initial begin 
   $monitor("time=%0d ,a=%b , b=%b , cin=%b ,s=%b , cout=%b",$time,a,b,cin,diff,brrow); 
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
# OUTPUT 
```
![image](https://github.com/user-attachments/assets/59cbbd70-07ff-4f1f-9dd6-692ed26ad518)
