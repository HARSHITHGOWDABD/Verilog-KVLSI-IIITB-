
```
module clock ;
  real frequency =100;
  real clk;
  real duty =50;
  real timeperiod,ton ;
  
  initial begin 
    clk=0;
    timeperiod =(1000/frequency);
    ton= (duty*timeperiod)/(100);
    
    #100 $finish;
  end
   always 
    begin
    #(timeperiod-ton) clk=1;
    #ton clk=0;
    end 
endmodule
```
  
   
 ```
module clk_always;
reg clk = 0;

always #5 clk = ~clk; // Toggle every 5 time units
endmodule
```
```
module clk_forever;
reg clk = 0;

initial begin
forever begin
#5 clk = ~clk;
end
end
endmodule
```
```
module clk_while;
reg clk = 0;
integer count = 0;

initial begin
while (count < 10) begin
#5 clk = ~clk;
count = count + 1;
end
end
endmodule
```
```
module clk_for;
reg clk = 0;
integer i;

initial begin
for (i = 0; i < 10; i = i + 1) begin
#5 clk = ~clk;
end
end
endmodule
```
```
module clk_xor;
reg clk = 0;

initial begin
repeat (10) begin
#5 clk = clk ^ 1; // XOR toggle
end
end
endmodule
```
```
module clk_task;
reg clk = 0;

task automatic generate_clk;
input integer delay;
begin
forever #delay clk = ~clk;
end
endtask

initial begin
generate_clk(5);
end
endmodule
```
```
module clk_two_blocks;
reg clk = 0;

always #5 clk = 1;
always #10 clk = 0;
endmodule
```
