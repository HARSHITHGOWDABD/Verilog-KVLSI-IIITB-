# BITWISE OPERATOR 
```
module bitwise_operators;
  reg [3:0] a = 4'b1100, b = 4'b1010;
  reg [3:0] result;

  initial begin
    result = a & b;
    $display("The operation using &: %b & %b = %b", a, b, result);
    result = a | b;
    $display("The operation using |: %b | %b = %b", a, b, result);
    result = a ^ b;
    $display("The operation using ^: %b ^ %b = %b", a, b, result);
    result = ~a;
    $display("The operation using ~: ~%b = %b", a, result);
  end
endmodule
```
# NOTE 
```
The main difference between unary and binary operators is:

🔹 Unary operator → works on 1 operand
🔹 Binary operator → works on 2 operands
```
# OUTPUT 
```
The operation using &: 1100 & 1010 = 1000
The operation using |: 1100 | 1010 = 1110
The operation using ^: 1100 ^ 1010 = 0110
The operation using ~: ~1100 = 0011
```
