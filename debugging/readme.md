---------------------Verilog Debugging Questions By Shashi Kant----------------------------

What is the output of these program. 
```
Q1. module test;

	reg [7:0] a;
	initial 
	begin
		a= -8'd1;
		$display("A= %0d", a);
	end
   endmodule
```
```
Q2. module test;
	reg[2:0] i;

	initial begin
	for (i=0; i<8; i=i+1)
	$display("I= %0d", i);
	end
endmodule
```
```
Q3. module test;
	integer i,j,count=0;

	initial begin
	for (i=0; i<10; i=i+1)
		for(j=0; j<i; j=j+1)
		count= count+1;  
	$display("Count=%0d", count);
	end
    endmodule
```
```
Q4. module test;

	initial begin
	  	 #5 $display($time, "Thread A");
		fork
			#4 $display($time, "Thread B");
			#1 $display($time, "Thread C");
			begin
			#2 $display($time, "Thread D");
			#5 $display($time, "Thread E");
			end
			$display($time, "Thread F");
		join
	end
   endmodule


Q5. module test;

	initial fork
	   	#5 $display($time, "Thread A");
		begin
			#4 $display($time, "Thread B");
			#1 $display($time, "Thread C");
			fork
			#2 $display($time, "Thread D");
			#5 $display($time, "Thread E");
			join
			$display($time, "Thread F");
		end
	join
   endmodule


Q6.  module test;

	initial fork
	   	#5 $display($time, "Thread A");
		begin
			#4 $display($time, "Thread B");
			#1 $display($time, "Thread C");
			fork
			#2 $display($time, "Thread D");
				fork
				#5 $display($time, "Thread E");
				#2 $display($time, "Thread F");
				join
			#1 $display($time, "Thread G");
			join
			$display($time, "Thread H");
		end
	       $display($time, "Thread I"); 
	join
   endmodule

Q7  module test;

	integer a=0;
	always@(a)
	begin
	a= a+1;
	$display("A %0d",a);
	end
    endmodule

Q8. module test;

	integer a=0;
	always@(a)
	begin
	a<= a+1;
	$display("A %0d",a);
	end
    endmodule
	    

Q9. module test;

	integer a=0;
	always@(a)
	begin
	a<= a+1;
	$display("A %0d",a);
	end
    endmodule


Q10. module test;

	integer a=0;
	always@(a)
	begin
	a<= a+1;
	$display("A %0d",a);
	#1;
	end
    endmodule

Q11.module test;

	integer a=0;
	always@(a)
	begin
	a= a+1;
	$display("A %0d",a);
	#1;
	end
    endmodule

Q12. module test;
	integer a,b,c,d;
	initial begin
		#2 a<= #1 3; 
		#1 b= #4 5; 
		#5 c= #2 b+a;
		#2 d<= #3 10;	
		   d= #5 a+b;
	end
	initial begin
		$monitor("Sim time= %0t, A= %0d, b=%0d, c=%0d, d= %0d", $time,a,b,c,d);
	end
    endmodule


Q13. module test;
	integer a;
	
	initial 
	begin
	a<=1;
	$display("@@@@ a= %0d",a);
	$strobe("### a= %0d",a);
	a=2; 	
	end
   endmodule


Q14. module test;
	integer a=1, b=2, c=3, d=4;

	initial begin
	$strobe("a=%0d,b= %0d, c= %0d, d= %0d", a,b,c,d);
	  b= a;
	  c= b;
          d= c;
	  a= d;
	end
    endmodule

Q15. module test;
	integer a=1, b=2, c=3, d=4;

	initial begin
	$strobe("a=%0d,b= %0d, c= %0d, d= %0d", a,b,c,d);
	  b<= a;
	  c<= b;
          d<= c;
	  a<= d;
	end
    endmodule
  		
Q15. module test;
	reg[3:0] sel;

	initial begin
		sel= 4'b0000;	
		#3 sel= 4'b?000;
		#4 sel= 4'b000?;
	end
	
	initial 
		begin
		casez(sel)
		4'b000?: $display("First");
		4'b?000: $display("Second");
		default: $display("Third");
	end
	endmodule

Q16. module test;
	reg[3:0] sel;

	initial begin
		sel= 4'b0000;	
		#3 sel= 4'b?000;
		#4 sel= 4'b000?;
	end
	
	initial 
		begin
		case(sel)
		4'b000?: $display("First");
		4'b?000: $display("Second");
		default: $display("Third");
	end
	endmodule
