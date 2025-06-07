VHDL vs VERILOG 
1.VHDL is a typed language and it is very difficult to understand
2.verilog is similar to c programing, c is a procedural/sequential  and verilog is concurrent programming language.
3.Test bench is used to generate the stimuli 
4.for every design we will write in IP and VIP 
5.It is used for simulation and synthesis 
6.we can write the code without fabrication technology
7.Introduced by Gorden Bell and Alen Newell
8.Design flow diagram 
9.First implimentd by prabugoyal , phil moorby by gatway automation later become cadence -1995
10.In dut the first step is module and declaration of input and output ports
11. eloberate the design by using diffrent modelling style
12.In test bech the module is without ports and input as reg and out as wire (behavioral modelling)
13.Instanciate the dut and then stimuky geneation , capture and then publish the result 
14.It is case sencitive and extencition is .v
15.gate , structural , dataflow (rtl), behavioral , switch level of modelling
16.comments (//) for multiple (/*),
17.Rules of Identifier ,all keywords are in lower case,
18.negative number is represented by 2's compliment form only
19.default number is decimal and size is 32 bit .
20.variable name =size'base value 
21.blank space is filled by only 0,x,z.
22.0x is an hexadecimal format .
23.all the datatype in verilog has 4 states except real.
24. ? is an alternative symbol for z in verilog,but in some of the condition it is dontcare .
25.x and z are case insencitive 
26. net type is used to connect multiple data default size is 1 and value is z.
27. In net type signal must be driven continiously , suitable for combinational circuit 
28. In vetror representation the size must be mentiond before variable name 
 
 ---->DIFFRENCE BETWEEN THE WIRE AND REG 
 1.Default value is z and reg is X
 2.wire needs continious driving
 3.reg is used to hold the value wire will simply supply
 4.reg will be written inside the procedural blocks 
 5.wire and reg by default they are unsigned .(integer is signed )
 6.If we want to make it signed then signed keyword can be used befor the size  of 32 bit 
 7.multidriver condition is supported by wire 


---> ALWAYS AND INITIAL ARE THE PROCEDURAL BLOCKS 

30. Order must be same always from higher to lower or lower to higher in vector
31. integer is also a type of reg datatype
32. it is 32 bit and signed and default value is x . Equal to reg signed [31:0]a;
33. ---> WE cannot mention the size to an integer.Because by default the size is fixed
34. ---->all inputs are wire and output are of reg in dut
35. Real is a type of register data type used to store real values
36. ---> default value is 0 and
37. time and realtime are 64 bit datatype used to show the simulation results.
38. time will give the time in integer where as realtime will provide the fraction values also
39. $time is a system function used to show current simulation time.

ARRAYS 
40. Used to store same type of data 
41. In vectors the data will be stored in the form of row 
42. In arrays size is defined after the array name 
43. In array each row of size 32 bit and it can be of reg ,integer, string (arrays forms column )
-----> vector should always be of reg type
int a[10] --> compact declaration 
int a[1:0] --->verbose declaration 
45. array accesing declaration is same as array declaration with compact

STRINGS
46.There is no ready made string datatype in verilog 
47.String is a arrray of character and each charactes need 8 bit to represent it 
48.We need to use the reg datatype to for the string 
49.In verilog we need to declare the memory first 
50.Syntax is similar to the vector 
51.If we decalare the size is more than the required then the blank space will be created at msb side 
52.If the size is less than the required then lsb bits are given higher preiority msb bits are truncated 

FUNDAMENTAL BLOCK OF VERILOG 
53.Module is a basic building block of verilog 
54.By default the datatype of the input is wire always 
55.For output it can be reg or wire 
56.while writing the port if they are of same size no need to declare seperately 
57.vector representation for mux and other type of representation

58.Input always be a wire type , output is reg or wire

Parameter 
1.It is used to define the parameter in the code 
2.Syntax Parameter variable_name = value
3.Parameter can be chaned by using the defparam used in testbench (it will overite the value )
4.It can be binary , real, integer or string 

Level of abstraction in verilog 
1. Structural (by using gates ) we will use the primitives here
2. dataflow (assign )
3. structural (instatiation )
4. behavioral (higher level of constracts )

Structural modelling 
1. Majorly there are three types of primitives in a)logic b)inverter/buff c)tristate inv/buff
2. Logic primitive and ,or ,xor,xnor,nand , nor (they have only one input and multiple output
3. syntax will be logic(output , in1,in2,in3)
4. In  inveter/ buffer --1)Buf and 2) not here [it as one input and multiple output]
5. the syntax is inv(op1,op2,op3,in)
6. Tristate inveter,buffer --bufif0  -- active high control buffer 
7. .                      --bufif1  -- active low control buffer 
8. .                      --notif0  -- active low control inverter 
9. .                      --notif1  -- active high control inverter
10.  syntax is primitive name instance name (outputs, inputs, control)

----In gate level and dataflow  , structural the output is of the wire type only
----In Behaviorl output is of the reg type 
59.# is used to provide the delay 
30.Steps in the test bench 
 a)write a module without port 
 b)input as reg and output as wire 
 c)Dut instantiation (Port mapping may be position or named )
 d)stimuly generation 
 e)Capture the monitor input and output within procedural block
 f)For waveform with in the initial block $dumpfile ("dump.vcd") and $dumpvars("0,a,b,c) zero is the level of hirachy 

1) 2:1 mux using  structural modelling
2) 2:4 decoder
3) 4:2 encoder
4) 3 bit parity generator

Dataflow modelling 
1.Impliment by using some operators
2.Assign key word will be used 
----in dataflow the target must be of wire (net)type 
 3.How asign works initially evaluation of rhs will be done and then updation to lhs will be done 
4.RHS could be of net or reg or function 
5.if single wire is assigned with two diffrent operation is called multidriver condition
6.It is only when the target is of wire type (it will produce x)
7.If there is delay there is no problem

codes 
a)3 bit binary to gray code converter 
b)prime number detectator 
c)3 bit pallendrode detector 
d)BCD to excess 3 code converter 
----> in behavioral asignment the target must (LHS) be of the reg type only 

OPERATERS 
1.Arithmetic operator is a binary operator 
2.If any of the opearatiod is real or x or z it will be x and real
3.In tb there are many 
4.Logic operator
5.Shift operator( op1 should to unsigned in logical shift ans signed in arithmetic shift )
6.Concatination opeartion
7. In arithmetic opearation a/b if b is zero the result will be x
8.Ternary operator is called ternary because it has three operands condition , true , false 
9.Reduction operator writtens only one value 
10.Logical equal and case equal is very important == and ===
11.Equality operator equality , inequality ,case equality ,case inequality (case refers to 3 symbols)
12.Bitwise operand returns the size of largest operand
13.diffrence between the & and && &(bit wise means bitwise operation returs the largest bit of the operands ) &&(logical operands first decides if it is zero or non zero then it will give only one bit output ) Reduction operand also written only one bit .

STRUCTURAL MODELLING STYLE 
How to delcare the parameter module #(parameter =4) (a,b,sum,cout)

46. Initial block is non synthesizable always used in testbench , always block is synthesizable and execute in the looping fashion
47. The code inside the always and sequential in nature
48. Sencitivity list is the list of variables means inputs and @ (holds the simulation till the changes occurs inside the sencitivity
      list )
    BEHAVIORAL MODELLING 
49.Behavioral can be used  for cobinational and sequential circuit
50.In combinatioal circuit include all the inputs in the sencitivity list and use the blocking statements
51.Inputs must be of wire and output must be reg
52.= blocking statement <= non blocking statement
53.more number of memory will be created in the non blocking , because the sequential circuits needs to be shedule for a while and then ex
54.Behavioral modelling is majorly used in the sequential circuit
55.Lathes are more or less it is a sequential circuit
56. In flip flop we are only bother about the edges
57. If i am making syncronous flip flop use the posedge only in sencitivity list
58. If it is asynconous use resset also in the sencitivity list
59. Output cannont be given as a input becouse they are uni directional
60. So under this condition take that as a reg variable and later assign it
61. In test becnh there are 5 major task
62. a) declaring all i/o b)connecting dut with test bench c)Generate a stimuly d)drive the stimuli e) capture the responce
63. Simulation refers just verifiying our design
64. Compilation ----> Checks the synthatical errors
65. Simulation  ----> Checks logical equilance
66. Synthesis   ----> Convering to netlist
67. What ever the statements starts with the $ symbol it is called system task
68. In behavioral modelling we are using higher level constructs like while , for , function , task
69. As the code inside the procedural blocks will execute in the sequential manner
70. We can have multiple procedural blocks in the code and every one starts from 0 simulation time
71. Target must be reg type in behavioral
72. nesting of procedural blocks are not allowed
73. Procedural blocks are exegute continiouslay untill we block the exegution (# , @, wait )
74. # provides the delay , @ holds untill the change in the sencitivity list , wait waits for the signal
75. Assignment statement inside the procedural block in BLOCKING = , and NON BLOCKING <=.
76. Till now we have 3 assignment a) continious assignmnt for dataflow b)blocking for combinational c)non blocking for sequential
77. Initial block only used in testbench bcz to initilize the values (it is non synthesizable)
78. Initial block exegutes in zero simuation time
79. In pracitcall simulator does not work concurrentely it works sequntially
80. Initial block rums only one time
81. --> in program we have both the initial and always block then initial runs first then always
82. When ever we want to combine multiple statement we use begin and end
83. Combinatiol leades to blocking and non blocking for sequential
84. Begin end means the sequential exegution
85. Modelling of flip flop should be by using higher lelvel constructs (if else and case ..)
  ----------->PROCEDURAL BLOCKS ARE INITIAL AND ALWAYS AND FUNCTION AND TASK 
  ----------->PROCEDURAL ASSIGNMENT ARE BLOCKING AND NON BLOCKING 

87. ALWAYS BLOCK
88. It can be use for both dut and test bench
89. Always block executes at multiple times that depends on the sencitivity list
90. When we dont write the sencitivity list the always block will exwcute for infinate time
91. In the same code we have both always and initial in this case initial will execute first

DIFFRECNE BETWEEN THE INITIAL AND ALWAYS BLOCK 
1. initial non synthesizable , always may be synthezible(provoided codeing guidelines are followed)
2. initial runs one time , always runs frequently depending upon the sensitivity list 
3. Multiple times we can use and always execute in 0 simulation time
4. Mostly used in testbench (initial) always used in the dut
5. Logically the both the reset and clk should be either the edge or the level

   # write a verilog code the initial block works as a always block and always as a initial block
   Hint : ineed to make initial block as continious

   CLOCK GENERATION
   1.If we remove the sencitivity list this always block becomes infinate loop
   2. always  #1 clk =~clk 50% duty cycle with the time period of 2
   3. real keyword is used in the defining the frequency

   FUNCTIONS  AND TASK IN VERILOG
   1.Funtion and task are subroutine which makes code more readable 
   2.Function is used in DUT , Task is used testbench
   3.Function can be synthesizable , Task cannot be synthesizable
   4.Function reurns only one value , Task doesnot return any value
   5.Function and task are the procedural statements , when ever we want to include multiple value we can you begin and end are used
  ----> STATIC : when we write a module and initilize the memory will be created it is called as static
   6.And by default the module is static in nature shars the memory
   7.So if i call the function number of times the value will be written in the same memory
   8.To avoid this the Automatic will be used it will involes the memory for every call.( we need to add the automatic with the fucnction      and task )
   9.Class is dynamic in nature so to allocate the memory to the object we neeed to use the new keyword, untill we use the new the memory       will not be created .
   10.Static means the sharing the memory
   11.AUtomatic every invocation new memory will be created .
   12.The purpose of function and task is to incerease the readibility
   13.Defination of Module and task must be inside the module then
    a)if it is inside the module it is called that it is local to module
    b)if it is outside the module to is called as global .
   14. Function can accept any number of inputs and returns only one output
   15. Task doesnot return any value  but it will calculate multiple values
   16. Task may contaion delay and other time consuming elements, where function doesnot 

   FUNCTION
   1. Function start with the function keyword and ends with endfunction
   2. Function always returns the single value
   3. They cannot have input and output ports  but task has
   4. Function must have one input argument
   5. Delay event , timing control is not allowed
   6. Function exegutes at zero simulation time
   7. when we declare a function with the same name the register will be created
   8. Function cannot have trigger
   9. Function can be invoked(called ) by function name .
   10. Function can be called inside the function
   11.----> We cannot call task inside the function
   12. Function can invokes other function but task cant
   13. Return type of all inputs are i bit by default
   14. -----> Only blocking sequential statemnts are allowed in function bcz the function always exegute in the avtive region .
   15. We cannot use the non blocking statements in the function
   16. Function and task have an access to the outside the scope (should be written inside the module )
   17. -----inputs are always be  a wire in function , output can be reg or wire 

  -----> POINTS 
  1.functction is a procedural block 
2.It synthesizable 
3.all delay and timing constrainds are not be use 
4.It will accepts multiple inputs and written only one output 
5.we can call function inside the task , but we can call function inside the function 
6.Function eritten the output of 1 bit reg .
7.Function should written inside the module 
8.Function have an acces to the global varible 
9.Function use only blocking statement and eegute in the activeregion 
10. Function must have one input argument

### Points to be remember while writing the code 
1.It fallows the behavioral type of modelling 
2.inputs must be wire and output must be of wire type 
3.Inside the finction dont mention the output arguments 
4.While calling the function use the variable declare in the module 

TASK 
1. It starts with the keyword task and ends with endtask
2. Non synthesizable
3. In function only input ports are are declared and output through the function name
4. But in  task we can pass multiple values through the input and output ports
5. Function required atlest one arguments function name( arg) ,But in task there is no arguments task ()
6. Delay and all timing controls are allowed in task
7. Function cannot call task but task can call function
8. function                 |  task 
       task (not allowed )  |     function (allowed)

9.It doesnt not written anything
10.It doesent required any written type  in task 
11. -----> The arguments are called with the same order what they are declared 
12.Task can be disabled by using disable keyword 
13.Both blocking and non blocking are allowed in task 
14.Based on the useage the task can be executed in  the diffrent region 
15.Function and task have an acceibility to the signals written inside the module 

Function and task diffrence 
1. synthesizable non 
2. Requires atlest one input argiment , non required 
3. exegutes in the active regin , depends 
4. Function will return a value , task doesnt 
5. output arguents not allowed in function , input output inout are allowed 
6. Function should requires atleast one input arguments , task desnot 
7. only blocking statemnts are allowed in function , non also allowed in task
8. Timing constarins are not allowed , here it is allowed 
9. Order of accesing shold be same as declaed in the task
10. function exegutes at zero simulation time 

   AUTOMATIC
1.Automatic function will create the memory for the each invocation
2.This concept is used in reccursive function and task
3.Function calling itself best example is factorial of a number
4.fact(n)  ====n*fact(n-1)
 SYNTAX
 function automatic returntype function_name( inputs --)
   begin
   ----
  -----   // defination (logic)
  end 
  endfunction 
5.Automatic function crates the static memory 
6.Automatic function invokes the new set of memory every time this function is invokes  
7.Factorial of a number by using the static function will not give the required result. Automatic will overcome this problem 
8.It will come into picture when ever we are using the reccursive function 

DELAYS IN VERILOG 
1.delays spicify the time in which the assigned value propogate through the nets 
2.Delay and timing control are not synthesizable 
3.REFER THE PPT 
4.In inter assignment delay the both the blocking and non blocking have the same value 
5.In intra assignment delay the blocking and non blocking have diffrent behaviour 
6.In inter assignment  the delay will be exeguted first and then statement will be exeguted
7.In intra statement will be evaluated first and then then delay will be exeguted 
8.Intra and non blocking behaves as an actual hardware 
9.HINT ----while calculating the delay use the memory 

ORDER OF EXEGUTION IN VERILOG 
1.Preponed region- initilization 
2.Active region -- conditional statemts , blocking statement exegution , $display and $write , rhs updation of non blocking assignment 
3.Inactive region -- #0 delay will be exeguted 
4.NBA region --- updation of non blocking 
5.Postponed region --$strobe and $monitor 

SYSTEM TASK IN VERILOG 
1.It will starts with $ symbol
2.By this we can 
     a)Display and monitor the inputs and outputs 
     b)Control of simulation
     c)Timing checks 
3.All system tasks are non synthesizable 
4.System task must be used inside the procedural block 

THERE ARE FOUR DISPLAY TASK 
a) $display  exegution in -----> active region  ---- has new line char --- prints only one time 
b) $write                 -----> active region  ---- no new line char  --- prints only one time 
c) $monitor               -----> postponed region  ---has new line char -- prints whenever the changes occer 
d) $strobe                -----> postponed region ----has new line char -- prints only once 

5.We can write the multiple monitor inside the code but only the last moniter will going to active
6.We can  control the monitor by $monitor on and $ monitor off
7.If two statements are in the active region then preority will be give to which one is first 

SIMULATION CONTROL TASK 
Majory 3 are there 
  1)Terminate / end -------->$finish
  2)Suspend (pause ) ------->$stop
  3)resheddule / reset ------>$reset

1. $finish(0) ----> do not return anything , just terminate the exegution
2. $finish(1) ----> prints at what time the suspention encounter 
3. $finish(2) ----> gives complete information , about the memory and at this simulation time it has suspend etc

CONTINIOUS ASSIGNMENT 
1. continoius assignment should be written outside the procedural block
2. Active all the time
3. Suppors multidriving condition
4. Multi driving condition is alloed in the wire only (at same time you are driving the value )
5. It will print x ( if y=0 and y=1)

Procidural assignments 
1. It is  called procedural assignemt because we are writing inside the procedural blocks
2. a)Blocking                                      b) Non blocking
3.Exegutes in active region           | RHS eveluation in active region and updation in the NBA region 
   and blocks further statements      | and allows the further statements to exegute 
4.Used for combnational circuit       | It is for sequential circuit modelling 
  modelllig
5.Some times it has race condition    |Removes the race condition
6.Solve the problems on regions
7.
                                  
  


  
  

   
   
   
   
   

    

    

   



