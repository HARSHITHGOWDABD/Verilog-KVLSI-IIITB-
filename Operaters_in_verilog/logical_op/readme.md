# LOGICAL OPERATORS
```
! -----> Converts non zero value to zero and zero to non zero.(logic not)
&& ----> If both the operands are one returns one (logic and)
|| ----> If any one of the operand is one returns 1(logic or)
```
# NOTE 
```
1. It returns a single bit 1, 0,x;
2.If the operand is non zero it is treated as 1.
3.If the operand is zero it is equlal to logic zero .
4.If the operand is neither zero nor one it is equalent to 1, simulator is treated as false
```
# CODE 
```
module logical_operators;
  reg a = 1, b = 0;
  reg result;

  initial begin
    $display("Logic not=%b ",!a);
    $display("Logic and=%b ",a && b);
    $display("Logic or =%b", a||b);
    
      end
endmodule
```
# OUTPUT
```
Logic not=0 
Logic and=0 
Logic or =1
```
