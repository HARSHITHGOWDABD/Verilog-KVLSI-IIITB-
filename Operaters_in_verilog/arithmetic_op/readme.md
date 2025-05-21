# ARITHMETIC OPERATOR 
```
+ -----> addtion between two operands.
- -----> substraction between to oerands.
* -----> multiplication between two operands .
/------>division between two operands.
** ----> exponent.
% ----->modulus operator gives remainder.
```
# CODE
```
module arithematic_operator ;
  reg[3:0]op1,op2;  // input must be reg type
  initial begin 
    op1=2'b11; 
    op2=2'b10;
    $display("Addition operation  =%b", op1+op2);
    $display("Substraction operation  =%b", op1-op2);
    $display("Multiplication operation  =%b", op1*op2);
    $display("Division  operation  =%b", op1/op2);
    $display("Exponent operation  =%b", op1**op2);
    $display("Modulus operation  =%b", op1%op2);
  end 
  
endmodule
```
# OUTPUT
```
Addition operation  =0101
Substraction operation  =0001
Multiplication operation  =0110
Division  operation  =0001
Exponent operation  =1001
Modulus operation  =0001
```

# NOTE 
```
1. IF ANY VALUE IS X OR Z THE RESULT WILL BE X.
2.IF SECOND OPERAND IS DIVISION OR MODULUS IS ZERO , THEN RESULT WILL BE X.
3.SECOND OPERAND EXPONENT IS ZERO THE RESULT WILL BE ONE.
IF THE EITHER OF THE OPERAND IS REAL THE RESULT IS ALSO REAL.
```
 

