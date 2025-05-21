# REPLICATION OPERATOR
```
1.Replication  operators can accept any number of operands .
2.Replication operator are used to replicate an operand specified number of times .
Syntax == {replicate_times{operand}};
```
# CODE 
```
module replication_operator;
  reg [1:0] a = 2'b10;
  reg [5:0] result;

  initial begin
    result = {3{a}};
    $display("The operation using {{}}: {3{%b}} = %b", a, result);
  end
endmodule
```
# OUTPUT 
```
The operation using {{}}: {3{10}} = 101010
```
