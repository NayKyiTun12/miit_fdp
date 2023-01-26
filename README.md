# miit_fdp
Day 1 Content
Introduction to Verilog RTL Design and Senthesis
Lab Using iverilog and gtkwave
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






























