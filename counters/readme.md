 MOD 16 UPCOUNTER 
 ```
module counter(clk , count , rest);
  input clk,rest;
  output reg [3:0]count;
  reg [3:0]counti;
   
  always @( posedge clk)
    if (rest)
      counti<=4'b0000;
    else 
      counti<= counti+1;
  
  count =counti ;
  
endmodule
```
MOD 16 DOWNCOUNTER 
```
module counter_up_3bit(clk,rst,count);
  input clk,rst;
  output [2:0] count;
  reg [2:0] temp;
  
  always@(posedge clk)
    begin
      if(rst)
        temp<=0;
      else
        temp<=temp-1;
    end
  
  assign count = temp;
  
endmodule
```
# UP DOWN COUNTER 
```
module up_down( clk,reset,ctrl,count);
  input clk,reset,ctrl;
  output [3:0]count ;
  reg[3:0]tempcount ;
  
  always @(posedge clk)
    begin 
      if(reset) 
        tempcount<=4'b0000;
      else
        
        if(ctrl)
          tempcount<=tempcount+1;
       else
          tempcount<=tempcount-1;
      end 
      
      assign count=tempcount;
      
    
endmodule

```
# MOD 47 UPCOUNTER 
```
module mod47_up(count, clk,rset);
  input clk,rset;
  output [7:0]count ;
  
  reg[7:0]tempcount;
  
  always @(posedge clk)
    begin 
      if(! rset  | tempcount<=8'd46)
          tempcount<=8'b0;
      else 
         tempcount <= tempcount +1;
         end
      assign count= tempcount ;
 
endmodule
```
# MOD 10 _40_ UP COUNTER 
```
module mod10_to_40_up(count, clk,rset);
  input clk,rset;
  output [7:0]count ;
  
  reg[7:0]tempcount;
  
  always @(posedge clk)
    begin 
      if(! rset  | tempcount>=8'd40 | tempcount <8'd10)
          tempcount<=8'd40;
      else 
         tempcount <= tempcount +1;
         end
      assign count= tempcount ;
 
endmodule
```
# counter_10_to_40_up_down
```
module counter_10_to_40_up_down(count, u_d,load,clk,rst,data);
  input [7:0]data;
  input clk,rst,load,u_d;
  output [7:0] count;
  
  reg [7:0] count_temp;
  
  always @(posedge clk)
    begin
    if(! rst | count_temp>8'd40 | count_temp<8'd10)
          count_temp <=8'd10;
  else if(load)
          count_temp<=data;
  else if(u_d)
    count_temp <= (count_temp>=40)?8'd10:count_temp+1;
  else
    count_temp <= (count_temp<=8'd10)?8'd40:count_temp-1;
  
    end
  assign count= count_temp;
  
endmodule
```
