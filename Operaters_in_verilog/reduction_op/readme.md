# REDUTION OPERATION 
```
1.Reduction operators are unery operators.
2.Reduction operators perform bitwise opearion on a single vector.
3.Reduction
```
 # CODE 
 ```
 module reduction_operators;
  reg [3:0] a = 4'b1101;
  reg result;

  initial begin
    result = &a;
    $display("The operation using &: &%b = %b", a, result);
    result = |a;
    $display("The operation using |: |%b = %b", a, result);
    result = ^a;
    $display("The operation using ^: ^%b = %b", a, result);
    result = ~&a;
    $display("The operation using ~&: ~&%b = %b", a, result);
    result = ~|a;
    $display("The operation using ~|: ~|%b = %b", a, result);
    result = ~^a;
    $display("The operation using ~^: ~^%b = %b", a, result);
  end
endmodule
```
# OUTPUT 
```
The operation using &: &1101 = 0
The operation using |: |1101 = 1
The operation using ^: ^1101 = 1
The operation using ~&: ~&1101 = 1
The operation using ~|: ~|1101 = 0
The operation using ~^: ~^1101 = 0
```
