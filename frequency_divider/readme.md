# FREQUENCY DIVIDE BY 2 
```
module freq_div_by_2 (clk_out, clk, rst);
  input clk, rst;
  output reg clk_out;
  
  always @(posedge clk)
    if(rst)
       clk_out <=0;
  else 
       clk_out<=~clk_out;
endmodule
```
# For divide by 4 circuit you need to add the two always block thats the change 
```
```
# Frequency divide by 3 Circuit 
```
module div_3( 
   input clk, 
    input reset, 
     output clk_out); 
reg[1:0] pos_cnt; 
reg [1:0]neg_cnt; 
      always@(posedge clk) 
    if(reset) 
pos_cnt<= 0; 
else if(pos_cnt==2) 
pos_cnt<= 0; 
else 
pos_cnt<= pos_cnt+1; 
always@(negedge clk) 
if(reset) 
neg_cnt<= 0; 
else if(neg_cnt==2) 
neg_cnt<= 0; 
else neg_cnt<= neg_cnt+1; 
assign clk_out=((pos_cnt==2) | (neg_cnt==2)); 
endmodule
```
  
