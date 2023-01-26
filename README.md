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


































