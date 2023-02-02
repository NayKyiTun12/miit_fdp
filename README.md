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







    




   
   
   
