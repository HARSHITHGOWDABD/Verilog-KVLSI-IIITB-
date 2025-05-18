# CODE
```
// Code your testbench here
// HARSHITH GOWDA B D 
module datatype_in_verilog;
  wire     a;
  reg      b;
  integer  c;
  real     d;
  time     e;
  realtime f;
  reg   [4]g;
  wire  [4]h;
     initial begin
          $display("The default value of wire is   = %0d,default size of wire is = %0d",a,$bits(a));
           $display("The default value of reg is   = %0d,default size of reg is  = %0d",b,$bits(b));
          $display("The default value of integer is   = %0d,default size of integer is = %0d",c,$bits(c));
          $display("The default value of real is   = %0f",d);
          $display("The default value of time is    = %0d,The defalut size of time is = %0d",e,$bits(e));
          $display("The default value of realtime is = %0f",f);
          $display("The default value of wire is = %0d,default size of wire is = %0d",g,$bits(g));
         $display("The default value of reg is = %0d,default size of reg is = %0d",h,$bits(h));
     end
endmodule
```
## NOTE
```
1.wand, wor , supply1, supply0 are also the type of wire datatype with same size and default values .
2.real and realtime is not used for giving input and output .
3.display is a printing statement used to print only once and also support string .
```
### OUTPUT
```
The default value of wire is       = z,default size of wire is = 1
The default value of reg is       = x,default size of reg is  = 1
The default value of integer is   = x,default size of integer is = 32
The default value of real is      = 0.000000
The default value of time is     = x,The defalut size of time is = 64
The default value of realtime is = 0.000000
The default value of wire is     = x,default size of wire is = 4
The default value of reg is      = z,default size of reg is = 4



