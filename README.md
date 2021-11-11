# Simple-Computer-in-verilog
Computer Organization

Part 1: Simple implementation of Load, Store, and Add instructions.
-----

## Main block 
=====

```verilog
`include "MEM.v"
`include "CPU.v"


module H_COMP ();

reg clock;  // CLock Initialize 
initial begin
    clock = 0;
    forever 
        #5 clock = ~clock;
end


// buses to transfer data
wire [15:0] cpu_to_memory; // cpu_to_memory
wire [15:0] memory_to_cpu; // memory_to_cpu
wire [7:0] MAR;

// Memory enable and control signal
wire Mem_EN, Mem_CS;

MEMORY Mem(MAR, cpu_to_memory, memory_to_cpu, Mem_EN, Mem_CS, clock); 
CPU cpu(MAR, memory_to_cpu, cpu_to_memory, Mem_EN, Mem_CS, clock);

initial begin
    #1 $finish;   
end

endmodule

```

## CPU block and MEMORY block

[CPU.v](https://gist.github.com/98dc5734bdd0512ad65b96f44a33391c.git)

[MEM.v](https://gist.github.com/df626266f31418cec698f0f0a9a65a90.git)

---

#### By GTKwave 
I't doesn't appear - it need to some work 

[]()







Verilog Compiler
=======
###### Icarus Verilog is a free compiler implementation for the IEEE-1364 Verilog hardware description language. Icarus is maintained by Stephen Williams and it is released under the GNU GPL license.
[Icarus Verilog](https://bleyer.org/icarus/)



----

In divide my code into CPU block , MEMORY block and the main block(H_COMP)

where the I add all block to work together.


---

to compile the code i write the command to the terminal 

`iverilog -o [test bench module] [module name]`

after compile it 

 `vvp [module name]`
 
 its DONE


 

