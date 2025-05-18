# HALF ADDER
```
module half_adder (
    input A, B,
    output Sum, Carry
);
    assign Sum = A ^ B;
    assign Carry = A & B;
endmodule
```
#  FULL ADDER BY USING HALF IN STRUCTURAL MODELLING 
```
module full_adder (
    input A, B, Cin,
    output Sum, Carry
);

    wire sum1, carry1, carry2;

    // First Half Adder
    half_adder HA1 (
        .A(A),
        .B(B),
        .Sum(sum1),
        .Carry(carry1)
    );

    // Second Half Adder
    half_adder HA2 (
        .A(sum1),
        .B(Cin),
        .Sum(Sum),
        .Carry(carry2)
    );

    // Final Carry
    assign Carry = carry1 | carry2;

endmodule
```
# OUTPUT
```
A B Cin | Sum Carry
0 0  0  |  0    0
0 1  0  |  1    0
1 0  0  |  1    0
1 1  0  |  0    1
0 0  1  |  1    0
0 1  1  |  0    1
1 0  1  |  0    1
1 1  1  |  1    1
```
