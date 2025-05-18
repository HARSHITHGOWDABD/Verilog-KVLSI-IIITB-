# verilog code 
```
module counter_fsm_0237(clk, rst, count);
  input clk, rst;
  output reg [2:0] count;
  reg [2:0] ps,ns;
  
  
  parameter s0 = 2'b00;
  parameter s1 = 2'b01;
  parameter s2 = 2'b10;
  parameter s3 = 2'b11;
  
  always @(posedge clk) begin
    if(rst)
      ps <= s0;
    else
      ps <= ns;
  end
  
  always @(ps) begin
    case(ps)
      s0 : begin
        count = 3'd0;
        ns = s1;
      end
      
      s1 : begin
        count = 3'd2;
        ns = s2;
      end
      
      s2 : begin
        count = 3'd3;
        ns = s3;
      end
      
      s3 : begin
        count = 3'd7;
        ns = s0;
      end
      
      default : begin
        count = 3'd0;
        ns = s0;
      end
    endcase
    
  end
endmodule
```
