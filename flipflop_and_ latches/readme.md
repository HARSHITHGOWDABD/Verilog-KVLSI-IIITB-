# D FLIP FLOP WITH ASYNCRONOUS RESET (choose active low or high)
```
module dflip(d,clk,rst,q);
  input d,clk,rst;
  output reg q;
  
  always @(posedge clk or posedge rst)
    begin
    if (rst)
      q<=0;
   else 
     q<=d;
    end 
endmodule

```
```
module test;
  reg clk,rst,d;
  wire q;
  
  dflip dut(d,clk,rst,q);
  
  initial begin
    clk=0;
    rst=1;
    #10 rst=0;
    d=0;
    #10 d=1;
    #10 d=0;
    #10 d=1;
    #50 $finish;
  end
  
  initial begin
    $monitor("sim time=%0t, d=%0b, q=%0b",$time,d,q);
  end
  
  always #5 clk=~clk;
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,test);
  end
  
endmodule
```
# D FLIP FLOP WITH SYNCRONOUS RESET 
```
module dflip(d,clk,rst,q);
  input d,clk,rst;
  output reg q;
  
  always @(posedge clk )
    begin
    if (rst)
      q<=0;
   else 
     q<=d;
    end 
endmodule
```
```
module test;
  reg clk,rst,d;
  wire q;
  
  dflip dut(d,clk,rst,q);
  
  initial begin
    clk=0;
    rst=1;
    #10 rst=0;
    d=0;
    #10 d=1;
    #10 d=0;
    #10 d=1;
    #50 $finish;
  end
  
  initial begin
    $monitor("sim time=%0t, d=%0b, q=%0b",$time,d,q);
  end
  
  always #5 clk=~clk;
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,test);
  end
  
endmodule
```
# D latch with asynconous reset 
```
module dflip(d,clk,rst,q);
  input d,clk,rst;
  output reg q;
  
  always @(d,clk,rst )
    begin
    if (rst)
      q<=0;
      if(clk)
     q<=d;
    end 
endmodule
```
```
module test;
  reg clk,rst,d;
  wire q;
  
  dflip dut(d,clk,rst,q);
  
  initial begin
    clk=0;
    rst=1;
    #10 rst=0;
    d=0;
    #10 d=1;
    #10 d=0;
    #10 d=1;
    #50 $finish;
  end
  
  initial begin
    $monitor("sim time=%0t, d=%0b, q=%0b",$time,d,q);
  end
  
  always #5 clk=~clk;
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,test);
  end
  
endmodule
```
# D latch with syncronous reset 
```
module dflip(d,clk,rst,q);
  input d,clk,rst;
  output reg q;
  
  always @(d,clk,rst )
    begin
      if (clk)
      if(rst)
     q<=0;
      
      else 
        q<=d;
    end 
endmodule
```
```
module test;
  reg clk,rst,d;
  wire q;
  
  dflip dut(d,clk,rst,q);
  
  initial begin
    clk=0;
    rst=1;
    #10 rst=0;
    d=0;
    #10 d=1;
    #10 d=0;
    #10 d=1;
    #50 $finish;
  end
  
  initial begin
    $monitor("sim time=%0t, d=%0b, q=%0b",$time,d,q);
  end
  
  always #5 clk=~clk;
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,test);
  end
  
endmodule
```
# JK _ FLIP FLOP WITH ASYNCONOUES RESET [*]
```
module  jk_ff_async(j,k,clk,rst,q);
  input j,k,clk,rst;
  output reg q;
  reg temp;
   
  always @(posedge clk or posedge  rst)
    begin 
      if(rst)
        temp<=0;
      
      else begin
        if(j==0 && k==0)
           temp<=temp;
      else 
        if(j==0 && k==1)
             temp<=0;
          
       else 
         if(j==1 && k==0)
           temp<=1;
          
       else 
         if(j==1 && k==1)
          temp<=~temp;
     
    end 

   q<=temp;
    end
  
  
endmodule
```
```
module tb;
  reg j,k,clk,rst;
  wire q;
  
  jk_ff_async dut(j,k,clk,rst,q);
  
  initial begin
    clk=0;
    rst=1;
    #1 rst=0;
    j=0; k=0;
    #10 j=0; k=1;
    #10 j=1; k=0;
    #10 j=1; k=1;
    
    #50 $finish;
  end
  
  always #5 clk=~clk;
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,tb);
  end
  
endmodule

```
# JK Flipflop with syncronous 
```
module  jk_ff_syn(j,k,clk,rst,q);
  input j,k,clk,rst;
  output reg q;
  reg temp;
   
  always @(posedge clk )
    begin 
      if(rst)
        temp<=0;
      
      else begin
        if(j==0 && k==0)
           temp<=temp;
      else 
        if(j==0 && k==1)
             temp<=0;
          
       else 
         if(j==1 && k==0)
           temp<=1;
          
       else 
         if(j==1 && k==1)
          temp<=~temp;
     
    end 

   q<=temp;
    end
  
  
endmodule
```
# JK Latch with syncrnous reset 
```
module jk_latch_async(j,k,clk,rst,q);
  input j,k,clk,rst;
  output q;
  reg temp;
  
  assign q = temp;
  
  always@(j,k,rst,clk) begin
    if(clk)
      if(rst)
        temp<=0;
    
      else
        if(j==0 & k==0)
          temp<=temp;
        else if(j==0 & k==1)
          temp<=0;
        else if(j==1 & k==0)
          temp<=1; 
        else
          temp<=~temp;
    
    else
      temp<=temp;
    
  end
  
endmodule
```
# T flip flop with asyncronous reset 
```
module tff_async(t,clk,rst,q);
  input clk,rst,t;
  output reg q;
  reg temp;
  
  always@(posedge clk or posedge rst)
    begin
      if(rst)
        temp<=0;
      
      else
          if(t)
            temp<=~temp;
          else
            temp<=temp;
      
      q<=temp;       
     
    end
  
endmodule
      

module test;
  reg clk,rst,t;
  wire q;
  
  tff_async dut(t,clk,rst,q);
  
  initial begin
    clk=0;
    rst=1;
    #10 rst=0;
    t=0;
    #5 t=1;
    #5 t=0;
    rst=1;
    #6 rst=0;
    #5 t=1;
    #5 t=0;
    #50 $finish;
  end
  
  initial begin
    $monitor("sim time=%0t, t=%0b, q=%0b",$time,t,q);
  end
  
  always #5 clk=~clk;

  initial begin
    $dumpfile("dump.vcd");
    $dumpvars(1,test);
  end
  
endmodule
```
T flip flop with syncronous reset 
```
module tff_sync(t,clk,rst,q);
  input clk,rst,t;
  output reg q;
  reg temp;
  
  always@(posedge clk or posedge rst)
    begin
      if(rst)
        temp<=0;
      
      else
          if(t)
            temp<=~temp;
          else
            temp<=temp;
      
      q<=temp;       
     
    end
  
endmodule
```
 # T latch with asynronous 
 ```
module tlatch(t,clk,rst,q);
  input clk,rst,t;
  output reg q;
  reg temp;
  
  always@(clk,rst,t)
    begin
      if(rst)
        temp<=0;
      
      else
        if(clk)
          if(t)
            temp<=~temp;
          else
            temp<=temp;
      
      q<=temp;       
     
    end
  
endmodule

```
# T latch with syncronous reset 
```
module tlatch(t,clk,rst,q);
  input clk,rst,t;
  output reg q;
  reg temp;
  
  always@(clk,rst,t)
    begin
      if(clk)
        if(rst)
          temp<=0;
        else
          if(t)
            temp<=~temp;
          else
            temp<=temp;
      
      q<=temp;       
     
    end
  
endmodule
```
    

