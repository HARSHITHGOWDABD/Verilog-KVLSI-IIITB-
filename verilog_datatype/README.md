# code 
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
