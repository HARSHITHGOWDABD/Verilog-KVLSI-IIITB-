# CONCATINATION OPERATION 
```
Syntax =={ op1,op2,op3}
```
# CODE
```
module concatenation_operator;
  reg [3:0] a = 4'b1100, b = 4'b1010;
  reg [7:0] result;

  initial begin
    result = {a, b};
    $display("The operation using {}: {%b, %b} = %b", a, b, result);
  end
endmodule
```
# OUTPUT 
```
The operation using {}: {1100, 1010} = 11001010
```
