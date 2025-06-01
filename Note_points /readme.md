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
 6.If we want to make it signed then signed keyword can be used befor the size 


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
45. array accesing declaration is same as array devalration with compact

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

