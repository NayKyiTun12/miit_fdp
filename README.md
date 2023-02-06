# miit_fdp
# Day 1 Content
# Introduction to Verilog RTL Design and Senthesis
# Lab Using iverilog and gtkwave

mkdir vsd  
 cd vsd  
 git clone https://github.com/kunalg123/vsdflow.git  
 mkdir vlsi  
 cd vlsi  
 git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git  
 cd SKY130RTLDesignAndSynthesisWorkshop  
 cd my_lib  
 cd lib  
 cd ..  
 cd verilog_model  
 cd ..  
 cd ..  
 cd verilog_files  
 ![image](https://user-images.githubusercontent.com/123365842/214255981-fe709aa1-d23c-4224-8025-35e0857ba98a.png)
 
![image](https://user-images.githubusercontent.com/123365842/214256095-64fcddc9-bef1-4f9a-82e0-ab214628d091.png)

![image](https://user-images.githubusercontent.com/123365842/214256231-342d9b0f-6377-4835-b387-3b88aa930c8d.png)

![image](https://user-images.githubusercontent.com/123365842/214256462-7c8d4158-fea7-4b5e-9968-beb3db072db5.png)

![image](https://user-images.githubusercontent.com/123365842/214257929-cc6a19e4-64db-4074-b980-80e4e04a8760.png)

![image](https://user-images.githubusercontent.com/123365842/214256562-19383dbd-bc05-4842-aa1c-42340cf15d85.png)

![image](https://user-images.githubusercontent.com/123365842/214256673-5f535d64-b558-4a1f-bd95-f7a79cde2db0.png)

![image](https://user-images.githubusercontent.com/123365842/214257137-18918cf3-6e30-4297-a372-27e4a69c5c86.png)

![image](https://user-images.githubusercontent.com/123365842/214257192-9eed680d-edac-438c-8345-1ff19d67d65b.png)

![image](https://user-images.githubusercontent.com/123365842/214257249-f1f28d18-c97e-46ee-a22a-1b8d7b6a0582.png)

![image](https://user-images.githubusercontent.com/123365842/214257336-368aaf4d-4665-4bf3-ace8-535a96981071.png)

# DAY2 : TIMING LIBS, HIERARCHICAL Vs FLAT SYNTHESIS AND EFFICIENT FLOP CODING STYLES

# INTRODUCTION TO TIMING .lib

Write the command is  gvim ../my_lib/lib/SKY130_fd_sc_hd__tt_025C_1v80.lib

The following window appears that shows the library file sky130_fd_sc_hd__tt_025C_1v80.lib

!vim ../lib/SKY130_fd_sc_hd__tt_025C_1v80.lib

![image](https://user-images.githubusercontent.com/123365842/214759508-db1bbf5e-a6df-48f7-8099-4a61220bfa9d.png)

Switching off the syntax color red

  Command used : syn off

![image](https://user-images.githubusercontent.com/123365842/214759442-e1d89634-6b4e-4745-9ff5-b890de021dbd.png)

Enabling the line numbers

  Command used :se nu
  
  ![image](https://user-images.githubusercontent.com/123365842/214759602-40ce9f0f-fd92-4139-8bbb-72f06962b60e.png)
  
  ![image](https://user-images.githubusercontent.com/123365842/214759637-455a47ab-0131-4ed1-8c33-c65b8711c28e.png)
  
  ![image](https://user-images.githubusercontent.com/123365842/214759704-02ae59db-5129-42cf-a0af-af13a1ab52ba.png)
  
  ![image](https://user-images.githubusercontent.com/123365842/214759756-932b7e65-baae-454a-b69f-8af003a435f4.png)
  
  Command used - :vsp
  
  ![image](https://user-images.githubusercontent.com/123365842/214759824-4bb6f2a6-2219-46ef-ae49-a86d7bcbae7e.png)
  
  Command used -  :vs
  
  ![image](https://user-images.githubusercontent.com/123365842/214759919-6e1585a9-62f8-48b4-a73a-d9da3826f48c.png)

Command used -    !vim multiple_modules.v

![image](https://user-images.githubusercontent.com/123365842/214759999-8e8dd2c8-681f-45e0-b2ce-f3da2e164669.png)

After the command ----  synth –top multiple_modules, the following screenshot will be shown.

![image](https://user-images.githubusercontent.com/123365842/214760058-0306d223-a15c-4a9e-947f-ef8a7aa62249.png)

Command used -- abc  –liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib

![image](https://user-images.githubusercontent.com/123365842/214760179-8a8e22ce-ba2d-4b85-8eb0-2e6d16240055.png)

After the command ------ show multiple_modules, the following result will be shown.

![image](https://user-images.githubusercontent.com/123365842/214760264-51dc5139-9fdc-4558-b6ec-df77e08e24ca.png)

yosys>write_verilog –noattr  multiple_modules_hier.v

yosys>!vim multiple_modules_hier.v

![image](https://user-images.githubusercontent.com/123365842/214760354-4768484e-6a48-426c-a506-60215996bc37.png)

yosys> show

![image](https://user-images.githubusercontent.com/123365842/214760431-c9ec9451-c6ac-495f-8a71-0297717bec9d.png)

SUB MODULE LEVEL SYNTHESIS AND ITS NECESSITY

In the following example, I am going to synthesize at sub_module 1 level

yosys>synth –top sub_modules1

yosys>abc –liberty ../lib/ sky130_fd_sc_hd__tt_025C_1v80.lib

yosys>show

After above command, the following result will be shown.

![image](https://user-images.githubusercontent.com/123365842/214760571-04d9a2e8-ae25-4177-865a-a5691b429e13.png)

Glitches

Asynchronous and Synchronous Resets

In yosys terminal, type the command - !vim dff_asyncres.v –o dff_async_set.v

![image](https://user-images.githubusercontent.com/123365842/214760656-d14fabff-c91d-4204-a8f0-b422063c3723.png)

$ iverilog dff_asyncres.v tb_dff_asyncres.v

$./a.out

$gtkwave tb_dff_asyncres.vcd

![image](https://user-images.githubusercontent.com/123365842/214760724-f545f36c-cdbc-4118-a48f-8c844ba6da86.png)

  •	Q follows d only at the posedge of the clock.

  •	But as and when async_rest=1,Q becomes 0 without waiting for the next edge of the clock.

![image](https://user-images.githubusercontent.com/123365842/214760789-87229091-3aba-4227-89a8-20d00c71cfdd.png)

  •	But when async_reset goes low(1 to 0),Q doesn't become 1 immediately ,it waits for the next clock edge to follow D.
  •	Even if asunc_reset=1 and D=1, Q=0 as reset takes high precedence(that is how the code has been written,if condition of reset is checked first).

# Synthesis implementation results : asynchronous set:

![image](https://user-images.githubusercontent.com/123365842/214760906-0c13360e-f886-4133-98e3-2c4084764638.png)

# Synthesis implementation results : asynchronous reset

![image](https://user-images.githubusercontent.com/123365842/214760967-3bb0e865-fc0f-45a8-9dea-dc2a697a1791.png)

For Synchronous, Synchronous Reset and set :

![image](https://user-images.githubusercontent.com/123365842/214761017-ebcf2121-f8d0-44ac-80cf-7e84f2e24282.png)

Synthesis Results:

![image](https://user-images.githubusercontent.com/123365842/214761081-26dfa1bf-17ef-4440-aa0c-c105a00f6dd0.png)

Case wherein both both asynchronous and synchronous resets are applied together :

RTL Code:

![image](https://user-images.githubusercontent.com/123365842/214761349-1c14fec6-8cd1-4ff4-bc1f-28c5e989e801.png)

Synthesis results:

![image](https://user-images.githubusercontent.com/123365842/214761406-6f05f05d-fc24-4a06-9f1e-96fb50ca203a.png)

# Optimization

Let's Consider the following design where the 3 bit input is multiplied by 2 and the output is a 4 bit value.

RTL Code

![image](https://user-images.githubusercontent.com/123365842/214761505-742e3f57-fd17-4c54-85f0-1be4f6d86e55.png)

Synthesis Result:

![image](https://user-images.githubusercontent.com/123365842/214761551-0ba6d8b4-05b7-437c-9775-caa01a834edd.png)

Let's consider the following design where the 3 bit input is multiplied by 9 and the output is a 6 bit value.

module mult8 (input [2:0] a , output [5:0] y);
	assign y = a* 9;
endmodule

![image](https://user-images.githubusercontent.com/123365842/214765290-d0e1f62d-6aa1-4734-b21e-112214b8ff1d.png)

# DAY 3 : Combinational and Sequential Optimisations

Inorder to produce a digital circuit design which is optimised interms of area and power, the simulator performs many types of optimisations on the combinational and sequential circuits.

1.Combinational optimisation methods:

    Squezzing the logic to get the most optimised design
        -Area and Power savings
    Constant propogation
        -Direct Optimisation
    Boolean Logic Optimisation
        -K-map
        -Quine-mckluskey Algorithm

2.Sequential optimisation methods:

    Basic
        -Sequential constant Propogation
    Advanced
        State Optimisation
            -Retiming
            -Sequential Logic Cloning (Floor Plan Aware Synthesis)
	    
# Combinational Logic Optimisations

All the optimisation examples are in files opt_check.v, opt_check4.v, and multiple_modules_opt.v. All of these files are present under the verilog_files directory.

Example 1:

opt_check.v

module opt_check (input a, input b , output y);

	assign y = a?b:0;
	
endmodule

Ideally ,the above ternary operator should give us a mux. But the constant 0 propagates further in the logic .Using boolean simplification we obtain y = ab.

Synthesizing this in yosys :

Before realising the netlist, we must issue a command to yosys to perform optimisations. It removes all unused cells and wires to prduce optimised digital circuit.This can be done using the opt_clean -purge command as shown below.

![image](https://user-images.githubusercontent.com/123365842/214765869-e7a2da88-cb98-40be-8dcd-11f0557794d5.png)

Next,

 abc -liberty ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib  
 
 write_verilog -noattr opt_check_netlist.v 
 
 show

On viewing the graphical synthesis realisation , we can see the Yosys has synthesized an AND gate as expected.

![image](https://user-images.githubusercontent.com/123365842/214766003-cf358a0d-2de7-4795-bd83-45663a6982db.png)

Example 2:

opt_check2.v

module opt_check2 (input a, input b , output y);

	assign y = a?1:b;
	
endmodule

After simplification,we expect the output y to be an OR gate, since the output of the mux can be simplified to y = a + b. If we generate the netlist and look at its graphical representation , we get

![image](https://user-images.githubusercontent.com/123365842/214766541-1bfe8c87-dbb8-4b04-b0e0-5cecb6bec1ff.png)

![image](https://user-images.githubusercontent.com/123365842/214766600-c80570b9-0762-4af1-b5d2-4e5a7ffd86c5.png)

Example 3: opt_check3.v

module opt_check3 (input a, input b , input c , output y);

	assign y = a?(c?b:0):0;
	
endmodule

For the RTL verilog code of opt_check3.v , we expect the output to be a 3 input AND gate based on constant propagation and boolean logic optimisation.The output y can be simplified to y = abc.

![image](https://user-images.githubusercontent.com/123365842/214766668-8a8b85aa-b2f8-4065-b967-1a205577b775.png)

Next we generate the netlist and observe its graphical representation after synthesis

![image](https://user-images.githubusercontent.com/123365842/214766701-2faa8e0a-8cbb-4ca6-946a-67d37e96a97c.png)

Example 4:opt_check4.v

module opt_check4 (input a, input b , input c , output y);

	assign y = a?(b?(a & c):c):(!c);
	
endmodule

![image](https://user-images.githubusercontent.com/123365842/214766766-3f4ea177-37fb-404f-ac6c-41bf6be508a1.png)


In this case,the boolean logic optimisation simplifies the output to a single xnor gate i.e. y = a xnor c. Next we generate the netlist and observe its graphical representation after synthesis

![image](https://user-images.githubusercontent.com/123365842/214766785-b593f268-f5b9-482f-92b7-66e3105cf7e0.png)

Example 5:multiple_module_opt.v

module sub_module1(input a , input b , output y);

	assign y = a & b;
	
endmodule

module sub_module2(input a , input b , output y);

	assign y = a^b;
	
endmodule

module multiple_module_opt(input a , input b , input c , input d , output y);

wire n1, n2, n3;


sub_module1 U1 (.a(a), .b(1'b1), .y(n1));

sub_module2 U2 (.a(n1), .b(1'b0), .y(n2));

sub_module2 U3 (.a(b),  .b(d), .y(n3));

assign y =c | (b & n1);

endmodule

![image](https://user-images.githubusercontent.com/123365842/214766931-4fa18c5f-60e4-4d25-b702-51766e948ea1.png)

While synthesizing this in yosys we use flatten before opt_clean -purge. The multiple_module_opt instantiates both submodule1 and 2. We must use Flat Synthesis here otherwise the optimisations will not be performed on the sub module level.

![image](https://user-images.githubusercontent.com/123365842/214767017-5186ae4e-3705-4130-b579-349f44ce27c9.png)

![image](https://user-images.githubusercontent.com/123365842/214767299-03edbb15-8925-4204-9317-34f458ada457.png)

![image](https://user-images.githubusercontent.com/123365842/214767318-31609456-5f55-4587-bad8-0463a0499ede.png)


# Sequential Logic Optimisations

All the optimisation examples are in files dff_const2.v,dff_const3.v,dffconst4.v and dff_const5.v. All of these files are under the verilog_files directory.

Example 1: dff_const1.v

module dff_const1(input clk, input reset, output reg q);

always @(posedge clk, posedge reset)

begin
	if(reset)
	
		q <= 1'b0;
		
	else
	
		q <= 1'b1;
		
end

endmodule

Here, it appears that the output Q should be equal to an inverted reset or Q=!reset. However, as the reset is synchronous,even if the flop has D pinned to logic 1,when reset becomes 0, Q does not immediately goto 1. It waits untill the positive edge of the next clock cycle.

This is observed by simulating the design in verilog, and viewing the VCD with GTKWave as follows

![image](https://user-images.githubusercontent.com/123365842/214767385-f3e2ced8-b5ab-4692-b4c0-8bf22bad4211.png)

Observation : In the gtk waveform above , when reset becomes 0, Q becomes 1 at the next clock edge. Since Q can be either 1 or 0,we do not get a sequential constant, and no optimisations should be possible here. We verify it using Yosys synthesis and optimisation.

dfflibmao -liberty ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib

dfflibmap is a switch that tells the synthesizer about the library to pick sequential circuits( mainly Dff's and latches) from.

We then generate the netlist

abc -liberty ../my_lib/lib/sky130_fd_sc_hd_tt_025C_1v80.lib 

write_verilog -noattr dff_const1_netlist.v 

show

![image](https://user-images.githubusercontent.com/123365842/214768006-01cd03be-d4a6-42db-859b-ed4c7a24f491.png)


Example 2 : dff_const2.v

module dff_const2(input clk, input reset, output reg q);

always @(posedge clk, posedge reset)

begin

	if(reset)
	
		q <= 1'b1;
		
	else
	
		q <= 1'b1;
		
end

endmodule

Here, Regardless of the inputs, the output q always remains constant at 1 .

This is observed by simulating the design in verilog, and viewing the VCD with GTKWave as follows

![image](https://user-images.githubusercontent.com/123365842/214767853-c2540852-2166-4838-953e-83539eef3716.png)

Since the output is always constant ie Q=1, it can easily be optimised during synthesis.

![image](https://user-images.githubusercontent.com/123365842/214768066-d9c975c3-0f13-4d76-954c-f4f2836c2d36.png)

Example 3 : dff_const3.v

module dff_const3(input clk, input reset, output reg q);

reg q1;

always @(posedge clk, posedge reset)

begin
	if(reset)
	
	begin
	
		q <= 1'b1;
		
		q1 <= 1'b0;
		
	end
	
	else
	
	begin 
	
		q1 <= 1'b1;
		
		q <= q1;
		
	end
	
end

endmodule

When reset goes from 1 to 0,Q1 follows D at the next positive clock edge in an ideal ckt. But in reality, Q1 becomes 1 a little after the next positive clk edge(once reset has been made 0)due to Clock-to-Q delay.

Thus, q takes the value 0 until the next clock edge when it read an input of 1 from q1. This is confirmed with the simulated waveform below.

![image](https://user-images.githubusercontent.com/123365842/214768230-8044bc63-6d1f-4097-9680-915779f4b591.png)

Since Q takes both logic 0 and 1 values in different clock cycles. It is wrong to say that Q=!(reset) or Q=Q1

Hence, both the flip-flops are retained and no optimisations are performed on this design. We can confirm this using Yosys as shown below.

![image](https://user-images.githubusercontent.com/123365842/214768338-ddf0f0df-b514-4ea6-adeb-f9a3a17264c4.png)

Example 4: dff_const4.v

RTL Code:

![image](https://user-images.githubusercontent.com/123365842/214768419-7737d25e-c640-4973-9dd8-47a82cc9c056.png)

Here, regardless of the input whether reset or not , Q1 is always going to be constant i.e. Q1=1 . As q can only be 1 or q1 depending on the reset input , but q1 = 1 .Thus q is also constant at the value 1. We can confirm this with the simulated waveforms as shown below.

![image](https://user-images.githubusercontent.com/123365842/214768439-7ced8c97-0c27-41ed-b713-dd529440e5c9.png)


![image](https://user-images.githubusercontent.com/123365842/214768459-fc831127-1af6-4293-b53d-467454515b69.png)

# Day 4: Gate Level Simulations,Blocking vs Non Blocking assignments,Synthesis-Simulation Mismatch

# Introduction to Gate Level Simulations

# Synthesis Simulation Mismatches


    Missing sensitivity list
    Blocking and non blocking statements
    
# Missing sensitivity list

Simulator functions on the basis of activity that is it looks for if either of the inputs change. If there is no change in the inputs the simulator won't evaluate the output at all.

Example:

module mux(input i0, input i1, input sel, output reg y);

always @(sel)
begin
	if (sel)
	begin
		y = i1;
	end
	else
	begin
		y = i0;
	end
end
endmodule

# Blocking and non blocking statements 

    Blocking Executes the statements in the order it is written So the first statement is evaluated before the second statement
    Non Blocking Executes all the RHS when always block is entered and assigns to LHS. Parallel evaluation

# Example of Blocking assignments:

module shift_register(input clk, input reset, input d, output reg q1);
reg q0;

always @(posedge clk,posedge reset)
begin
	if(reset)
	begin
		q0 = 1'b0;
		q1 = 1'b0;
	end
	else
	begin
		q0 = d;
		q1 = q0;
	end
end
endmodule

D is assigned to Qo not which is then assigned to Q. Due to optimisation a single latch is formed where Q is equal to D.

Example of Non-Blocking assignments:

In the above RTL code if

      begin
		q0 <= d;
		q1 <= q0;
      end
      
The non blocking assignments all the RHS are evaluated and parallel assigned to lhs irrespective. So, always get a two flop shift register.

Therefore, always use non blocking statements for writing sequential circuits.

Other example:

module comblogic(input a, input b, input c, output reg y);
reg q0;

always @(*)
begin
	y = q0 & c;
	q0 = a|b;
end
endmodule

# Labs on GLS and Synthesis-Simulation Mismatch

Example 1: A mux designed with the help of ternary operator

module ternary_operator_mux (input i0 , input i1 , input sel , output y);
	assign y = sel?i1:i0;
endmodule

The synthesized netlist for the above,using yosys

Write this command "vim ternary_operator_mux.v –o bad_mux.v –o good_mux.v"

"iverlog ternary_operator_mux.v tb_ternary_operator_mux.v"

"./a.out"

"gtkwave ternary_operator_mux.v"

![image](https://user-images.githubusercontent.com/123365842/214830927-9c8d46aa-2997-498a-85dd-06ff504be32c.png)

To invoke GLS,

    We need to read our netlist file and the test bench file assosciated with it.
    We need to read 2 extra files that contain the description of verilog models in the netlist.

Write the command "iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v"

# ![image](https://user-images.githubusercontent.com/123365842/214831563-36bd2ece-05b7-4fa0-8d1b-bfff653ffd07.png)

To see the waveform of RTL simulation,the following commands is 

![image](https://user-images.githubusercontent.com/123365842/214831843-b6c38c10-b210-4539-a63d-667395b2adeb.png)

The generated netlist does behave like a 2X1 multiplexer.

Example 2:

module bad_mux (input i0 , input i1 , input sel , output reg y);
always @(sel)
begin
	if(sel)
		y <= i1;
	else
		y <= i0;
end 
endmodule

This is verified by GTKWAVE of RTL Simulation below :

Write this command "vim bad_mux.v"

"iverlog bad_mux.v tb_bad_mux.v"

"./a.out"

"gtkwave bad_mux.v"

![image](https://user-images.githubusercontent.com/123365842/214873761-489c3e5a-0c85-47cd-a9f1-5387dff794a6.png)

The design simulates a latch rather than a 2x1 mux.
But the Yosys implementation shows a 2X1 mux .

![image](https://user-images.githubusercontent.com/123365842/214874310-ae69757c-5030-49e9-9cd3-3611accf08ee.png)

Write the command "show"

![image](https://user-images.githubusercontent.com/123365842/214874710-938fb98c-87f6-4413-a25d-a626272407c8.png)

Example 3: This is an example of synthesis-simulation mismatch due to wrong order of assignment in blocking assignments.

module blocking_caveat (input a , input b , input c , output reg d);
reg x;

always @(*)
begin
	d = x & c;
	x = a | b;
end 
endmodule


Write this command "vim blocking_caveat.v"

"iverlog blocking_caveat.v tb_blocking_caveat.v"

"./a.out"

"gtkwave bad_mux.v"

![image](https://user-images.githubusercontent.com/123365842/214875258-3d5456a2-96d3-403e-ae2b-6deec9f69adb.png)


![image](https://user-images.githubusercontent.com/123365842/214875575-599546e3-b79b-418a-bf48-b2cdb7fed3b3.png)

the inputs a b or C changes but D is assigned with old X value since it is using the value of the previous Tclk ,the simulator mimics a delay or a flop. Where as, during synthesis we see the the OR and AND gates

Write the command "show"

![image](https://user-images.githubusercontent.com/123365842/214876066-86ce53aa-64dc-4025-b7f6-cc7e7462532d.png)


![image](https://user-images.githubusercontent.com/123365842/214876154-a7fe370e-4a3d-4883-879e-9d4850bc50ba.png)

Where both the inputs a and b are 0. a | b should output 0, which when ANDed with c, should give an output y of 0. The output y thus should hold the value 0. Instead,it holds the value 1 .

The netlist representation on synthesis yields

![image](https://user-images.githubusercontent.com/123365842/214876212-9b35d984-8b33-436e-a373-9b5bf396f4d3.png)

Here , the circuit behaves as intended combinational ckt. 

Output d results from the present value of inputs, and not the previous clock values like in the simulation results. 

SO, the waveforms of the stimulated RTL verilog code do not match with the gate level simulation of generated netlist,we get a Synthesis-Simulation Mismatch again.


# Day- 5 
# Day 5 - If, Case, For Loop and For Generate
If Constructs

If condition is used to to write priority logic. The condition one has a priority or if has more priority than the consecutive else statements . Only when condition 1 is not met condition 2 is evaluated and so on and y is assigned accordingly depending on the matching conditions.

if (cond_1)
begin 	
	y = statement_1;
end
else if (cond_2)
begin
	y = statement_2;
end
else if (cond_3)
begin
	y = statement_3;
end
else
begin
	y = statement_4;
end

If-else block implements a Priority logic that is if cond_1 is satisfied, next if statements are not executed. Thus above If-Else code translates to a ladder like multiplexer structure in the final design instead of a single multiplexer.

Dangers of using Incomplete If statements Inferred Logic which occurs due to bad coding styles that is incomplete if statements.

if (condt1) 
    y-a;
else if (condt2)
    y=b;

In the above code if condition 1 is matched y is equal to a else if condition 2 is matched y is equal to b but there is no specification for the case when condition2 is not matched, as a result of which the simulator tries to latch this case to the output y.It wants to retain the value of y.
This is a combinational loop to avoid that the simulator infers a latch. Enable of this latch is OR of the condition 1 and condition 2. If neither condition 1 or condition 2 is met the OR gate output disables the latch . The latch retains the value of y and stores it.
This is called the inferred latch due to incomplete if statements which is very dangerous for RTL designing. It should be avoided except for some special cases like the counter.

reg[2:0]
always @(posedge clk,posedge reset)
Begin
If (reset)
Count<= 3'b000;
else if(enable)
Count<= count+1;
end

This is also a case of incomplete if statements. Here ,if there is no enable the counter should latch onto the previous value.For example if the counter has counted up till 4 and there is no enable then it should retain the value 4 rather than going to 0 again.
So here the incomplete if statements result in latching And retaining the previous value which is our desired behavior in a counter. The earlier mux example was a combinational circuit and therefore we cannot have inferred latches.

Note:
If, case statements are used inside always block.
In verilog whatever variable we use to assign in if or case statements must be a register variable.

CASE Constructs

Let's look at the following verilog code block. Here, the inferred hardware should be a 4:1 multiplexer. The CASE statements do not have priority logic like IF statements.

always @(*)
begin
     case(sel)
		2'b00: begin
			y = statement_1;
			end
		2'b01: begin
			y = statement_2;
			end
		2'b10: begin
			y = statement_3;
			end
		2'b11: begin
			y = statement_4;
			end
	endcase
end

Depending on the cases matching the select y is assigned accordingly.

Some caveats with using CASE statements:

1.Incomplete CASE
Let's say I have a two bit variable select.

reg [1:0] sel
always @(*)
begin
     case(sel)
     2'b00: begin
                   . condition 1
                   end
     2'b01: begin
                   . condition 2
                   end
    end case
    end

Then select is C1 or C3 the conditions are not specified. It causes an incomplete case which results in inferred latches for these two cases that latch on to output y.This occurs when some cases are not specified inside the CASE block .For example, if the 2'b10 and 2'b11 cases were not mentioned , the tool would synthesize inferred latches at the 3rd and 4th inputs of the multiplexer.
Solution is code case with default inside the CASE block so that the tool knows what to do when a case that is not specified occurs.

Correct code :

reg [1:0] sel
always @(*)
begin
     case(sel)
     2'b00: begin
                   . condition 1
                   end
     2'b01: begin
                   . condition 2
                   end
    default :begin
                   . condition 3
                   end   
    end case
    end

2.Partial assignments

always @(*)
begin
	case(sel)
		2'boo: begin
			x = a;
			y = b;
		2'b01: begin
			x = c;
		default: begin
			x = d;
			y = d;
			end
	endcase
end

In the above example, we have 2 outputs x and y. This will create two 4X1 multiplexers with the respective outputs. If we look at case 2'b01, we have specified the value of x for this case ,but not the value of y. It appears that it is okay to do so, as a default case is specified for both the outputs, and if we don't directly specify the value of y for any case, the simulator will implement the default case. This, however , is incorrect. In partial assignments such as this, the simulator will infer a latch at the 2nd input for multiplexer y as no value is specified for a particular case.

3.Overlapping cases

always @(*)
begin
	case(sel)
		2'b00: begin
			y = a;
		2'b01: begin
			y = b;
			end
		2'b10: begin
			y = c;
		2'b1?: begin
			y = d;
			end
	endcase
end

In the above code block ,2'b1? specifies that the corresponding bit can be either be 0 or 1. This means when the sel input is holding a value 3 i.e 2'b11, cases 3 and 4 both hold true. What is synthesized depends on the mercy of the simulator. It can lead to Synthesis-Simulation mismatches.
If we used an IF condition here, due to priority logic, condition 4 would be ignored when condition 3 is met. However,in the CASE statement , even if the upper case is matched,all the cases are checked.So,if there is overlapping in cases,it poses a problem as the cases are not mutually exclusive. And we would get an unpredictable output.
Labs on Incorrect IF and CASE constructs

Example 1: Incomplete If statements

Below is the file titled incomp_if.v, and can be found in the directory verilog_files.

module incomp_if(input i0 , input i1 , input i2 , output reg y);
always @(*)
begin
	if(i0)
		y <= i1;
end
endmodule

The code contains an incomplete IF statement as no else condition corresponding to it is mentioned . On simulating this design , following gtkwave is obtained

Screenshot (883)



Write the following the command in the verilog file: "iverlog incomp_if.v tb_incomp_if.v"


![image](https://user-images.githubusercontent.com/123365842/215092505-e675f80c-07ff-4086-bdfd-2cdf4ed79276.png)


Write the following the command in the yosus terminal:"read_liberty -lib ../lib/sky...."

![image](https://user-images.githubusercontent.com/123365842/215096982-070c8a0f-e951-416e-b750-cf9770f824ed.png)


Write the following the command in the verilog file: "iverlog incomp_if2.v tb_incomp_if2.v"


![image](https://user-images.githubusercontent.com/123365842/215093337-07830b66-ff3c-47c5-854d-8aad5e339810.png)

Observation: When io is high,output follows i1. When io is low,it looks for i2.

If i2 is high,it follows i3. But if i2 is low(and io is already low),y attains a constant value=previous output.

This can be verified by checking the graphical realisation of the yosys synthesis below.

Write the following the command in the yosus terminal:"read_liberty -lib ../lib/sky...."

![image](https://user-images.githubusercontent.com/123365842/215098212-06aa1f00-0d5f-46be-a3e3-18e94bc173cb.png)

Yosys synthesizes enable pin is some combinational logic with the multiplexer as well as a latch.

Example3:

Below is a design with Incomplete Case's specification in a mux.

module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel , output reg y);
always @ (*)
begin
	case(sel)
		2'b00: y = i0;
		2'b01: y = i1;
	endcase
end
endmodule

The truth table for the above 2X1 mux looks like:
sel[1] 	sel[0] 	y
0 	0 	io
0 	1 	i1
1 	0 	latch
1 	1 	latch

Whenever se[1]=1 ,latching action takes place. The yosys synthesis implementation is given below.


Write the following the command in the verilog file: "iverlog incomp_case.v tb_incomp_case.v"


![image](https://user-images.githubusercontent.com/123365842/215117807-ac1a7f1a-faef-44aa-8fe5-6e08c009d4dc.png)

Write the following the command in the yosus terminal:"read_liberty -lib ../lib/sky...."

![image](https://user-images.githubusercontent.com/123365842/215120940-2be963d2-191c-41ad-add2-bf75e23d4112.png)

Observation: 1. !(sel[1]) is going to D latch enable. 2.The inputs io,sel[0], !(sel[1]) go to the upper mixing logic that is implemented on D pin of the latch.

Example 4:

Complete Mux along with all the cases specified.

module comp_case (input i0 , input i1 , input i2 , input [1:0] sel , output reg y);
always @ (*)
begin
	cae(sel)
		2'b00: y = i0;
		2'b01: y = i1;
		default:y = i2;
	endcase
end
endmodule

Output follows i2 at default case,if i1 and io go low. Hence a 4X1 mux is synthesized without any latch that can be verified below.

Write the following the command in the verilog file: "iverlog comp_case.v tb_comp_case.v"

![image](https://user-images.githubusercontent.com/123365842/215122432-c9bdb7e9-2402-4dd4-a716-9b0fa018f840.png)


Write the following the command in the yosus terminal:"read_liberty -lib ../lib/sky...."

![image](https://user-images.githubusercontent.com/123365842/215124251-c244988a-774c-45b9-b72e-8c83b065f92b.png)


Example 5: Partial Assignments

module partial_case_assign (input i0 , input i1 , input i2 , input [1:0] sel , output reg y , output reg x);
always @ (*)
begin
	cae(sel)
		2'b00: begin
			y = i0;
			x = i2;
			end
		2'b01: y = i1;
		default: begin 
			x = i1;
			y = i2;
			end
	endcase
end
endmodule


Write the following the command in the verilog file: "iverlog comp_case.v tb_comp_case.v"



Expected Circuit: The 2X1 mux with output y is inferred without any latch. To find out the latching condition of the second mux we take the help of the following truth table:
sel[1] 	sel[0] 	x
0 	0 	i2
0 	1 	latch
1 	0 	i1
1 	1 	i1

Condition for enabling:

              en=sel[1]+!(sel[0]) 

Using Redundancy Theorem

Yosys implementation of the above design after synthesis,

Write the following the command in the yosus terminal:"read_liberty -lib ../lib/sky...."

![image](https://user-images.githubusercontent.com/123365842/215267015-fd27bda4-a442-4423-99b8-63a0c0e9b8fa.png)


As expected, Only 1 D latch is inferred for X. No latch is inferred for y.

Example 6: Design of 4X1 mux having overlapping cases

module bad_case (input i0 , input i1 , input i2 , input [1:0] sel , output reg y);
always @ (*)
begin
	cae(sel)
		2'b00: y = i0;
		2'b01: y = i1;
		2'b10: y = i2;
		2'b1?: y = i3;
		
	endcase
end
endmodule

In gtkwaveform of RTL simulation:


Write the following the command in the verilog file: "iverilog bad_case.v tb_bad_case.v"

![image](https://user-images.githubusercontent.com/123365842/215267554-21e5665d-6766-4214-bedd-90cd5fe836a2.png)


Observation : When sel[1:0]=11, the output neither follows i2 nor i3. It simply latches to 1.

Whereas while running GLS on the netlist,the waveform of the synthesized netlist behaves as 4X1 mux as shown below

Write the following the command in the verilog file: "iverlog ../my_lib/verilog_model/primitives.v ../my-lib/verilog_model/sky .... bad_case.v tb_bad_case.v"

![image](https://user-images.githubusercontent.com/123365842/215269294-bb402b0a-0718-4de7-96c7-e5c1eef6cbb9.png)



Thus ,Overlapping cases confuse the simulator and leads to Synthesis-Simulation Mismatches.

# Introduction to Looping Constructs

There are two types of FOR loops in verilog.

1.FOR loop 1.Used within the always block 2.Used to evaluate expressions

    Generate FOR loop 1.Only used outside the always block 2.Used for instantiating hardware

Necessity of FOR loops

For loops are extremely useful when we want to write a code /design that involves multiple assignments or evaluations within the always block. Lets us take an example: If we want to write the code for 4:1 multiplexer, we can easily do so using a either four if blocks or using a case block with 4 cases,as seen in the previous if-else blocks.But this approach is not suitable for complicated design with numerous inputs/outputs say 256X1 mux.If we wanted to design a 256X1 multiplexer, we will have to write 256 lines of condition statements using select and corresponding assignments. But in for loop ,be it 4X1 or 256X1 we would always be writing 4 lines of code only. Although we need to provide 256 inputs using an internal bus.

integer k;
always @(*)
begin
	for (k = 0, k < 256, k= i  +1)
	begin
		if (k== sel)
			y = in[i];
		end
	end
end

This code can be infinitely scaled up by just replacing the condition i < 256 with the desired specification for our multiplexer.

Similarly, we can create High input demultiplexers as well.

integer k
always @(*)
begin
	int_bus[15:0] = 16b'0;
	for (k= 0; k< 16; k= k+ 1) 
	begin
		if (k == sel)
			int_bus[k] = inp[k];
		end
	end
end

Here , we have created a 16:1 demultiplexer using for loops within the always block. The int_bus[15:0] specifies our internal bus which takes on the input of the demux. It is necessary to assign all outputs to low for a new value of sel else latches will be inferred resulting in the incorrect implementation of our logic.

Below are few of the examples of FOR construct .

Example 1:

file mux_generate.v that generates a 4X1 mux using For loop.

module mux_generate (input  i0, input i1 , input i2 , input i3 , input [1:0] sel , output reg y);
wire [3:0] i_int;
assign i_int = {i3,i2,i1,i0};
integer k;

always @(*)
begin
	for(k = 0; k < 4; k=k+1)begin
		if(k == sel)
			y = i_int[k];
	end
end
endmodule

The 4 inputs get assigned to a the internal 4 bit bus named i_int.

The gtkwave obtained after the simulation

![image](https://user-images.githubusercontent.com/123365842/215269367-a2f2c9e1-6c3d-494f-a55d-18894f40cf16.png)


Example 2:

Similar to example 1, file demux_generate.v that generates a 4X1 demux using For loop.

module demux_generate (output o0 , output 02 , output o3 ,  output o4 , output o5 , output o6 , output o7 , input [2:0] sel , input i);
reg [7:0]y_int;
assign {o7,o6,o5,o4,o3,o2,o1,o0} = y_int;
integer k;

always @(*)
begin
	y_int = 8'bo;
	for( k = 0; k < 8; k++) begin
		if(k == sel)
			y_int[k] = i;
	end
end 
endmodule

Write the following the command in the verilog file: "iverlog comp_case.v tb_comp_case.v"

The above code has good readabilty,scalability and easy to write as well. Let's verify if it functions as a 8X1 demux as expected by viewing its gtkwave simulated waveform.

![image](https://user-images.githubusercontent.com/123365842/215272484-b00abe39-c792-47c9-b71b-6cdf4a4ccb7c.png)


# FOR Generate and its Uses

FOR Generate is used when we needto create multiple instances of the same hardware. We must use the For generate outside the always block.

We take example of a 8 bit Ripple Carry Adder(RCA) to understand the ease of instantiations provided by the For generate statement. An RCA consists of Full Adders tied in series where the carry out of the previous full adder is fed as the carry in bit of the next full adder in the chain. Hence, we can make use of generate for to instantiate every full adder in the design , as they are all represent the same hardware.

For this example , we use the file rcs.v which holds the code for the ripple carry adder. It also needs to be included in our simulation.

module rca (input [7:0] num1 , input  [7:0] num2 , output [8:0] sum);
wire [7:0] int_sum;
wire [7:0] int_co;

genvar i;
generate
	for (i = 1; i < 8; i=i+1) begin
		fa u_fa_1 (.a(num1[i]),.b(num2[i],.c(int_co[i-1],.co(int_co[i]),.sum(int_sum[i]));
	end

endgenerate
fa u_fa_0 (.a(num1[0]),.b(num2[0]),.c(1'b0),.co(int_co[0]),.sum(int_sum[0]));

assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule

Here, fa references another verilog design file containing the definition of for the full adder submodules .This is shown below, from the fa.v file

module fa(input a, input b , input c,  output co, output sum);
	assign  {co,sum} = a +b + c;
endmodule

In the RCA verilog code, we instantiate fa in a loop using generate for outside the always block.

Rules for addition :

N + N bit number --> Sum will be N + 1 bits N +M bit number --> Sum will be max(N,M) +1 bits

Now, let us simulate this design in verilog and view its waveform with GKTWave .As the rca design referances the file fa.v , we must specify it in our commands as follows

iverilog fa.v rca.v tb_rca.v
./a.out
gtkwave tb_rca.v

the resulting gtkwaveform is shown below that shows an adder being simulated:

![image](https://user-images.githubusercontent.com/123365842/215273394-8bd5e14e-c3d9-47d3-b0a1-eb64e3a24858.png)


Takeaways from this workshop:

    We succesfully learnt How to write the verilog codes using for,generate,if-else,case ,blocking/non blocking assignments so that our intended functionality is met.
    We learnt to genertaed the gtk waveform ans see the simulated wave results. We learnt to read timing diagrams as well.
    We learnt to synthesize the rtl verilog design using yosys and understand how the synthesizer implements the logic considering area and delay optimisations
    We learnt to verify the simulation -synthesis results by feeding netlist+testbench+Gate verilog models to the iverilog,during GLS(gate level synthesis simulation).
    We learnt good coding practices and ways to write optimised verilog codes.
    
    
    # Day-6
    
    # FPGA Fabric Design And Architecture
    
    ![image](https://user-images.githubusercontent.com/123365842/215945855-1f0d16fd-72c0-4889-8183-c74d0560c94b.png)
    


   ![image](https://user-images.githubusercontent.com/123365842/215945936-afbb419a-4b05-4ce1-9fce-015a2509b5f9.png)
   
   
   
   ![image](https://user-images.githubusercontent.com/123365842/215948624-9f18c656-8ed6-49a2-8b4c-f7b2891bb782.png)
   
   
   
   ![image](https://user-images.githubusercontent.com/123365842/215948699-b83f0ed4-c48d-4d7b-9155-b3cfcedaac1c.png)
   
   
   
   ![image](https://user-images.githubusercontent.com/123365842/215948877-ad579ff4-b230-49da-8f89-933b50460734.png)



   ![image](https://user-images.githubusercontent.com/123365842/215948998-65fb0061-1737-458b-bc50-ad477e9c3dfd.png)


   
   ![image](https://user-images.githubusercontent.com/123365842/215949115-9ba5aaa7-c6b8-4120-827d-f62d62a58e0d.png)


   
   ![image](https://user-images.githubusercontent.com/123365842/215949212-0cf08ba4-7f18-4ab1-bb84-58b6725c3740.png)
    
    
   
   ![image](https://user-images.githubusercontent.com/123365842/215949288-3508cb63-67fe-4ec1-93a5-d8fc9184360d.png)


   
   ![image](https://user-images.githubusercontent.com/123365842/215949479-d1ae0d56-718f-4351-a568-538292f07bfb.png)


   
   ![image](https://user-images.githubusercontent.com/123365842/215949684-71be1966-b7d8-43b2-9831-e9b33e2bf15f.png)
   
   
   
   ![image](https://user-images.githubusercontent.com/123365842/215950064-8299678d-4df7-4ecd-9c43-b1ef4f056a41.png)

 
   
   ![image](https://user-images.githubusercontent.com/123365842/215950206-76dda99e-bfd0-41b1-a499-a040977882b8.png)
   
   
   # Error1
   
   
   ![image](https://user-images.githubusercontent.com/123365842/215950775-a063a10b-9795-41ec-8072-7c99bb84a06f.png)
   
   
   # Error2
   
   
   ![image](https://user-images.githubusercontent.com/123365842/215951148-f450ac56-f235-4ede-97b4-eca3183b4b70.png)
   
# Day-7
# Advance Physical Design using OpenLANE/Sky130
# Day 1 -Inception of open-source EDA, OpenLANE and sky130 PDK

	To perform the intruction, which are given externaly in computers, some hardware is there which convert our external instruction into understandable language of computers. Arduino consists of both a physical programmable circuit board (often referred to as a microcontroller) and a piece of software, or IDE (Integrated Development Environment) that runs on the computer, used to write and upload computer code to the physical board.Basically microcontroller is made from package, inside the package chip is there.Chip is made by pads, core, die and foundary IP's.

![image](https://user-images.githubusercontent.com/123365842/216225495-063556cb-8a79-46e5-a8b4-d3f11ed41031.png)

# Package

The package is a case that surrounds the circuit material to protect it from corrosion or physical damage and allow mounting of the electrical contacts connecting it to the printed circuit board (PCB).

![image](https://user-images.githubusercontent.com/123365842/216225639-e63b3f9c-b3ef-4de0-9ee2-cd49a5ec240c.png)

# Chip

Inside the Package, chip is available which contains, foundary IP's (for example, RISC-V Soc, PLL, ADC, DAC, SRAM, SPD), core (core contains AND, OR etc. all gates and digital logics), pads (through which input and output signals are communicates).

![image](https://user-images.githubusercontent.com/123365842/216225721-122f7b4d-dad5-4481-ab33-6680138ea959.png)

# What is RISC-V?

RISC-V, where five refers to the number of generations of RISC architecture that were developed at the University of California, Berkeley. RISC is an open standard instruction set architecture (ISA) based on established RISC principles. A number of companies are offering or have announced RISC-V hardware, open source operating systems with RISC-V support are available, and the instruction set is supported in several popular software toolchains.

The instruction set is designed for a wide range of uses. The base instruction set has a fixed length of 32-bit naturally aligned instructions, and the ISA supports variable length extensions where each instruction can be any number of 16-bit parcels in length. The instruction set specification defines 32-bit and 64-bit address space variants. The specification includes a description of a 128-bit flat address space variant, as an extrapolation of 32 and 64 bit variants, but the 128-bit ISA remains "not frozen" intentionally, because there is yet so little practical experience with such large memory systems.

# How software communicate with Hardware?

Between apps or software (in our mobilephones and computers or laptops) and Hardware (in our mobilephones and computers or laptops), One full channel is there, which contains O.S. (operating system), compiler and assembler. This channel proccesses the inputs from the apps and gives the outputs to the Hardware. And according to the output of assembler, the hardware will perform.

![image](https://user-images.githubusercontent.com/123365842/216226235-be875ef2-5c5a-489d-863c-7d9317a91abe.png)

So, this inputs goes throuth the system software cahnnel, where O.S. handles the input/output operations, it allocates the memory to for the codes and low level systems functions are there in O.S. Then program goes to the compiler, where program will compile and generate the HDL program.This HDL program is basically the sets of Instructions which can hardware is able to understand. The instructions are basically depends on what kind of hardware we are using. For example if we are using Mips processor then instruction formaate will be according to the Mips processor, if Hardware is RISC-V then the instruction formate will be according to the RISC-V and similerly for Arm and intel processors also.

This sets of instrusctions is now given to the Assembler. here according to the instruction set, assembler will generate the Binary code (contains only 0s and 1s). this binary code can be understandable for hardware. And according to this code, hardware will gives the output.

# How to design Digital ASIC?

To design Digital ASIC, few tools or things which are required from the day one. These are

    RTL Design

    EDA tools

    PDK data

# what is RTL design?

In digital circuit design, register-transfer level (RTL) is a design abstraction which models a synchronous digital circuit in terms of the flow of digital signals (data) between hardware registers, and the logical operations performed on those signals.for this designs many open sorces are available. like, librecores.org, opencores.org, github.com, etc...

# What is EDA tools?

The term Electronic Design Automation (EDA) refers to the tools that are used to design and verify integrated circuits (ICs), printed circuit boards (PCBs), and electronic systems, in general. many open sorces tools are available like Qflow, OpenROAD, OpenLANE, etc...
# What is PDK Data?

PDK is process design kit. It is interface between FAB and design. This data is collections of files like,

    process design rules: DRC, LVS, REX

    Digital standerd cell libreries

    i/o librerirs

    etc.....

which are used to model a fabrication process for the EDA tools used to design an ICs. for example, in 2020, google release the open source PDK for FOSS 130nm production with the skywater technology. But right now it is at cutting age of the 5 nm also. But in many applications, the advance node is not required, and the cost of advanced node is also high as compared to 130nm processors. This 130nm processors are also fast processor. for example,

    intel: P4EE @3.46 GHz(Q4'o4)

    sky130_OSU (single cycle RV32i CPU) pipeline version can achieve more than 1 GHz clock

# Simplified RTL to GDSII flow

![image](https://user-images.githubusercontent.com/123365842/216226635-9d4e88b5-fe21-4107-9fb6-3fb0b37704c9.png)

### Synthesis In the synthesis, the design RTL is translated to a circuit out from the SCL. The resultant circuit is describes in HDL and usualy refered to the gate level netlist. the gate level netlist is functionaly equivelent to the RTL. "standard Cells" have regular layouts.
Floor planning and Power planning

The main objective here is that to plan silicon area and distribute the power to the whole circuit. In the chip floor planning, the partition chip die between different system building blocks and place the i/o pads. In micro floor planning, we define the dimensions, pin locations, rows.

![image](https://user-images.githubusercontent.com/123365842/216226778-a2a0a56d-b229-4bd8-9137-1d5ea74a91d9.png)


In power planning, the power network is connstructed. tipically, the chip is power by multiple VDD and GND. so, total components are connected to power supply horizontaly and vertically by metal streps. here parallel structures are used to reduce the resistance. To address the electromagnetization problem, power distribution network uses upper metal leyers, which are thicker than lower metal layers. Hence have less resistance.

![image](https://user-images.githubusercontent.com/123365842/216226914-399c08f5-1382-48a9-baf5-98a57379459e.png)

# Placement

In this process, we place the gate level netlist on the floor planning rows, alligned with the sites. cells should be placed very closed to eachother to reduce the interconnnect delay. Usually placement is done in 2 steps:

    Global placement

    Detailed placement
    
![image](https://user-images.githubusercontent.com/123365842/216227008-996f1c81-d198-476d-9a4a-21090c5a5b98.png)

Global placement

Global placement is very first stage of the placement where cells are placed inside the core area for the first time looking at the timing and congestion. Global Placement aims at generating a rough placement solution that may violate some placement constraints while maintaining a global view of the whole Netlist.
Detailed placement

In detailed placements, we determined the exact route and layers for each netlist. the objective of detailed placement is valid routing, minimize area and meet timing constrains. Additional objective is minimum via and less power.
Clock tree synthesis (CTS)

Before routing the signals, we have to route the clock. In the process of clock synthesis, we have distribute the clock to the every sequential elements. for example flipflops, registers, ADC, DAC ete. basically clock netwroks looks likes a tree. where the clock source is roots and the clock elements are end leaves. Synthesization should be done in a manner that with minimum skew and in a good shape.To minimize the clock skew by using the low-skew global routing resources for clock signals.Microsemi devices provide various types of global routing resources that significantly reduce skew.Usually a tree is a H tree, X tree etc.

![image](https://user-images.githubusercontent.com/123365842/216227551-936be733-39d6-43cf-b6c2-3020d1175320.png)

# Routing

After routing the clock, the signal routing comes. Making physical connections between signal pins using metal layers are called Routing. Routing is the stage after CTS and optimization where exact paths for the interconnection of standard cells and macros and I/O pins are determined. There are two types of nets in VLSI systems that need special attention in routing:

    Clock nets

    Power/Ground nets

The sky130 PDK defines the 6 routing leyers. the lowest leyer is called local interconnect layer (titanium nitride layer). Other five layers are alluminium layers.

![image](https://user-images.githubusercontent.com/123365842/216227685-73e8c995-fb5f-4d8c-8dc4-6520ca7f0524.png)

In the proccess of routing, metal trackes forms a routing grids and these grids are huge. so, devide and conquer approach is use for routing. The two types of routing is used:

    Global routing: Generates the routing guides

    Detailed Routing: Uses the routing guides to implement the actual wiring

# Sign off

Once the routing is done, we can construct the final layout. This final layout will goes under the verification. Two types of verifications are there:

    Physical verification: Here design rule checking will done and it will check the final layout and owners layout

    Timing Verification: Here Static Timing Analysis will done

# Introduction to OPENLANE:

OPENLANE is an automated RTL to GDSII flow that is composed of several tools such as OpenROAD, Yosys, Magic, Netgen, Fault, CVC SPEF-Extractor, CU-GR, Klayout and a number of scripts used for design exploration and optimization. It is started as an Open-source flow for a true Open Source tape-out Experiment. striVe is a family of open everything SoCs:

    Open PDK

    Open EDA

    Open RTL

# striVe SoC Family

![image](https://user-images.githubusercontent.com/123365842/216228007-1de27c57-c048-4fe7-b5de-26c83ad232e1.png)

The main goal of OPENLANE is to produce a clean GDSII with no human intervation (no-human-in-the-loop). here the meaning of clean is that:

    No LVS violations

    No DRC Violations

    No timing Violations

OPENLANE is tuned for skyWter130nm open PDK. it can be used to harden Macros and chips.there is two mode of operation

    Autonomus : it is the push botton flow. with the push botton , it is a some time base design and due to this push botton, we get final GDSII

    interactive : here we can run comamds and steps one by one.

It has large number of design examples(43 designs with their best configurations).

# OpenLANE ASIC Flow (Detailed)

![image](https://user-images.githubusercontent.com/123365842/216228146-74544a37-7128-49f0-bd8e-e534e4da298a.png)

The design exploration utility is also used for regression testing(CI). we run OpenLANE on ~ 70 designs and compare the results to the best known ones.
# DFT(Design for Test)

it perform scan inserption, automatic test pattern generation, Test patterns compaction, Fault coverage, Fault simulation.

![image](https://user-images.githubusercontent.com/123365842/216228218-6f391beb-3ce3-4ea4-b70c-73ec500a5f03.png)

After that physical implementation is done by OpenROAD app. physical implementation involves the several steps:

    Floor/Power Planning

    End Decoupling Capacitors and Tap cells insertion

    Placements: Global and Detailed

    Post Placement Optimization

    Clock Tree synthesis (CTS)

    Routing: Global and Detailed

Every time the netlist is modified.(CTS modifies the netlist and Post Placements optimization also modifies the netlist).so for that verification must be performed. The LCE(yosys) is used to formally confirm that the function did not change after modifying the netlist. 
Dealing with antenna rules Violation: when a metal wire segment is fabricated, it can act as antenna.as an antenna, it collect charges which can demaged the transister gates during the fabrication.

![image](https://user-images.githubusercontent.com/123365842/216229009-a1fd97cc-e17d-4c0f-b86f-00543f1393a1.png)

To address this issue, we have to limit the lenght of the wire. usually this is the job of the router. If router fails to do this, then there are two solutions:

    Bridging attaches a higher layer intermediary

![image](https://user-images.githubusercontent.com/123365842/216229074-61538ad8-aabc-4408-9a5e-3ebb49a9fcd7.png)

image

    Add antenna diode cell to leak away charges.(Antenna diodes are provided by the SCL)

![image](https://user-images.githubusercontent.com/123365842/216229129-30d8d9a0-6bff-400d-b8ff-0ee318ba49dc.png)

With OpenLANE, we took a preventive approach. here we add fake antenna diode next to every cell input after placement. Then run the Antenna checker on the routed layout. If the checker reports a violation on cell input pin, replace the fake diode cell by a real one.

![image](https://user-images.githubusercontent.com/123365842/216229221-3fc98a37-4a65-45a2-9207-7140f1f09eee.png)

# Static Timing analysis(STA)

It involves the interconnect RC Extraction(DEF2SPEF) from the routed layout, followed by STA on OpenSTA(OpenROAD) tool. resulting report will shows the timing violations if any violations is there.

# Physical Verification (DRC and LVS)

Magic is used for design Rules checking and SPICE Extraction from Layout. Magic and Netgen are used for LVS.

# Open source EDA tools
# OpenLANE Directory Structure in detail
# cd command

cd means change directory. this command will help us to go inside the directory.

# ls command

ls means listing the directory. It is used to find the list of total details of directory.

# ls --ltr

This command will help to list the details in cronological order.

Working in Sky130_fd_sc_hd PDK varient. where, "sky130" is process name or node name."fd" is a foundary name (skyWater foundary)."sc" means standerd cell librery files and the last one "hd" stands for high density(basically one type of varient).

Sky130_fd_sc_hd varient contains many technology files like verilog, spice, techlef, meglef,mag,gds,cdl,lib,lef,etc. (techlef file contains the layer information).

# Design Preparation Step

when we enter in the OpenLANE, we have to use flow.tcl because as a name says, it will goes with the flow using the script. And by using interactive switch, we will do step by step process. without interactive switch, it will run complete flow from RTL to GDSII. Now OpenLANE is open and we can see that prompt will change now. 

Write the Command is

$ cd Desktop/work/tools/openlane_workind_dir/openlane
$docker
$./flow.tcl -interactive

So, show the following figure:

![image](https://user-images.githubusercontent.com/123365842/216230707-e1f97470-1673-4a0b-b8c1-cb16841a9247.png)

Now, here we are ready to execute the command.

Now, if we are going into the design folder in openlane, there are nearly 30-40 designs are already builted. Out of them we can open any of the design. for example, here we are opening the picorv32a.v design. In this design we can see many files are available. i.e., scr, config.tcl, etc. This config.tlc file contains every details about the design. for example, details about enrollment, clock period, clock period port etc.

![image](https://user-images.githubusercontent.com/123365842/216231741-d64401fb-a0c7-43a9-90aa-f55854831a86.png)

Here we can see that the time period is set to the 5.00 nsec. but is we see in the openlane sky130_fd_sc_hd folder, the period is set about 24 nsec. so it is not override to the main file. If it override then give first priority to the main folder. 

Write the command is 

%package require openlane 0.9
%prep –design picorv32a

![image](https://user-images.githubusercontent.com/123365842/216232349-c3cb30de-d18b-43f3-9165-c4bec71eefc3.png)

Now, in openlane, we are going to run the synthesis, but before synthesis, we have to prepare design setup stage. for that command is " prep -design picorv32a".

Write the command is
$ cd work/tools/openlane_working_dir/openlane/designs/picorv32a
Now we have to input all the packages which required to run the flow.Here we are ready to execute the command.

Write the command is

$less config.tcl

![image](https://user-images.githubusercontent.com/123365842/216235412-f185b66f-995c-42a5-980c-4ff599cafc12.png)

Write the command is
Less sky130A_sky130_fd_sc_hd_config.tcl
![image](https://user-images.githubusercontent.com/123365842/216235549-b0d17780-7070-4b2e-bff2-f0eb58b4016d.png)
so, here it is shown that preparation is completed.

Review after design preparation and run synthesis

After completing the preparation, in the picorv32a file, the run terictory is created. Inside the folder, Today's date is created. so in this terictory some folders are available which is required for openlane.

To Review is the write command
cd work/…../picorn32a/$ runs/01-02-09-25/
01-02-09-25 $ cd tmp 
tmp $ ls
$ cd tmp
temp $ cd ..
01-02-09-25$ ls –ltr
$ cd tmp
tmp $ less merged.lef

![image](https://user-images.githubusercontent.com/123365842/216235854-3e7a4c52-7284-4258-867c-7dbeb5ab6d83.png)


![image](https://user-images.githubusercontent.com/123365842/216236125-c6566ada-9f6d-42fe-ad2c-8d31f97145ce.png)

In the temp file, merged.lef file is available which was created in preparation time. if we open this merged.lef file, we get all the wire or layer level and cell level information.

Write the command is 

$Less merged.lef
![image](https://user-images.githubusercontent.com/123365842/216236247-85c52e12-ae12-48f2-bfb3-ca561d9f771f.png)

![image](https://user-images.githubusercontent.com/123365842/216236472-3cec7431-f914-4d36-b03b-6db87ec74b3b.png)
While, in the result folder is empty because till we have not run anything and in the report folder all the folders are there about synthesis, placement, floorplanning,cts,routing,magic,lvs.

![image](https://user-images.githubusercontent.com/123365842/216236562-26690ff7-c5c8-4115-860f-714287301cdf.png)
now here also one config.tcl file is available similar like design folder. But this config.tcl file contains all default parameter taken by the run.

![image](https://user-images.githubusercontent.com/123365842/216236623-4b3871fa-8146-4db9-9eec-5ef606b955b9.png)

when we make some change in the origional configuration and then we run, for example if we make a change in core utilization in the floorplanning and then we run the floorplanning, at this time in the congig.tcl file, the core utility will change and by cross checking it we can check that the modification is reflected in the exicution or not.

Now, cmds.log file takes all the record of the commands, what we have fab.

![image](https://user-images.githubusercontent.com/123365842/216236767-173120a5-fa1a-4a74-85e4-4816dbb43c7e.png)

To Openlane
%run_synthesis

![image](https://user-images.githubusercontent.com/123365842/216236818-ff26a1d2-95ad-4f5e-94e7-209d667b25a0.png)
So, the flop ratio = (number of flip flops)/(number of total cell).

So, the flop ratio is 10.84%.

Before run, we saw that the result folder is empty. but now, after running the synthesis, we can see that all the mapping have been done by ABC.

![image](https://user-images.githubusercontent.com/123365842/216236856-f51c765d-53c9-40f2-b47b-df452af8dc30.png)

And in the report, we can see when the actual synthesis has done. and the actual statistics synthesis report is showing below, which is same as what we have seen before.
![image](https://user-images.githubusercontent.com/123365842/216238201-a14f19b2-7d93-4a64-b621-c2f70e85b508.png)
From the data of synthesis, total number of counter D_flip-flops is 1613. and the number of cells is 14876.
![image](https://user-images.githubusercontent.com/123365842/216238254-6340238a-2bb8-4372-92d5-c79d8c174d2d.png)
So, the flop ratio = (number of flip flops)/(number of total cell).

So, the flop ratio is 10.84%.

Before run, we saw that the result folder is empty. but now, after running the synthesis, we can see that all the mapping have been done by ABC.

![image](https://user-images.githubusercontent.com/123365842/216238319-8d3b9867-a3f4-49f6-a42a-6a98711037dd.png)

And in the report, we can see when the actual synthesis has done. and the actual statistics synthesis report is showing below, which is same as what we have seen before.

![image](https://user-images.githubusercontent.com/123365842/216238440-08ef691f-46f9-4f7c-aacf-d9901b10efe7.png)

# Advance Physical Design using OpenLANE/Sky130
# Day 2 -Good floorplanning Vs Bad floorplanning and introduction to library cells
# Chip floorplanning considerations
# Utilization factor and aspect ratio
# 1)defining the width and height of core and Die
![image](https://user-images.githubusercontent.com/123365842/216497139-9fc3bc28-bbfc-4007-91e8-51d3ecf0c315.png)
let's begin with netlist( Netlist describes the connectivity of an electronic designs). Considering a netlist with 2 flops and 2 gates.
![image](https://user-images.githubusercontent.com/123365842/216497239-eb25762f-2a40-4225-96b8-980b608af398.png)
lets giving the height and width of standerd cell is 1 unit. So, area of standerd cell is 1 square unit. And assuming the same area for the flip flops also.

Now lets calculate the area occupied by the netlist on a silicon wafer by arranging them together. The total area occupied by netlist in silicon wafer is 4 square units.
![image](https://user-images.githubusercontent.com/123365842/216497314-38be173d-8ddf-4b1b-b505-160c41fc5b57.png)

# what is the core and die?

A 'core' is the section of the chip where the fundamental logic of the design is placed.

A 'Die', which is consist of core, is small semiconductor material specimen on which the fundamental circuits is fabricated.

![image](https://user-images.githubusercontent.com/123365842/216497412-0b47e03c-5c58-40d6-a8ac-2c8730e70490.png)
If we put the 'arranged netlist' in the core, then whole core is occupied by netlist. that means utilization of core is 100%.
![image](https://user-images.githubusercontent.com/123365842/216497511-c54c2411-d246-425f-8f03-b8c3d234a3fa.png)

# Utilization factor

it is defined as, 'the area occupied by netlist' devided by the 'total area of core'.

so, in above case, the utilization factor is 1.

practically, we don't go with 100% uti;ization. practically utilization factor is about 50%-60% to add other extra cells (like buffer) in the core after netlist is placed.

# Aspect Ratio

it is defined as (height)/ (width). here in above example the aspect ratio is 1.
# Concept of pre-placed cells
# 2) Define locations of preplaced cells

to define the preplaced cells, let's take a combinational logic i.e., mux, multiplier, clock devider, etc. and assuming that the output of the circuit is huge and assuming that the circuit has some 100k gates. so let devides in two blocks of 50k gates.
![image](https://user-images.githubusercontent.com/123365842/216497694-8a8e2645-464d-4f72-989e-cb3d42eabdab.png)
This both blocks are implimented separatly. Now, extending the input and output pins from the both blocks. now, let's detached these box. we will black box the boxes and detached them. After black boxing, the upper portion is invisible from the top or invisible to the one , who is looking into the main netlist. now we make separate them out.
![image](https://user-images.githubusercontent.com/123365842/216497747-eaac9452-80c0-4de7-8301-6991645ee807.png)

This blocks are implemented in netlist once and then we can reuse it multiple time. Similarly, there are other modules or IPs also readily available.i.e.,memory, clock gating cell, comparater, mux. these all are part of the top level netlist.They recieve some signals, they perform some functions, they deliver the outputs but the functionality of the cell is implemented only once. That what we called as preplaced cells.

The arrangement of these ip's in a chip is refferd as floorplanning.These IP's have user-defined locations, and hence are placed in chip before automated placement and routing are called "preplacement cells".These cells are place din such fashion that, the placement and routing tool not touch the location of the cell.

![image](https://user-images.githubusercontent.com/123365842/216497877-04b33ae5-e97f-4092-975d-9bfd199c6b33.png)

Let consider memory as a preplaced cells as a block 'a', block 'b' and block 'c'. Memory of any device is implemented once and reused multiple times. these preplaced cells are located as per the design bacckground. the location of the cells are never touched.

# De-coupling capacitors
# 3) surround pre-placed cells with Decoupling capacitors

Let consider some circuit, which is part of the blocks which were defined above. When some gate (let consider AND gate) switched from 0 to 1 ot 1 to 0, considered amount of the switching current required because of small capacitance is available there. this capacitor should be completely charged to represent logic 1 and completly discharged to represent logic 0. the required amount of the charge is suplied from the Vdd and absorb from the Vss. during supplying the current, wire has some drop of voltage due to resistence and inductunce of the physical wire.

![image](https://user-images.githubusercontent.com/123365842/216498023-478e280e-d1ae-4800-98be-9e69fc9f1718.png)

So, due to this if ideal logic 1 = 1 volt then here practically it can be less then 1 volt i.e., 0.97 volts (Vdd'). So, for any signal to be considered as Logic '0' and '1' in the NM low and NM high range. It is danger case.

![image](https://user-images.githubusercontent.com/123365842/216498080-bfe00810-8542-47fa-8b94-968584c56322.png)

To solve this problem,, we have to put De-coupling capacitor in parallel with the circuit. Every time the circuit switches, it draws current from Cd, whereas, the RL network is used to replacenish the charge into Cd.

![image](https://user-images.githubusercontent.com/123365842/216498230-a19749a0-e510-4128-9b11-a3c69a4e7e77.png)

![image](https://user-images.githubusercontent.com/123365842/216498256-f4e3ab25-5dd8-40ae-9ec0-92caf450588c.png)

# Power Planning
# 4) How to do power planning?

Up to here, we have taken care of local communication. Now let consider that local circuitory as a black box and it can be repeat multiple times and power supply is also connected to all of them as shown below,

![image](https://user-images.githubusercontent.com/123365842/216498336-e2debdcf-81dd-4c38-a4bf-9cf119353c52.png)

Now 16 bit bus has to retain the same signal from driver to the load. so it should get the sufficient power from the supply. But at this bus, there is no de-coupling capacitor is available because it is not physible to put capacitor at all over the place. now, power supply is far away from the bus, that is why some drop between them will definalty occurs.

Let consider this 16 bit bus connected to inverter. So, all capacitor are initially charged will get discharged and vice-versa due to inverter.

![image](https://user-images.githubusercontent.com/123365842/216498433-f96323ee-b3a2-425e-af42-52161def28bf.png)

But the problem is occurs due to all capacitor is connected to the single ground. This will cause a bump in 'ground' tap point during discharging.

![image](https://user-images.githubusercontent.com/123365842/216498474-885afa8c-0e9b-4118-8f8b-aebd3110078a.png)

Same problem will occurse during the charging time also. at that time lowering of voltage occurse at 'Vdd' tap point.

![image](https://user-images.githubusercontent.com/123365842/216498551-84387c34-790f-483a-bcbf-ffd1e92917d5.png)

The solution of the problem is use multiple power supply. So, every block will take charge from neartest power supply and similarly dump the charge to the nearer ground. this type of power supply is called mesh.

![image](https://user-images.githubusercontent.com/123365842/216498635-097bc5c7-3e54-4e2f-a00e-99a5d10bb9b5.png)

And the power planning is shown below,

![image](https://user-images.githubusercontent.com/123365842/216498733-45299293-f07a-4af5-8bac-1f7ab9a5fee7.png)

# Pin placement and Logic floor planning considerations
# 5) Pin Placement

Lets take below designs for example that needs to implemented.

![image](https://user-images.githubusercontent.com/123365842/216498870-4e753678-e24d-4dbc-999f-ef080ebc32f1.png)

Both the sections has different inputs like Din1 and Din2 and operated from different clocks like clock 1 and clock 2. along with that we have preplaced cells as well. So, basically now we have 4 input ports and 3 output ports.

let's have one more design that needs to be implemented. this types of circuits are very much helpful to understand the timing analysis of inter clocks.

now complete design becomes like given below which has 6 input ports and 5 output ports. it is called the 'Netlist'.

![image](https://user-images.githubusercontent.com/123365842/216498934-415b69e9-5c3b-4ff0-98d0-927f14eaee9d.png)

Let's put this netlist in the core which we have designed before and let's try to fill this empty area between core and die with the pin information. The frontend team who decides the netlist input and output and the backend team who done the pin placements. So according to the pin placements, we have to locate the preplaced blocks nearer to the inputs of the preplaced blocks.

![image](https://user-images.githubusercontent.com/123365842/216499001-a855dd76-345d-48ce-be01-cb8eb5adcea5.png)

Here one thing that we noticed is that clock-in and clock-out pins are bigger in size as compared to input and output pins. reason behind this is that, input clocks are conntinuously provides the signal to the every elements of the chip and output clock should out the signal as fast as possible. So, we need least resistance path for the clocks inputs and clocks outputs. So, bigger the size, lower the resistance.

One more thing is need to take care about is that, this pin placement area is blocked for routing and cell placements. so we nned to do logical cell placement blockage. this blockage is shoown in above image in between pins.

So, floor plan is ready for Placement and Routing step.

# Steps to run floorplan using OpenLANE

Before run the floorplanning, we required some switches for the floorplanning. these we can get from the configuration from openlane.

![image](https://user-images.githubusercontent.com/123365842/216499709-7aa46e0f-4bdc-4359-ac18-dae90b83cd3f.png)

Here we can see that the core utilization ratio is 50% (bydefault) and aspect ratio is 1 (bydefault). similarly other information is also given. But it is not neccessory to take these values. we need to change these value as per the given requirments also.

Here FP_PDN files are set the power distribution network. These switches are set in the floorplane stage bydefault in OpenLANE.

![image](https://user-images.githubusercontent.com/123365842/216500065-80732e6e-3148-4465-8938-453a9ba33e01.png)

Here, (FP_IO MODE) 1, 0 means pin positioning is random but it is on equal distance.

In the OpenLANE lower priority is given to system default (floorplanning.tcl), the next priority is given to config.tcl and then priority is given to PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl).

Now we see, with this settings how floorplan run.
Reviewing floorplan files and steps to view floorplan

In the run folder, we can see the connfig.tcl file. this file contains all the configuration that are taken by the flow. if we open the config.tcl file, then we can see that which are the parameters are accepted in the current flow.

![image](https://user-images.githubusercontent.com/123365842/216500316-3d83f796-1d61-46bc-a86c-5a72debf62f3.png)

here we can see that, the core utilization is 35%, aspect ratio is 1 and core margin is taken as 0. while in default the core utilization is 50%. this is the issue. because this design is override the system. but it is the taken from PDK varient.tcl file. so priority vise it is true.

To watch how floorplane looks, we have to go in the results. in the result, one def( design exchange formate) file is available. if we open this file, we can see all information about die area (0 0) (660685 671405), unit distance in micron (1000). it means 1 micron means 1000 databased units. so 660685 and 671405 are databased units. and if we devide this by 1000 then we can get the dimensions of chips in micrometer.

![image](https://user-images.githubusercontent.com/123365842/216500398-5b6845f0-b45a-4263-9b3e-8fd99f775154.png)

so, the width of chip is 660.685 micrometer and height of the chip is 671.405 micrometer.

To see the actual layout after the flow, we have to open the magic file by adding the command magic -T /home/kunalg123/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def

And then after pressing the enter, Magic file will open. here we can see the layout.

![image](https://user-images.githubusercontent.com/123365842/216500522-2a0958e1-ce3d-4045-87b2-1424483ee7cb.png)

# Reviewing floorplan layot with magic.

In the layout we can see that, input output pins are at equal distance.

![image](https://user-images.githubusercontent.com/123365842/216500790-fa196b1f-2f8e-458c-9621-9a64387e7e91.png)

after selecting (To select object, first click on the object and then press 's' from keyboard. the object will hight lited. to zoom in the object, click on the object and then press 'z' and for zoom out press 'sft+z') one input pin, if we want to check the location or to know at on which layer it is available, we have to open tkcon window and type "what". it will shows all the details about that perticular pin.

![image](https://user-images.githubusercontent.com/123365842/216501273-a7ab1bb5-d7a1-4c9d-9ef7-1cc353e09d9b.png)

![image](https://user-images.githubusercontent.com/123365842/216501382-8e51996c-e3be-408e-8e7d-0efabd2ef7c4.png)

so, it show that the pin is in the metal 3.similarly doing for the vertical pins, we find that this pin is at metal 2.

![image](https://user-images.githubusercontent.com/123365842/216501774-e86b5881-607e-49b8-8caa-1ede0e807ddc.png)

Along with the side rows,the Decap cells are arranged at the border of the side rows.

![image](https://user-images.githubusercontent.com/123365842/216501601-cddf8697-4114-4683-8f24-f320cdc38274.png)

Another cells also placed here, which is a tap cells. these cells are meant to avoide the latch-up problems in the CMOS devices. it connect N-well to the Vdd and substrate to the Ground. these tap cells are placed at diagonally equal distance.

![image](https://user-images.githubusercontent.com/123365842/216501884-cae9cf3b-28f7-4aaf-8967-ec214870d16f.png)

In the floorplane, standerd cells are not placed but here standerd cells are available in the left side of the floorplan. we can see few boxes are there.

![image](https://user-images.githubusercontent.com/123365842/216502114-dfd0b486-34da-4aed-ace6-4dc1b59e79a1.png)

here we can see that first standerd cells is for buffer 1. similarly other cells are for buffer 2, AND gate etc.
Library building and Placement
Netlist binding and initial place design
1) bind netlist with physical cells

Taking netlist as what we taken before,

![image](https://user-images.githubusercontent.com/123365842/216502199-1c2e32d5-4066-4802-ac90-3f42ababfb56.png)

Here, we can see that every gate or flip-flops have a shape to understand the functionality of the element. But practically, this cells are square or rectangular boxes which has internally some logic to perform. So, here we are taking all the elements from netlist and giving them a perfact height and width with perticular dimention. These all cells together are called 'self'. And this self are stored in the lybrary. Library have all the innformation about all the blocks, like height, width , time delay, conditional innformation, etc. library also have a option for the similar cells (with same functionality) like this with different height and width. According to our space available at floorplanning we can choose out of them.

![image](https://user-images.githubusercontent.com/123365842/216502240-9e99a04d-d34b-43cb-a9b5-ae3b8c6681ca.png)

After giving size and shape to each and every box, next step is to take the boxes or element from library and placed in the floorplan. This is called placements of the cells.According to the design of the netlist, we have to put physical blocks in the floorplan which we have design before.Put all the blocks according to the input and output of that perticular blocks.

![image](https://user-images.githubusercontent.com/123365842/216502303-40314d80-e89e-445d-9180-4e5626e9571d.png)

up to here we have done stage one and stage two placement. Now we will going for stage 3 and 4. here we have to place FF1 of stage 3 nearer to the Din3 and FF2 of stage 3 nearer to the Dout3. But Din3 and Dout3 are at somme distance from eachother. same thing is there for FF1 and FF2 of stage 4. Let's we placed these all element in such manner that all elements are closed to it's input and output pins.

![image](https://user-images.githubusercontent.com/123365842/216502368-316f9ac4-c908-428c-b8c6-ffc88fb5cdf7.png)

But, the distance of FF1 of Stage 4 and Din4 is still far them others. By optimizing the placement, we can solve this problem.

# Optimize placement using estimated wire lenght and capacitance
# 2) Optimize Placement

As we seen that the distance from Din2 to FF1 of stage 2 is higher. so if we connect the wire between them then resistance and capacitance of the wire comes in to the picture. and due to this the signal integrity can not maintain.

To maintain the integrity of the signal out from Din2 to FF1, we have to put some repeaters like buffers on between Din2 and FF1. But it will cause of loss of area.

In the stage 1, there is no need of any repeater to transmit the signal. But in stage 2, due to high distance, the lenth of wire is high and signal is not transmitted in perticular range. so we required repeater.

![image](https://user-images.githubusercontent.com/123365842/216502492-716b2949-09ed-4f5b-931b-bee50e785b1b.png)

# Final Optimization

Similar as stage 2, in Stage 3 also we required the buffer between gate 2 and FF2.

![image](https://user-images.githubusercontent.com/123365842/216502577-cdf59d48-5951-4739-9e71-248835a41907.png)

Stage 4 is bit tricky as compared to other stages. ![image](https://user-images.githubusercontent.com/123365842/216502610-821a867c-daf0-4e52-8fb7-db576f5357f9.png)

Now we have to check that, what we have done is correct or not. For that we need to do Timing analysis by considering the ideal clocks and according to the data of analysis, we will understand that, the placement is correct or not.

# Need for libraries and characterization.
# Library charactorization and modelling

In whole IC design, we have to go through synthesis, floor/power planning, placement, routing , STA. In all this steps one thing remain common, which is "Gates or Cells". That is where the library charactorization becomes very important.

# Congestion aware placement using RePLAce

Right now we are not constrain about timing, but constrain about the congestion. so, we are making the congrstion is less.

The placement is donne in two stages. Global and detailed. In global placement, legalization is not happened but after detailed placement legalization will be done.

When we run the placement, first Global placement is happens. main objective of glibal placement is to reducing the length of wires.

Now opening the Magic file to see actual view of standerd cells placement.And the actual view in the magic file is given below,

![image](https://user-images.githubusercontent.com/123365842/216502874-e0dea5f3-825b-4784-98e8-25ef755df615.png)

If we zooom into this, we find the buffers, gates, flip flops in this.

![image](https://user-images.githubusercontent.com/123365842/216502959-6bdd549e-9840-4b34-897a-552f11d6ad3a.png)

# Cell design and characterization flows
# Inputs for cell design flow
# Cell design flow

As we know that standerd cells are placed in the library. And in the library many other cells are available which have same functionality but the size is different. As size is different the parameters like hVt, Ivt also different for each standerd cells.

If we take one of the standerd cells called inverter, it has their own design flow by this it can be understandable to EDA tool.

The cell design flow is devided into three part.

    Inputs

    Design steps

    Outputs
    
 ![image](https://user-images.githubusercontent.com/123365842/216503071-3e0e1ce4-0e42-4221-ab7c-aaccf0396d5b.png)
 
 # 1)inputs

inputs required for cell design is PDKs, DRC and LVS rules SPICE models, library and user defined specs.
Circuit design steps
# 2)design steps

steps are circuit design, layout design, characterization
# 3)Outputs

The typical output what we get from the circuit design is CDL(circuit description language) file,GDSII,LEF,extracted spice netlist(.cir).
# Layout design steps

    implement function
    
![image](https://user-images.githubusercontent.com/123365842/216503198-b126e2c6-ec8a-4f7a-85b0-6b01ec507f1c.png)
 
Derive the NMOS and PMOS network graph

![image](https://user-images.githubusercontent.com/123365842/216503252-6e0d4e37-6e08-475c-b0ef-c85f2a1349a0.png)

Obtain the Euler's path

![image](https://user-images.githubusercontent.com/123365842/216503321-ed693d03-9f80-4bde-be48-c6560d61e6c8.png)

Stick diagram
![image](https://user-images.githubusercontent.com/123365842/216503397-1101d1c9-a003-4cb8-8e86-7c95af73ea73.png)

Convert stick diagram into proper layout

![image](https://user-images.githubusercontent.com/123365842/216503446-733d0fb0-3f45-482a-93ed-ee1820a957b1.png)

After layout design, we have to ecxtract the layout and characterize it. In characterization step, we can get the information about Timing, Noice,power.libs and function.

# Characterization Flow

As of now, from the circuit design and layout design, we have final layout of buffer cell. where two buffers are connected in series with each other.

![image](https://user-images.githubusercontent.com/123365842/216503543-775a5aeb-1604-47e3-bbff-d2ae4117d899.png)

Now steps of flow is:

    Read the model file

    read the extracted spice netlist

    reconize the behavior of buffer

    Read the subcircuit of the inverter

    Ateched the neccessory power source

    Apply the stimulus

    Provide the necessory of output capacitance

    Provide the necessory simulatin command

This all steps we have to give in "GUNA" software. and this software will give the timing, noise, power.libs and functions.

# General Timing characterization parameters
# Timing threshold defination

![image](https://user-images.githubusercontent.com/123365842/216503672-a61a6172-45a0-433a-a46f-93e982085d41.png)

Let we take the waveform from the output of the first buffer and it will be input of the second buffer and taking output of the second buffer also.

![image](https://user-images.githubusercontent.com/123365842/216503723-68684529-16d3-488f-ba05-13c15182716d.png)


    slew_low_rise_thr

here low means nearer to the ground, and rise tresold means we want to measer the slope of the increasing graph. typical value of slew low rise thr is around 20-30%. 

![image](https://user-images.githubusercontent.com/123365842/216503788-25f8f5b2-84c6-4404-942a-bddc643f61c6.png)


    slew_high_rise_thr

same as above, high means nearer to high value. 

![image](https://user-images.githubusercontent.com/123365842/216503860-8f27dc65-230c-4bfc-8067-64b36806f028.png)

whenever we want to calculate the slew, take the point at 20% from the low and take the point at 20% from the high. according to these point, take the time data and the time difference between them will helps to calculate the slew.

    slew_low_fall_thr

![image](https://user-images.githubusercontent.com/123365842/216503899-fd9d2ef3-027d-45d8-a84c-223fc38fd8f6.png)

    
    slew_high_fall_thr
    
![image](https://user-images.githubusercontent.com/123365842/216503981-8ce5700d-064f-4fb0-a88c-c1acecfa3092.png)

NOw, taking the waveform of input stimulus which is input of the first buffer and with that taking output of the first buffer.

Similar as a slew, thresolds are for delay also available. for that same as slew, we have to take some rise and fall points from the waveforms. this tresolds are almost 50%.

    in_rise_thr

![image](https://user-images.githubusercontent.com/123365842/216504041-12eb18a3-cd32-44d5-ad7a-6fd430095bf9.png)

    in_fall_thr
    
![image](https://user-images.githubusercontent.com/123365842/216504093-d2cb59d8-2455-4bce-9ceb-89d1f104d57b.png)

    out_rise_thr
    
![image](https://user-images.githubusercontent.com/123365842/216504149-d6b167ba-9b7a-4dbc-a047-0e44931967ac.png)

    out_fall_thr
    
![image](https://user-images.githubusercontent.com/123365842/216504229-e74fd8fe-fe1d-41c0-931c-931205cd1564.png)

So, according to rise and fall theresold we can find the rise delay and fall delay of the buffer.

![image](https://user-images.githubusercontent.com/123365842/216504277-fe6633af-09b2-4cc2-805f-5b8874932da6.png)

# Propogation delay and Transition time
# propogation delay

let's take the same setup for understand the propogation delay. Time delay = Time(out_thr)-time(in_thr).

Let's take waveform on which we can apply above formula.

![image](https://user-images.githubusercontent.com/123365842/216504353-14cfefec-7441-4ec6-9afd-7ecd7d8927fe.png)

In any case if thresold point move at the top, at that time we get negative delay because output comes before input. so reason behind the negative delay is the poor choice of the tresold points. which is not acceptable. so, choosing the thresold point is very important.

![image](https://user-images.githubusercontent.com/123365842/216504406-79528228-8238-4995-81e2-c38ed90d3cf0.png)

Taking another example where the wire delay is very high because of high distance between two elements. so, here by choosing correct thresold point then also we get the negative delay.

![image](https://user-images.githubusercontent.com/123365842/216504505-5ccf0c3b-d611-4340-a1b9-7b1ccc252dc3.png)

# Transition time

transition time = time(slew_high_rise_thr)- time(slew_low_rise_thr)

or

transition time = time(slew_high_fall_thr)- time(slew_low_fall_thr)

let's take waveform for understand the slew calculation.

![image](https://user-images.githubusercontent.com/123365842/216504574-50355add-91a8-465e-b7bb-a8fa4d6c59f9.png)


# Day 3 -Design library cells using Magic Layout and ngspice characterization
# Labs for CMOS inverter ngspice simulations
# SPICE deck creation for CMOS innverter
# IO placer revison

Till now, we have done floor planning and run placement also. But if we want to change the floorplanning, for example, in our floor planning, pins are at equal distance and if we want to change it then we can also make it by "Set" command.

For that first we have to check the swithes in the configuration and from that we have to take the syntax "env(FP_IO_MODE) 1". and make it to the "env(FP_IO_MODE) 2". then again run the floorplanning.

Then check the changes in the pins location through magic -T.

Write the command is 

"$magic –T /home/naykyitun/desktop/work/tools/openlane_working_directory/pdks/sky130A/libs.tech/magic/sky130A.tech leaf read ../../tmp/merged.lef def read picrov32a.floorplan.def&"

![image](https://user-images.githubusercontent.com/123365842/216800048-6bc0b25d-4cf3-4ad4-99e3-bc9813470e50.png)

So, here we can see that there are no pins in the upper half side. all pins are in the lower half of the core.
SPICE deck creation for CMOS inverter
VTC- SPICE simulations.

Before entering into the simulation, we have to creat the spice deck. The spice deck is nothing but netlist. so, we have to creat the spice deck for CMOS.

    Component connectivity

![image](https://user-images.githubusercontent.com/123365842/216800071-4cc91821-e540-49aa-8468-dfb0fe306c99.png)

    Define the components values
    
 ![image](https://user-images.githubusercontent.com/123365842/216800145-2f3df5de-f7c8-4c7d-9b55-cd8a079f3af3.png)
 
    Identyfy the nodes
    
 ![image](https://user-images.githubusercontent.com/123365842/216800196-48231a17-b36c-4bcf-83dc-3f512ce4e064.png)

    Name 'Nodes'
    
 ![image](https://user-images.githubusercontent.com/123365842/216800208-3a41b037-9ee2-4db0-940c-a086f0353303.png)

Now, let's strat the writing the SPICE deck

![image](https://user-images.githubusercontent.com/123365842/216800216-11f2fb76-1439-4a57-97e9-ff08e5350c52.png)

In the syntex, It is like Name of the mosfet, drain , gate, substrait , source. so, the meaning of the syntex is that, name of the mosfet is M1, Drain is connected to OUT node, Gate is connected to IN node, Substrait is connected to Vdd and the Source is connected to Vdd node. PMOS says the type of mosfet and the Width and lenth of channel is defined. similarly, For M2, syntex were written.

# SPICE simulation lab for CMOS

Tile we discribe the connectivity information about CMOS inverter only. Now we have to discribe connectivity information about other components also like source, capacitor etc. so, lets look into the other components.

First we discribe the load capacitor and then about the Vdd and Vin.

![image](https://user-images.githubusercontent.com/123365842/216800252-ff65b3c0-00da-49f9-a1b4-645609f6f5ed.png)

Now, we have to give simulation command. which is about swiping the Vin from 0 to 2.5 with the steps of 0.05. Because we want Vout while changing the Vin.

![image](https://user-images.githubusercontent.com/123365842/216800264-e4b37cfa-a868-41a8-bde2-197baa651029.png)

The final step is to discribe the Model file.Model file contains all the details about PMOS and NMOS. from this file only we get the information about PMOS and NMOS.

![image](https://user-images.githubusercontent.com/123365842/216800294-5d2929da-848e-4a5c-a270-eb1e7ae2a816.png)

So, the total program is given below,
   
![image](https://user-images.githubusercontent.com/123365842/216800300-cbbef08a-2627-45f3-ab09-bfe24f0c877f.png)

Now, doing the simulation and get the graph like this,

![image](https://user-images.githubusercontent.com/123365842/216800315-7ea908c3-f1b4-445a-8683-329df4841c65.png)

Now, doing other simulation in which we change the PMOS width to 3 times of NMOS width. and after diong the simulation, we get the graph like this,

![image](https://user-images.githubusercontent.com/123365842/216800332-1401a97e-1d31-4252-b08c-473425c5b51a.png)

The difference between this two graph is that in the second graph the transfer charactoristic is lies in the ecxact middle of the graph where in the first graph it is lies left from the middle of the graph.
# Switching Thresold Vm

These both model of different width has their own application. By comparing this both waveform, we can see that the shape of the both waveform is same irrespective of the voltage level.

This thing tell us that when Vin is at low, output is at high and when Vin is at high, the output is at low. so the charactoristic is maintain at all kind of CMOS with different size of NMOS or PMOS. That is why CMOS logic is very widely used in the design of the gates.

Switching thresold, Vm (the point at which the device switches the level) is the one of the parameter that defined the robustness of the Inverter. Switching thresold is a point at which Vin=Vout.

![image](https://user-images.githubusercontent.com/123365842/216800364-e1909305-31d3-4c96-941f-71ccc788e1b9.png)

In this figure, we can see that at Vm~0.9v, Vin=Vout. This point is very critical point for the CMOS because at this point there is chance that both PMOS and NMOS are turned on. If both are turned on then there is chances of leakage current(Means current flow direcly from power to ground).

By comparing this both the graph we can understang the concept of switching thresold voltage.

![image](https://user-images.githubusercontent.com/123365842/216800386-f41b8984-2da2-4081-ae91-220336a6c4e8.png)

![image](https://user-images.githubusercontent.com/123365842/216800400-30572a6c-8811-407b-990c-a73dde3a84f0.png)

Lab steps to git clone vsdstdcelldesign

To get the clone, copy the clone address from reporetery and paste in openlane terminal after the command "git clone". this will create the folder called "vsdstdcelldesign" in openlane directory.

Write the command is "openlane$git clone htps://github.com/nickson-jose/vsdstdcelldesign.git"

![image](https://user-images.githubusercontent.com/123365842/216800433-79a3dc6f-fff8-4c03-bbae-4b1710fdd4a5.png)

So, if we open the openlane directory, we find the vsdstdcelldesing folder in the openlane directory.

![image](https://user-images.githubusercontent.com/123365842/216800465-e6388a3c-378d-4d20-bc9a-9186934625b1.png)

Now if we goes in the vsdstdcelldesign folder and open it, we get the .mag file,libs file etc.

![image](https://user-images.githubusercontent.com/123365842/216800493-38d12cc6-9257-45f2-8f43-249b1d2e20ba.png)

now, let's open the .mag file and see that which layers are used to build the inverter. But before opening the mag file, we need tech file. so we will copy this file from this given below address,

![image](https://user-images.githubusercontent.com/123365842/216800919-16a9dc0e-15cd-4e17-bb22-c004ad40b633.png)

And do copy by "cp" command to the location which is given below,

![image](https://user-images.githubusercontent.com/123365842/216800600-b6394db6-c5a6-4351-8aec-b11e510494ac.png)

Now, we can see that this file is copied in the vsdstdcelldesign folder.

![image](https://user-images.githubusercontent.com/123365842/216800948-6b8cc82b-1994-4a30-a744-453e540ecebe.png)

Now, here to see the layout in magic, we don't need to write the whole address because we copy the tech file here.

Now, appying the magic comand like this,

![image](https://user-images.githubusercontent.com/123365842/216800992-62b7ce67-9b3a-451e-8204-4af19d90f3c2.png)

Now, we can see the layout of CMOS inverter in the magic like this,

![image](https://user-images.githubusercontent.com/123365842/216801015-cf2ab34c-4e8b-4b8c-8015-6c73939fc2a8.png)

Inception of layout CMOS fabrication process
create active region
1) selecting a substrate

we select P-type silicon substrate with high resistivity(5~50 ohms) with moderate dopping and orientation is (100).
2) creating active region for transister

First, we create the isolation layer by depositing the Sio2 layer (~40nm) on the substrate.

![image](https://user-images.githubusercontent.com/123365842/216801031-bf3ac0ba-4997-444c-aac3-775a109361f5.png)

Now, we are depisiting the Si3N4 layer (~80 nm) on the Sio2 layer.

![image](https://user-images.githubusercontent.com/123365842/216801041-7228b9a2-bfee-4af4-9473-7d453aa25f4b.png)

Now we do patterning by using depositing photoresist and using Mask 1 through UV light.

![image](https://user-images.githubusercontent.com/123365842/216801054-3f394dd4-830e-4e05-a1cd-6e7e6ef9730d.png)

Now, first we remove the mask and doing etching of Si3N4 layer on the exposed area.

![image](https://user-images.githubusercontent.com/123365842/216801066-0a62c27b-3033-4215-91e0-87137dae1890.png)

Now, next step is to remove photoresist by chamical reaction, because now to Si3N4 layer itslef behaves like good protecting layer for Sio2 layer. now, if we do LOCOS (local oxidation of silicon) process, the exposed sio2 part will gown and bird break also form. This grown sio2 will provide the perfect isolation between two PMOS and NMOS.

![image](https://user-images.githubusercontent.com/123365842/216801074-63d9af36-8e11-4a35-941e-30cf5e7395c7.png)

Next step is to etchout the Si3N4 layer by hot phosphoric acid.

![image](https://user-images.githubusercontent.com/123365842/216801091-a242cdaa-8f43-4608-9df4-e0249df2d103.png)

# Formation of N-well and P-well
# 3) N-well and P-well formation

we can not form P-well and N-well at a same time. we have to protect a region while forming one of the region by photoresist. And then using mask 2 and UV light, we will do patterning of photoresist to form P-well.

![image](https://user-images.githubusercontent.com/123365842/216801116-4bf11ffd-7225-4f6c-a356-db00f0495449.png)

Now, the area where we want to form the P-well is exposed. now we remove the mask and by applying the ion implantaton method (~200kev)to form P-well using Boron. But still it is P implant. After performing the high temparature anneling, it will become P-well.

![image](https://user-images.githubusercontent.com/123365842/216801127-4350e3da-9a8f-4485-b405-28d88f530763.png)

We wiil do a similar process to form N-well by using mask 3 and using Phosphorus ions.

![image](https://user-images.githubusercontent.com/123365842/216801140-e36e0f3b-1598-4fb8-911e-29045b897494.png)

till now depth of wells are not define. so, by putting into the high temparature furnace (drive-in diffusion), we will define the depth of wells.

![image](https://user-images.githubusercontent.com/123365842/216801144-88f718b0-1fa6-4de4-b5e9-be01041d76f8.png)

# Formation of gate terminal
# 4)Gate formation

Gate terminal is the most important terminal of the PMOS and NMOS because from the gate terminal only we can control the thresold voltage. doping concentration and oxide capacitance will control the thresold voltage.

so, first we are maintain the doping concentration here. for that we use mask 4 and again doing the ion implantation of boron ion at lower energy (~60kev).

![image](https://user-images.githubusercontent.com/123365842/216801165-b4adfbe5-10b8-4632-a1c7-db982ec8c020.png)

same process we will repeat for N-well also by using mask 5 and Arsenic ion.

![image](https://user-images.githubusercontent.com/123365842/216801177-689c19b3-7046-4a61-b676-a71dee428cb8.png)

Next step is that we have to fix the oxide layer. but before that we have to remove the oxide layer because this layer is got dammeged because of the privious processes. so,first we remove the layer using HF solution and again re-grown the high quality oxide layer with same thickness.

The final step is the deposition of polysilicon layer over oxide layer with more impurities for low resistance gate terminal.Then etched out this polysilicon layer by using mask 6 and photoresist.

![image](https://user-images.githubusercontent.com/123365842/216801193-42b9d556-f7ea-46b8-9bfa-25e7773de4d4.png)

After etching, remove the photoresist and gate terminal looks like,

![image](https://user-images.githubusercontent.com/123365842/216801206-ad3031ad-e99d-45ab-b3fa-9009c6a67363.png)

Lightly doped drain (LDD) formation
5) LDD formation

Here, we actully want P+,P-,N doping profile in the PMOS and N+,N-,P doping profile for NMOS. Reason for that is

    Hot electron effect

    short channel effect

For the formation of LDD, we again do ion implantation in P-well by using mask 7 and here we use phosphoros as a ion for light doping.

![image](https://user-images.githubusercontent.com/123365842/216801218-27781e76-c7a2-4479-9129-5dbde9b84a22.png)

Same process we will repeat for N-well. there we use mask 8 and BOron Ion.

![image](https://user-images.githubusercontent.com/123365842/216801231-a0e6dc7e-f218-48ec-9d75-773f0f976404.png)

Now, by creating the spacers, we can protect the actual structre remain constant of P-implantt and N-implant. For that we deposite a thick Sio2 or Si3N4 layer over the gate tereminal.

![image](https://user-images.githubusercontent.com/123365842/216801242-0a2bd1d1-bbe6-499e-ba2a-e0708ccabff5.png)

Now, we do Plasma anisotropic etching. By that side-wall spacers are formed.

![image](https://user-images.githubusercontent.com/123365842/216801261-aa52c6df-8dc8-4cc2-9985-f1a747b0e152.png)

# Source and drain formation
# 6)source-drain formation

Next step is deposite the very thin screen oxide layer to avoid the effect of channeling.

![image](https://user-images.githubusercontent.com/123365842/216801271-8ca803d1-a4a6-4d50-8b76-38ef4ece53a5.png)

Now to form the drain and source, again we do the ion implantation of arsenic at 75kev to create the N+ implant by using mask 9 in the P-well to form PMOS.

![image](https://user-images.githubusercontent.com/123365842/216801284-33b83cb9-aeb8-4fcb-a95b-96cdd12b4d79.png)

Same process we will repeat for NMOS by using the mask 10 and boron ion in the N-well at 50kev to creat P- implant.

![image](https://user-images.githubusercontent.com/123365842/216801309-dc41ae69-bc44-4f81-b36f-5d83699d8db8.png)

Now we put this Half made CMOS into the high temparature (1000 degree)anneling. So P+ implant and N+ implant now become the source and drain.

![image](https://user-images.githubusercontent.com/123365842/216801320-81dd927a-900c-4252-a7c3-a7d7b5d1b0b3.png)

# Local interconnect formation
# 7)steps tp form contacts and local interconnects

First step is remove the thin screen oxide layer by etching. Then deposite the titanium (Ti) using sputtering. here Ti is used because Ti has very low resistivity.

![image](https://user-images.githubusercontent.com/123365842/216801343-3e7e1dfb-34b0-4ad9-a439-7005e3002b64.png)

Next step is to create the reaction between Ti layer and source, gate, drain of CMOS. For that wafer is heated at about 650-700 degree temparature in N2 ambient for about 60 seconds. and after reaction, we can see the titanium siliside over the wafer. One more reaction is heppend there between Ti and N. and it results the TIN which is used for local communication.

![image](https://user-images.githubusercontent.com/123365842/216801373-71b7fd8e-2ed4-40c3-8a20-d69e552534bb.png)

Now by using mask 11 and photoresist, we will etched out the TIN and make perticular contacts. TIN is etched out by using RCA cleaning.

![image](https://user-images.githubusercontent.com/123365842/216801391-2e47aaab-f432-456b-a029-0451ab892193.png)

Now, local interconnects are formed after etching and removing the photoresist.

![image](https://user-images.githubusercontent.com/123365842/216801405-48c6b1dc-ecd3-4823-aeb5-f1fc3d3957a4.png)

# Higher level metal formation
# 8)Higher level metal formation

These steps are very semilar like previous steps. First thing that we are noticing is that the surface is non planner. it is not good to use this type of non planner serface for matel interconnects because of the problems regarding the metal disconinuty. so, we have to plannerize the surface by depositing the thick layer of sio2 with some impurity to make less resistive layer. and then we used CMP (chemical mechanical polishing) technique to plannerise the surface.

![image](https://user-images.githubusercontent.com/123365842/216801424-9231ac66-d8d5-478f-af5d-889c863bc5cf.png)

Now using mask 12 and photorsist we etched the sio2 layer to diposite the metal in it.

![image](https://user-images.githubusercontent.com/123365842/216801452-7fc41b3b-fee2-4063-bcf1-344d59e509de.png)

Now remove the photoresist and seposite the thin later of TIN (~10nm) over the wafer. Because TiN is act as very good adession layer for sio2 and also act as a barrier between bottom layer and top layer of metal interconnects.

![image](https://user-images.githubusercontent.com/123365842/216801463-631060c0-a041-47b6-9abc-5fdb14009f29.png)

Next step is to deposite the blanket tungsten (W) layer over the wafer. and then do the CMP here to plannerize the surface.

![image](https://user-images.githubusercontent.com/123365842/216801476-45be0608-b200-493e-84d5-66774ccb1a09.png)

This W is act as a contact holes and this holes needs to connect to the Higher metal layer. so we will deposite the Al (aluminium) layer.

![image](https://user-images.githubusercontent.com/123365842/216801489-0fa130c0-c0a9-4474-80a4-02f03c63560f.png)

Then by using the mask 13 and photoresist, we etched the W layer out to form the contact at perticular place by Plasma etching.

![image](https://user-images.githubusercontent.com/123365842/216801512-8e64770f-39cc-4ced-bcb1-a23dce2be713.png)

This is our first level of metal interconnets. now we again do the same process as above to deposite the second level of metal interconnect by using mask 14 for etched out the sio2 and using mask 15 for etched out Al leyer.

![image](https://user-images.githubusercontent.com/123365842/216801520-fea71fdc-0bec-4bc0-a59e-97cec573ace1.png)

The upper layer of Al is bit thicker as compared to lower layer of Al.Now, again deposite the layer of sio2 or si3N4 to protect the chip.

![image](https://user-images.githubusercontent.com/123365842/216801531-1c88ee7e-9511-41e9-8816-41b85b69c84f.png)

And finally our CMOS is looks like this after the fabrication.

![image](https://user-images.githubusercontent.com/123365842/216801555-cf81ce94-0c55-42a4-8318-2c86f0741e90.png)

# Lab introduction to Sky130 basic layer layout and LEF using inverter

![image](https://user-images.githubusercontent.com/123365842/216801570-3b208eda-3ae9-4a14-8590-94654b059361.png)

In sky130, every color is showing the different layer. here the firsst layer is for local interconnect shown by blue_perpel color, then second layer is metal 1 which is showm by light perple color, and the metal 2 is shown by pink color. N-well is showm by solide das line. green is N-diffusion region. and red is for polysilicon gate. similarly the brown color is for P-diffusion.

In tckon window, we can see that the selected area is NMOS and similarly we can chech PMOS also. and that is how we can check that the CMOS is working or not.

![image](https://user-images.githubusercontent.com/123365842/216801590-d4e731a7-bb36-48e1-a9b5-5c022661de8a.png)

semilarly we check for the output terminal also.(by double pressing "S" to select the entire thing at output Y).

![image](https://user-images.githubusercontent.com/123365842/216801610-a09bad56-d35b-47ad-b990-0401f0d9aeed.png)

so, we can see that "Y" is attached to locali in cell def sky130_inv.

we can check the source of the PMOS is connected to the ground or not. and similarly we can check it for NMOS also.

# Lab steps to create std cell layout and extract spice netlist

To extract the file from here, we have to write the command in tckon window. and the comand is "extract all".

![image](https://user-images.githubusercontent.com/123365842/216801671-a532d508-b816-409a-a2d6-0a6004f270d3.png)

Now let's go to this location from the terminal. it is exctracted.

![image](https://user-images.githubusercontent.com/123365842/216801636-f9ab9ee6-f049-49d9-8bb7-d2979224d6e1.png)

we will use this .ext file to create the spice file to be use with our ngspice tool. for that we have apply the comand "ext2spice cthresh 0 rthresh 0". this will not create anything new. now again we have to type "ext2spice" comand in tckon window.

![image](https://user-images.githubusercontent.com/123365842/216801698-8426a705-a3f0-4b8c-9ea5-a5977a416633.png)

so, now we are checking the location and at there spice file has been created.

![image](https://user-images.githubusercontent.com/123365842/216801723-af4d7fc2-a772-40e0-a4ef-1966926bb799.png)

let's see what inside the spice file by "vim sky130_inv.spice".

![image](https://user-images.githubusercontent.com/123365842/216801741-10d62522-a9ed-4115-8a00-25c6a4284f9c.png)

# Sky130 Tech File labs
# Lab steps to create final SPICE dexk using sky130 tech.

![image](https://user-images.githubusercontent.com/123365842/216801793-b6fcc45a-bb78-432f-ab7d-78a02437ee05.png)

here, we can see the all details about the connectivity of the NMOS and PMOS and about the power supply also.

X0 is NMOS and X1 is PMOS and both's connectivity is shown as GATE DRAIN SUBSTATE SOURCE.

But here the scale is 10000 um. but in Magic simulation, it is 0.01.

![image](https://user-images.githubusercontent.com/123365842/216801858-5794b6b5-14be-4cbc-bea9-b7e96391818b.png)

SO, we are going to change the dimension here in the terminal. so any measurement will be in this scale of 0.01u. i.e., width=37*0.01u.

Now we have to include the PMOS and NMOS lib files. it is inside the libs folder in the vsdstdcellsdesign folder.

![image](https://user-images.githubusercontent.com/123365842/216801954-6f8ea586-f878-44e9-84f6-569f81952a29.png)

so, now we include this file in the terminal by ".include ./libs/pshort.lib" and ".include ./libs/nshort.lib" comand.

And then set the supply voltage "VDD" to 3.3v by "VDD VPWR 0 3.3V" comand. and similarly set the value of VSS also.

Now, we need to specify the input files. by Va A VGND PULSE(0V 3.3V 0 0.1ns 2ns 4ns).

Also add the comand for the analysis like, ".tran 1n 20n", ".control" , "run",".endc",".end".

![image](https://user-images.githubusercontent.com/123365842/216802039-56e5d79f-199b-4ba1-81d8-c95f99eac779.png)

after running this file we get output of ngspice like this,

![image](https://user-images.githubusercontent.com/123365842/216802050-95064714-b44b-4635-96d6-d1b8b55afcfc.png)

Now, ploting the graph here by comand, "plot y vs time a".

![image](https://user-images.githubusercontent.com/123365842/216802089-81cd80c1-cc44-419e-8189-51c695d3b009.png)

# Lab steps to characterize inverter using sky130 model file

Here, we have to find value of 4 parameters.

    rise time

it is time taken to the output waveform to 20% value to 80% value.

![image](https://user-images.githubusercontent.com/123365842/216802120-d1cb1545-41c4-4428-a6f9-a1603f6ee345.png)

so, rise time= (2.20374-2.16038)e-09 = 0.04336 nsec.


    fall time

it is the time take by output for transition from 80% to 20%.

![image](https://user-images.githubusercontent.com/123365842/216802150-04c55410-9032-4a22-94d2-778f991ecc0f.png)

fall time= (4.0684-4.03037)e-09 = 0.03803 nsec.

Propagation delay

![image](https://user-images.githubusercontent.com/123365842/216803062-2a927335-d535-433a-be4e-e01d5b444b0f.png)

Propogation delay = (2. 18458-2. 18411)e-09 = 0.00047 nsec.

Cell Fall Delay

![image](https://user-images.githubusercontent.com/123365842/216803072-87c40e86-e974-4fc9-a27e-bd63ca9d30f8.png)

Cell fall delay = (4.05374-4.05234)e-09 = 0.0014 nsec.

# Day 4 -Pre-layout timing analysis and importance of good clock tree
# Timing modelling using delay tables
# Lab steps to convert grid info to track info

Till now we have done synthesis, floorplaning, placement and how to extract the spice out of it, done charecterization of it. till now, for placement and routing, we doesn't required any information about input/output port,logic path, power, ground.

Now the concept of 'lef' file will comes into the picture. it contains all the information which we discuss earlier. so our next objective is to extract the '.lef' file out of the '.mag' file. and next step is that extracted file could be placed into the picorv32a flow.

you need to folow certain guideline while making standerd cells.the guidelines are

    The input and output port must lie on the intersection of the verticle and horizontal tracks

    The width of the satnderd cell should be odd multiple of the track pitch and the height should be odd multiple of track verticle pitch

Now oprning the track file from the pdk/sky130/libs.tech /openlane/sky130_fd_sc_hd/track.info. where we get the info like this,

![image](https://user-images.githubusercontent.com/123365842/216803115-1c0446d7-9d6f-4f04-9145-ca4ae9d4d909.png)

so, the track is basically nothing but it is used during the routing stage.Rout will be go over the tracks. tracks are basically trases of matel layers.i.e., metal 1, matel 2, etc.

PNR is a automated. so we need to specified, where from we want routs to go. this specification is given by tracks. here we can see that each of the tracks are placed at (0.23 0.46)um horizontaly and (0.17 0.34)um vertically for li1, metal 1, metal 2 layer.

In layout, we can see that the ports are on the li1 layer. so we need to insure that the ports are on the intersection of the tracks or not. For that we have to cinvert the grid into the tracks. for that we have to first into the tracks file and the open the tckon window and type the "help grid" comand.

![image](https://user-images.githubusercontent.com/123365842/216803148-e10d226d-cb2b-4894-bdcf-bcb9aa4ea509.png)

Then again write comand according to the track file.

![image](https://user-images.githubusercontent.com/123365842/216803184-e3028916-3e03-4ad1-8b05-7f6665fcc033.png)

Let's see the changes in the layout.

![image](https://user-images.githubusercontent.com/123365842/216803222-d0b7a3c6-f77d-45b3-b034-e3f53e7f4ea6.png)

Here we can see that, as per the guideline the ports are placed at the intersection of the tracks.

now, between the boundaries, there is 3 boxes are coverd. so our second requirment also satisfied here.
Lab steps to convert magic layout to std cell LEF

here already the port name and the port definationa is seted, if not seted the we have to set the definanation and the name of the port.

As it parameters are set, we are ready to extract the 'LEF' file from the "mag" file. but before the extraction, let give the name to the cell by using tckon window.

Now we can see this file in the vsdstdcellsdesign folder.

![image](https://user-images.githubusercontent.com/123365842/216803238-a2def234-8928-4463-9199-cd36769034aa.png)

Now, we open this file in the magic by using comand "magic -T sky130A.tech sky130_vsdinv.mag &".

Now to extract the lef file we have to write the comand in the tckon window "lef write". so it will create a lef file and we can check it in the vsdstdcellsdesign folder.

![image](https://user-images.githubusercontent.com/123365842/216859287-641c5a78-4235-4c8f-8407-0c5a1756953e.png)

Now, lef file is created and now next step is plug this lef file in picorv32a. before that we move our files to src folder where all the design files are available at one location.

for that we are copiying this file in the src folder by 'cp' comand.
Introduction to timing libs and steps to include new cell synthesis

The basic idea is that we have to include our custom cell into openlane flow. and the first stage in the openlane is the synthesis.

here, also we required library. so we copiying the library to the src folder.

Before we do anything, we have to modified our congig.tcl file. so opening this file by "vim" comand and modifiying it.

Now, start the new terminal and open the openlane by docker, make flow interactive and then add the package and then prep design with the privios run by the comand " prep -design pecorv32a -tag [last running time i.e.27-01_17-53] -overwrite".

Now comes the deciding part. we have to see that the synthesis run and its maps our custom vsd inveter into this flow. so, run the synthesis.
Introduction to delay tables
Power Aware CTS

If we make enable pin at logic '1' in the AND gate, the clock will propogatee to the AND gate. similarly, if we make enable pin at logic '0' in the OR gate, here also clock propogate to the OR gate.

Similarly if we make enable pin at logic 'o' in the AND gate, gate will block the clock and same this will happend with the OR gate if we make enable pin at logic '1'.

The advantage of this scenario is that, during this time period of the blocking the clocks, we can save lots of power in the clock tree. now the question is that how can we use this scenario in the clock tree.

let say we have a clocktree like this given below,

![image](https://user-images.githubusercontent.com/123365842/216803361-351419eb-b52c-43e5-8e1c-7e4f82fdcf6c.png)

Here we spitted the load of the 4 FF into the 2 buffers and the load of the 2 buffers is given to the level 1 buffer. here assumptions are,

    Assume c1=c2=c3=c4=25fF

    Assume Cbuf1=Cbuf2=30fF

    Total Cap at node 'A'=> 60fF

    Total Cap at node 'B'=> 50fF

    Total Cap at node 'C'=> 50fF

We have done some observations here,

    2 levels of buffering

    At every level,each node driving same load

    Identical buffer at same level

so, here capacitance at the every node of the clock tree is not the same. it is varying. Now load is varying then input transition is also verying because the output load at the level 1 buffer is the input of the other buffers of level 2. so, we have variety of the delays. To capture it, we have delay tables.
How delay tables are prepared?

To prepare the delay table, the perticukar element is taken out of the circuit and saparetly verying the input transition and output load and according to the variation, we will charactorize the delay of the element and make the delay table frpm it.

![image](https://user-images.githubusercontent.com/123365842/216803380-d9290f5b-8f6e-4d7e-9131-0dcf54db9bc8.png)

# Delay table usage part 1

Let's looks into the sample examples and making the table for Cbuf'1' and Cbuf'2',

![image](https://user-images.githubusercontent.com/123365842/216803398-ef655a5d-4cd5-496f-b555-ba56ae00a302.png)

let's take practical example on the circuit. we take 40psec as input transition on the level 1 buffer and as per assumption load is around 60fF. and delay is comes between x9 and x10. lets take x9' as the delay of the buffer of level 1.

# Delay table usage part 2

Next step is to calculate the delay of the buffers of level 2. And after that we can find the letancy at the 4 clock end points.

now input transition is common for both the buffers. now assuming that the transition is around the 60psec and load at both the buffers is 50fF. so it will give the delay of y15.

The total delay from input to the output is= x9' + y15.(here we are ignoring the delay of the wires). that means the skew at the any output point is zero.

If load is not same at the every nodes, the skew will not be the zero.
# Lab steps to configure synthesis settings to fix slack and include vsdinv

After synthesis, we observed that the slack is nagative here. wns(worst negative slack)= -24.89 and tns(total negative slack)= -759.

![image](https://user-images.githubusercontent.com/123365842/216803450-ba4dcad8-f8d8-4cf8-b26f-51830bfe46e2.png)

let's do some modification here. for that opening the READme file from the /openlane/configuration/ less READme.md

Now lets try to make balance between area and the delay of the synthesis by changing the stratagy. comand for checking the current strategy is "echo $::env(SYNTH_STRATEGY)", and comand for changing the stategy is "set ::env(SYMTH_STRATEGY) 1". by doing this area will increase the little but but timing will improve.

Then checking the synth_bufferung and synth_sizing. if any one them is off then make it on by set the value of it by 1.

Till here we not get slack 0. to make slack 0, we ahve to write comand "set ::env(SYMTH_STRATEGY) DELAY 0"

After running synthesis we will get improved timing.

![image](https://user-images.githubusercontent.com/123365842/216840224-aa6ad34d-322c-4eb3-9027-07f32a3419be.png)

Next command for run is :

set lefs [glob $::env(DESIGN_DIR)/src/*.lef]

add_lefs -src $lefs

Then again run the synthesis.
Timing analysis with ideal clocks using openSTA
Setup timing analysis and introduction to flip-flop setup time
Timing analysis (with ideal clock)

we start with taking the ideal clock and we will do timing analysis for the ideal clock first.

Let's start the setup analysis with the ideal clock(single clock). specifications of the clock is

    clock frequency =1 GHz

    clock period =1 nsec

Let's take lainch Flop and Capture flop with clock. here clock tree is not built yet. so it is ideal scenario. here we have to do analysis between '0' and 'T'. with that assume that the delay of logic is 'θ'.

![image](https://user-images.githubusercontent.com/123365842/216803594-ed5d041c-51c9-4923-a33c-948d7a03e052.png)

Setup timing analysis says that θ<T. this condition should be neccessory for the the comninational logic work.

Now let's introduce the practical scenario here. Opening the capture flop and it has two mux inside it.

![image](https://user-images.githubusercontent.com/123365842/216803607-c010b7c6-327c-4f6f-9efb-9e41064495b5.png)

The way flop work, it will shown by the timing graph like this,

![image](https://user-images.githubusercontent.com/123365842/216803620-75f96664-9777-49cf-ac82-4ca39f214fd9.png)

So, here mux 1 and mux 2 both have their own delay. these delay will restrict the combination delay to the requirment.

Hence finite time 's' required before clk edge for 'D' to reach Qm.

So, we can write that the internal delay of the MUX1 = set up time(S).

So, now θ<T becomes θ<(T-S).
Introduction to clock jitter and uncertainty

Let's bring one more practical scenario here. clock is taking from the some clock source or PLL. So, because of some delay from the practical source of clock or PLL, clock pulse will not comes exacly at t=0 or at t=T. that in built variation of the clock is called jitter.

![image](https://user-images.githubusercontent.com/123365842/216803631-ab68c6af-73ee-40cd-bbdf-88432e3a1d91.png)

lets consider this uncertantity time(US) in consideration. So, now equation becomes like, θ<(T-S-US). Now assuming that 'S'=0.01ns and 'US'=0.09ns. by taking that, lets identify the timing path for our existing scenario. in our circuit stage 1 and stage 3 logic path has single clock.

NOw, what we have to do is identify the combinational path delay for the given both logics.

![image](https://user-images.githubusercontent.com/123365842/216803642-8a8065a7-b991-454f-b0f1-3cc8038fed4d.png)

![image](https://user-images.githubusercontent.com/123365842/216803646-cccc3157-6808-4ef7-8e84-99ef1383cbc4.png)

# Lab steps to configure OpenSTA for post-synth timing analysis.

when we do CTS, CTS is a stage where, we add clock buffers along with clockpath and build the clock tree. so, actually we are changing the netlist. Along the running CTS, actually the netlist file also created. so, after running the CTS, we will see the new Verilog file here.

Now, we see what is in the my_base.sdc file. 

![image](https://user-images.githubusercontent.com/123365842/216840088-9f3750ec-ecb4-4106-8ae3-4c91d33ae970.png)

here, we can see the capacitor load and clock period and clock port etc.

Now, to reduce the fanout we use the command is : "set ::env(SYNTH_MAX_FANOUT) 4" and then run the synthesis.

but here also slack doesn't reduce.

Now next step is run floorplan, place IO, do global placement or detail placement and genrate pdn file the run the cts by following comands.

inut_floorplan

place_io

global_placement_or

detailed_placement

tap_decap_or

detailed_placement

After running the floorplaning and done the global placement we get positive slack.

![image](https://user-images.githubusercontent.com/123365842/216839988-a1e95dc7-d784-48ec-b43e-f6faddaee964.png)

Write the command is:magic -T /home/kunalg123/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

![image](https://user-images.githubusercontent.com/123365842/216840007-de38e7a6-567e-4c9e-b75e-173cd4336207.png)

Clock tree synthesis TritonCTS and signal integrity
Clock tree routing and buffering uisng H-Tree algorithm
what is clock tree synthesis?

As shown in below, figure, let's connect clk1 to FF1 & FF2 of stage 1 and FF1 of stage 3 and FF2 of stage 4 with out any rules.

![image](https://user-images.githubusercontent.com/123365842/216803806-9992ec0f-2540-4423-90e8-b9f5bdb2e549.png)

Now, let's see the problem with this clock Rout. let us say time required to reach the FF1 and FF2 of stage 1 are t1 and t2 for clock1. so, we can say that t2-t1= skew (ideally skew=o).

![image](https://user-images.githubusercontent.com/123365842/216803824-e3dcaf72-6beb-42cd-814d-08819d518865.png)

To make, skew to be 0, this rout definatly not help. so, we can say that what we built the tree is "BAD TREE". so, the concept of H-tree comes out. with the Mid point strategy, H-tree form.

![image](https://user-images.githubusercontent.com/123365842/216803837-e435d92d-73d9-409b-9cde-d21f22ed8efd.png)

Next thing is clock tree synthesis (buffering).as we see in the clockk tree and we observed that clock has to travel through all wires and it will charge all capacitor which are comming in the path of this wire.

The problem occurse due to the charging the capacitor is signal inntigrity problem because of transition of signals. solution of this problem is add the repeaters here. the repaters are the similar as what we use in the data path but the main difference is, here repeater has equal rise and fall time.

![image](https://user-images.githubusercontent.com/123365842/216803853-eb062cb7-4b21-4ebf-bda3-6a61e746dc15.png)

Crosstalk and clock net shielding

We build the clock tree in a manners that the skew becomes zero between launch Flop and capture flop. but if accedently any crosstalk heppense then everything what we had design is detoriated.

Let take the first clock net and protect it by shielding. here we protect the clock network from outside world. if the protection is not there then problems like glitch and delta delay is heppens.

The glitch is heppence because of Coupling capacitance between the wires.

![image](https://user-images.githubusercontent.com/123365842/216803863-255ee0a2-f013-4fb5-8050-9ab39fd64bb7.png)

The shielding is the technique, by which we can protect the net from these problems. In a shielding, we put wire between the other teo wire where coupling capacitance is generate. This extra wire is grounded or connected to VDD.

Now, let's see about the delta delay.

![image](https://user-images.githubusercontent.com/123365842/216803874-2a0ef12e-5c1f-4244-a0a9-ba5a4db504cb.png)

# Lab step to run CTS using TritonCTS

Now next step is CTS. for that write the command: "run_cts".

![image](https://user-images.githubusercontent.com/123365842/216839269-36c9cdb2-e38e-42fb-8f2c-89ec9c0e3f4c.png)

In CTS stage the buggers are added in the paths. so, it will modifiying the netlist. so, if we go in the synthesis folfer and check the files, where cts.v file will avaiilable and this file contains the added buffers.

# Lab steps to verify CTS runs

we have run CTS.Now before we goes into the post cts flow, we need to know that the actual meaning of the "run" command. This is the proc of tcl file. so, lets see, from where, openlane take this procs. for that we need to goes into the openlane and then goes into scripts and then check the "tcl_commands". in this file tcl commands are there for every stages what we have run till now. so let's see the "cts.tcl" file.

![image](https://user-images.githubusercontent.com/123365842/216839792-ed28336e-054c-415e-a29f-8718d350c8a4.png)

here we can see the many procs are there. so here we can see the procs are run during the CTS run.

![image](https://user-images.githubusercontent.com/123365842/216839389-94498366-f0b4-41e9-aee0-968734b5b3ae.png)

so when we run the cts in the flow, basically it do this things.

first it run the tritonCTS by givin total information.

then it set the value of timer.

Then it goes for open the openroad.

if we check the openroad folder, at that directory "or.files" are available which was runs in the OPENROAD EDA tool.

Now les's check the "or_cts.tcl" file. inside this we can see the few switches.

![image](https://user-images.githubusercontent.com/123365842/216839486-044849cd-ae6f-4d93-8e8c-b7dd4fe130b2.png)

Now lets check what the library does. For this command is "echo ::env(LIB_TYPICAL)"

Now checking the clock period of this by command: "echo $::env(SYNTH_MAX_TRAN)"

So, clock period seted as 2.473 nsec.

Then checking the max cap value, by command : "echo $::env(CTS_MAX_CAP)". and it is setted as 1.53169

Now checking the branch buffer cells by command :"echo $::env(CTS_CLK_BUFFER_LIST)". and these are the buffer cells are listed there "sky130_fd_sc_hd__clkbuf_1 sky130_fd_sc_hd__clkbuf_2 sky130_fd_sc_hd__clkbuf_4 sky130_fd_sc_hd__clkbuf_8".

And last cheching the root buffer by command: "echo $::env(CTS_ROOT_BUFFER)". So, we find that this "sky130_fd_sc_hd__clkbuf_16 " buffer is root buffer.

![image](https://user-images.githubusercontent.com/123365842/216838943-04bace41-09f3-44a2-9ff8-d8e2a481c6e8.png)

# Timing analysis with real clocks using openSTA
# Setup timing analysis using real clocks

With real clock, circuit looks littel bit different then ideal clock. Here the bufferes and wires are added to the circuts.

Here, due to buffer, clock signals are not reaching the flop at t=0. it will reach at t=0+(delay of buffer 1 and 2).Now equation change to (θ+1+2)<(T+1+3+4).

![image](https://user-images.githubusercontent.com/123365842/216804079-300b0560-1db8-4735-a1bc-7c247b92a98b.png)

Let's called "1+2"=∆1 and "1+3+4"=∆2 and (∆1-∆2)=skew

![image](https://user-images.githubusercontent.com/123365842/216804106-38613228-f899-49ea-80e6-8e2862aef311.png)

And here also, we have to consider the propogation skew (s) and uncertainty delay (US). so final equaltion becomes like, (θ+∆1)<(T+∆2-S-US).

we can also say that (θ+∆1)= data arrival time and (T+∆2-S-US)=data required time.
If (Data required time)- (Data arrival time) = +ve then it is fine. If it is -Ve then it is called 'slack'.
Hold timing analysis

It is littel bit different then setup timing analysis. here we are sending the first pulse to the both launch FLop and capture flop.

Hold condition state that, Hold time (H)< combinational delay (θ). So, (θ>H).

![image](https://user-images.githubusercontent.com/123365842/216804126-75940eeb-3eae-4d77-823e-eb5dc5bc6448.png)

Hence, finite time 'H' required for 'Qm' to reach Q i.e., internal delay of mux2= hold time.

Now, if we add the real time clock, the equation will be change. now equation becomes (θ+∆1)>(H+∆2).

![image](https://user-images.githubusercontent.com/123365842/216804143-64867df3-d056-4889-9081-d7a2e73fe470.png)

# Hold time analysis with real clock

Now here also adding the Unsetainty delay(UH) value due to jitter. so, equation becomes like, (θ+∆1)>(H+∆2+UH).

we can also say that (θ+∆1)= data arrival time and (H+∆2+UH)=data required time.

If (Data arrival time) -(Data required time)= +ve then it is fine. If it is -Ve then it is called 'slack'.

Now, applying all these things in out network.

![image](https://user-images.githubusercontent.com/123365842/216804156-9ade4f90-c8d6-44df-b67e-c250db31cab4.png)

Lab steps to analyze timing with real clock using OpenSTA

let's open the OPENROAD tool in the flow by "openroad" command.

our objective is to do analysis of the clock tree.

we are analysin this in the OpenROAD because OpenSTA is already built in the OpenROAD. In OpenROAD the timing analysis is done in a different way. first we have to create "db" and "db" is created in a "lef" and "def" file.

Now let's create the DB. To create the DB, first we have to read the lrf file by comand "% read_lef /openLANE_flow/designs/picorv32a/runs/29-01_22-23/tmp/merged.lef".

Then we read the "def" file by command: "read_def /openLANE_flow/designs/picorv32a/runs/29-01_22-23/results/cts/picorv32a.cts.def".

NOw to create the DB write the command "write_db pico_cts.db"

NOW read this db file by command "read_db pico_cts.db"

then read the verilog file by applying the command "read_verilog /openLANE_flow/designs/picorv32a/runs/29-01_22-23/results/synthesis/picorv32a.synthesis_cts.v"

then read the library (max) by this command:"read_liberty -max $::env(LIB_FASTEST)".

similarly read the library (min) by this command: "read_liberty -min $::env(LIB_SLOWEST)".

Now read the sdc file by this command: "read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc"

now set the clocks by this command:"set_propagated_clock [all_clocks]"

there reports the checks by this

command: "report_checks -path_delay min_max -format full_clock_expanded -digits 4".

so after running this we can see that the slack is positive for hold and setup both. and also we can notice the data required time and data arroval time also.

So, the Hold slack = 1.4776nsec because here we can see that (arrivel time) >(required time).

![image](https://user-images.githubusercontent.com/123365842/216839090-73f8a6d4-5781-4e8f-a161-f8e9a8660bcf.png)

# Lab steps to execute openSTA with right timing libraries and CTS assignment

TritonCTS is right now built according to optimize fully according to one corner and we had bulid the clock tree for typical corner. and library also min and max. so we made tree according to typical corner but we analize it according to one corner. so, analysis become incorrect.

so, first we exits from the openroad by using "exit" command and we have to include the typical library for typical analysis. for that we have to open the "openroad" again and add this typical library. now we don't need to add lef and def file here. now commands for the adding a file is:

read_db pico_cts.db

read_verilog /openLANE_flow/designs/picorv32a/runs/29-01_22-23/results/synthesis/picorv32a.synthesis_cts.v

read_liberty $::env(LIB_SYNTH_COMPLETE)

link_design picorv32a

read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

set_propagated_clock [all_clocks]

report_checks -path_delay min_max -format full_clock_expanded -digits 4

slack for typical coirner= 0.1075nsec

![image](https://user-images.githubusercontent.com/123365842/216839124-f70f3538-67e0-40f7-993e-1f60f2bfce69.png)

Now checking the branch buffer cells by command :"echo $::env(CTS_CLK_BUFFER_LIST)". and these are the buffer cells are listed there "sky130_fd_sc_hd__clkbuf_1 sky130_fd_sc_hd__clkbuf_2 sky130_fd_sc_hd__clkbuf_4 sky130_fd_sc_hd__clkbuf_8".

when openlane are making the CTS, at that time this buffers are place in the clock path to meet the skew value. and we always want skew value is maximum to the 10% of clock period.


# Day 5 -Final steps to build power distribution network
# Routing and design rule check(DRC)
# Introduction to Maze Routing A lee As Algorithm

Final stage in the physical design is the routing and DRC stage.

Routing. by the name it is says that rout means make physical contact between Din1 and FF1 od stage 1. but algorithm wise,it understand that Din1 is the source and FF1 input pin is the target. so, algorthm has to find the best possible solution to connect the Din1 and FF1.

For that we use Maze Routing and Lee's algorithm. let's try to connect Block 1 and block 2 of stage 3. there are varies mathod to connect these blocks but we need best solution for the rout or connection. To understand that, we remove all other things.

Algorithm create the routing gird at backend. here algirithm create two points. one is source and other is target. Now by using this routing grid, algorithm find the best way of routing. algorithm marks the adgecent grids of source. similarly again it will find the adgecent grids of the previos grids.similarly this process will runs continuosly.

![image](https://user-images.githubusercontent.com/123365842/216804273-c81caa8b-c544-401b-979e-9e6b1964e104.png)

# lee's algorithm conclusion.

The extanding process of adgecent grids are contionuous till it reaches to the target

![image](https://user-images.githubusercontent.com/123365842/216804322-e2cce4de-2142-4cfd-90a2-037c6c97b2b6.png)

there is many ways to reach the target. but the best possible way is 'L' shaped way.

![image](https://user-images.githubusercontent.com/123365842/216804330-5c47d33f-ee80-4f63-bf9f-51fc243de086.png)

lets take another example for this routing.

![image](https://user-images.githubusercontent.com/123365842/216804343-3aaa8b39-7dbb-4cf9-8c7a-a96cbdf42f0f.png)

Now, we reouted all the blocks and the circuits looks like this,

![image](https://user-images.githubusercontent.com/123365842/216804352-1e0d5323-2664-474f-8ccb-509c44af8fbd.png)

# DRC(Design Rule check)

While doing the routing, we need to follow certain rules for that. this is called DRC cleaning.

Lets take two parallel wires from the circuit for example,

![image](https://user-images.githubusercontent.com/123365842/216804365-8faf1481-851a-4e7b-a2ca-b0985c1f4419.png)


    Rule 1

Width of the wire should be minimum that derived from the optical wavelenth of lithography technique applied.
![image](https://user-images.githubusercontent.com/123365842/216804380-ca2b8fcb-8f25-4d92-8d66-c27b82784210.png)

    Rule 2
    
The minimum pitch between two wire shold be this much.

![image](https://user-images.githubusercontent.com/123365842/216804419-a58adfc0-1381-45e8-bc15-68014000aa73.png)

    Rule 3

The wire spacing between two wires should be this much. 

![image](https://user-images.githubusercontent.com/123365842/216804436-362e54cb-87c7-4f0b-ab57-5d689c6c9fe1.png)

Let's take other part for understand the rules. basic problem in this types of wire is the signal short.

![image](https://user-images.githubusercontent.com/123365842/216804455-adffda41-41eb-45ee-b367-9b5f5dbc021d.png)

Solution of this signal short problem is take one of the wire and put it on the other metal layer. usually upper metal is wider than the lower metal.

![image](https://user-images.githubusercontent.com/123365842/216804475-466c3190-6631-4242-8aba-c68c859cf470.png)

After this solution, we add two new DRC rules should be check.

    Rule 1

via width should be some minimum value. 

![image](https://user-images.githubusercontent.com/123365842/216804494-986c41b7-1457-4161-8aff-6d22839cbb41.png)


    Rule 2

Via spacing should be minimum this. 
![image](https://user-images.githubusercontent.com/123365842/216804522-06c68b6c-b423-4996-868f-863280dd9713.png)

Next step is paracitic Extraction. so, the wire will get some resistance and capacitance value.

![image](https://user-images.githubusercontent.com/123365842/216804540-df30c67a-66de-46ba-913b-b07f9c2dfce7.png)

# Power distribution network and routing
# Leb steps to build power distribution network

IS in case, our terminal is delected by some cause, the if we want the previos terminal once again then this steps should be followed:

    docker

    ./flow.tcl -interactive

    package require openlane 0.9

    prep -design picorv32a -tag [run file name i.e., 20-01_22-23]

Now to check the which was the last stage we perorm, the command is:"echo $::env(CURRENT_DEF)".

So, till now we have done CTS and now we are going to do the routing. but before routing we have to generate the PDN(power distribution network)file. for that command is: "gen_pdn".

![image](https://user-images.githubusercontent.com/123365842/216838414-2dec05cd-da9f-403d-8981-4411a0ca39fc.png)

Here we can see the total number of nodes on the net VGND and it is also says that Grid matrix is created successfully. here total connection between all PDN nodes establish in the net VGND.

Now, till here we have picorv32a chip, and it needs the power. so it will get power from VDD and GND pads. From the pads, power goes to the tracks and from the tracks, the cells get power.

# Lab steps from power straps to standerd cell power

To understan this, take an example here,

![image](https://user-images.githubusercontent.com/123365842/216838375-46071a94-0908-434a-99be-1398736bc4c5.png)

In this figure, the green box is available is let say picorv32a chip. And the yellow, red and blue boxes which are the shown on the outside of the frame are the I/O pins and the power and ground pads. in this pads, the corner ones are called corner pads.

Red pads are the power pads and Blue pads are ground pads.

Power is transfered to the rings from the pads through Via which is shown by black dots on the cross section points of the ring and pads.

Now we need to insure that the power is transfered from the ring to the chip. for that we have vertiocal and horizontal tracks which are also shown by the red and blue color.

NOw, we need to supply power to the standerd cell (Which are shown by rectangular white boxes) from these tracks. this is done by horizontal small connections shown in the figure.

So, in a lab we have done this all the things till power distribution.

Now next and the final step is routing.

# Basic and Global detailed routing and configure TritonRoute

Now current def.file is change to pdn.def from the cts.def. pdn.def file is now in the "runs/29-01_22-23/tem/floorplan/pdn.def".

In the routing process we are focusing on the routing strategy. there are 5 routing strategies are there. 0,1,2,3 and 14. routing is done in the TritonRoute engine. we have to specifies the strategy for the routing. for example if we ser the strategy to 14 then "TritonRoute14" strategy is used.

If we set the TritonRouting strategy to "0" then it want converge to a 0 TRC routing. but because of this we will improve in the memory requirement and run time. if we use TritonRoute14 then the run time will be approximate 1 hours. but in the TritonRoute0 it will be around the 30 minutes. here we use the "TritonRoute0". so in our flow first we check the routing strategy by the command "echo $::env(ROUTING_STRATEGY)". if it is "0" then it is fine, otherwise we have to change the strategy to "0".

Now the last thing remains is routing. for that command is :"run_routing".

The routing process is very complex.So, total routing is devided into two part.

    Fast route (Global route)

    Detailed route

![image](https://user-images.githubusercontent.com/123365842/216804613-2a84f3b2-caad-4066-8b9a-163ccf24c48d.png)

In the Global route, the routing region is devided into the rectangular grids cells as shown in the figure. and it is represented as 3D routing graph. Global route is done by FAST route engine.The detailed route is done by TritonRoute engine.

As shown in the figure, A,B,C,D are four pins which we want to connects through routing. and this whole image of A,B,C,D show the nets.

Now, the routing is successfully done.

![image](https://user-images.githubusercontent.com/123365842/216838203-58c360dc-3184-4223-bb91-6253318a7f56.png)

# Tritinroute features
# TritonRoute feature 1 -Honors pre-processed route guid

![image](https://user-images.githubusercontent.com/123365842/216804638-04daa0ee-115e-4b06-9ed6-437e0b11f1bf.png)


    It performs initial detail route.

    It attempts as much as possible to route within route guides.

requierment of processed guides are 1)should have within unit lenth 2)should be in the preferred direction. 

![image](https://user-images.githubusercontent.com/123365842/216804645-0c5887ec-9464-47c3-9eca-f4c9801ae9d7.png)


    Assumes route guides for each net satisfy inter-guide connectivity.

If two guides are connected then 1) they are on the same metal layer with touching edges. 2) they are on the neighbouring metal layers with a nonzero vertically overlapped area.

    Assumes route guides for each net satisfy inter-guide connectivity.

# TritonRoute feature 2 & 3 - inter-guide connectivity and intra-layer & inter -layer routing

Each unconnected terminal. i.e, poin of a standerd-cell instance should have its pin shape overlapped by a route guide.

![image](https://user-images.githubusercontent.com/123365842/216804965-4abcfe57-8c90-4e0d-a612-c9c848150dfe.png)

Here we can see that black dots are pins of the cells and it is overlapped by route guide. if you have pins on the intersection of the vertical and horizontal tracks that will ensure that it will be overlapped by route guides.

# Intra-layer parallel and inter-layer sequential panel routing

Intra layer means within the layers and inter layear means between the layers.
![image](https://user-images.githubusercontent.com/123365842/216804955-128cece7-5749-46c0-a113-17b229cbbd05.png)

In this figure we can see the 4 layers of metal. each of these layers are devided in to the "--" lines. lets focus on metal 2 layer. here we assume the routing direction vertical. These "--" lines are called pannels. each pannels assigns the routing guides. here we can see the blue arrows. here routing is heppenes in the even index. it means that intra layer parallel routing. first it is heppenes in the even index and the it will heppen in the odd index. but it is heppening in the parallel in this perticular layer.

So, the (a) figure shows the parallel routing of panels on M2.In (b) figure, we can see the parallel routing of even panels on M3 and (c) shows the parallel routing of odd panels on M3.

# TritonbRoute method to handle connectivity

    INPUTS: LEF

    OUTPUTS:detailed routing solution with optimized wore-length and via count

    CONSTRAINTS:Route guide honouring, connectivity constraonts and design rukes

Now we have to defined the space where detailed routing take spaced.

# Handling connectivity

![image](https://user-images.githubusercontent.com/123365842/216804935-f92aeaff-e791-4dfe-914d-127bac150ae1.png)

# To handle the connectivity, two concepts comes into the picture,

    Access point:An on-gride point on the metal layer of the route guide, and is used to connect to lower-layer segments, upper-layer segments, pins or IO ports.

    Access point cluster (APC): A union of all access points derived from same lower-layer segment,upper-layer guide, a pin or an IO port

Here in the figure shown above, the illustration of access points:

(a)To a lower-layer segment

(b)To a pin shape

(c)To upper layer

# Routing topology algorithm and final files list post-route

![image](https://user-images.githubusercontent.com/123365842/216804922-de0c8901-d30b-4987-8502-bf060e93c882.png)

The algorithm says that for each APCs we have to find the cost associated with it and we have to do minimum spaning tree betweem the APCs and the cost. finally the conclusion of the algorithm is that we have to find the minimul and the most optimal poits between two APCs.

Now, remaning things is the post routing STA analysis. for that the first goal is to extract the perasetic (SPEF). This SPEF extraction is done outside the openlane because openlane does not have SPEF extraction tool.

The .spef file can be found under the routing folder under the results folder.

![image](https://user-images.githubusercontent.com/123365842/216838116-e07a8c03-182a-43c2-abc8-51829cda6556.png)

The following command can be used to stream in the generated GDSII file.

"run_magic"

Now the gds file will be generated and it is stored in the magic folder under results folder.

![image](https://user-images.githubusercontent.com/123365842/216838092-e5e865ac-50a1-4508-925d-030194f05d58.png)

And the generated layout is,

![image](https://user-images.githubusercontent.com/123365842/216838080-ee4e6d3b-5282-4593-b074-f9e5bba4e2c5.png)
















































    
    



    







   


























    




   
   
   
