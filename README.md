# RISC-V Shoot Out

There are so many RISC-V soft cores that it s very hard to choose the right one.  In order to help you choose the best RISC-V soft core for your application,  this directory categorizes the important ones and provides a brief introduction.  Some are good for education, some for error checking, some for size, some for speed, some for a particular FPGA architecture, some for name recognition.  This repository should help you sort through the noise and choose the best one for your needs.   

## 1. Tiny Cores

These are two cores that have a data path smaller than 32 bits wide, 1, 2, 4, or 8 bits wide.  That allows them to be much smaller, but then they take a lot more clock cycles to execute an instruction.   This is where my interest and expertise lie. 

### [Serve](https://github.com/olofk/serv)

The Serve soft core has a 1 bit wide data path, only requires 198 ICE40 LUTs, but takes a lot of clock cycles (how many?) to execute each instruction.  

### [FazyRV](https://github.com/meiniKi/FazyRV)

[Video](https://youtu.be/rRPVVCbpF5M) FaxyRV has a scalable data path to 1, 2, 4, or 8 bits with many variants.

### [NanoV](https://github.com/MichaelBell/nanoV/blob/main/README.md)

A bit serial processor, which rotates through the bits. On every clock cycle it accesses one 32 bit memory word, where each bit is from a different register.   Memory is FerroElectric RAM (FRAM), like Flash, but can be written to 10,000,000,000,000 times.

## 2. ICE40 Soft Cores

This section compares RISC-V soft cores which can run on the less expensive, more popular Lattice ICE40 UP5K FPGA.  

### [FemtoRV](https://github.com/dloubach/femtorv32)

This is a great cpu for learning verilog. Starting with a blinky, the system goes through 20 metamorphosii and becomes a RISC-V chip.  The creator Bruno Levy is this charming professorial type, and his hench man Matthia Koch is a brilliant technologist.  [@BrunoLevy](https://mastodon.social/@BrunoLevy01@fosstodon.org)  [@Mecrisp](https://mastodon.social/@Mecrisp@chaos.social)

### [NEORV32](https://github.com/stnolting/neorv32)

A platform independent VHDL processor with an emphasis on error-checking. 

> Special focus is paid on **execution safety** to provide defined and predictable behavior at any time.  For example, the CPU ensures *all* memory accesses are properly acknowledged and *all* invalid/malformed
> instructions are always detected as such. Whenever an unexpected state occurs the application software is informed via *precise* and resumable hardware exceptions.   

### [VexRiscv](https://github.com/SpinalHDL/VexRiscv)

This is a very configurable CPU written in its own langauge SpinalHDL whitten in Scala.  it is perfect for pipelined CPUs.  You can edit code in one file which affects different parts of the pipeline.  Don't even think of trying to do that in Verilog or VHDL. Of course there is a huge learning curve here.  Scala and SpinalHDL are both quite large. Like the author says, do not start by reading the code of an expert SpinalHDL developers, start with the much simpler tutorials, and slowly build up to understanding more complex ideas.  [Video](https://www.youtube.com/watch?v=dR_jqS13D2c)

Getting your organization to accept SpinalHDL is a huge challenge.  But building complex configurable pipelined CPUs in Verilog is a bigger challenge. 

### [ICE-V Dual](https://github.com/sylefeb/Silice/blob/master/projects/ice-v/IceVDual.mdhttps://github.com/sylefeb/Silice/blob/master/projects/ice-v/IceVDual.md) and [Ice-V Dual Fermata](https://github.com/sylefeb/Silice/blob/master/projects/ice-v/IceVDualFermata.md)

These cpus have to cores which share an ALU and control structures.  On calls and jumps usually RISC-V computation pauses while the core loads thenext instruction and decodesit.  By alternatiing between the two cores, this problem is avoided.  And many applications can easily be split into twothreads sharing the same memory.   By [@sylefeb@masodon.online](https://mastodon.online/@sylefeb)

### [MicroRV32](https://github.com/agra-uni-bremen/microrv32)

## 3. Larger Portable Soft Cores

### [VexRiscv](https://github.com/SpinalHDL/VexRiscv)

This is an award winning soft core, with great demos, and a great reputation.  Is is descibed above.

### [Hazard 3](https://github.com/Wren6991/Hazard3)

Hazard 3 is both a hard core and a softcore.  It is the hard core on the Raspberry PI 2350, an amazing chip which I am using with the ICE40 FPgA on the $35 [Pico-Ice Circuit Board](https://tinyvision.ai/products/pico-ice-fpga-trainer-board) 

### [PicoRV32](https://github.com/YosysHQ/picorv32/tree/main)

This is the soft core created by the open source Yosys synthesizer team. ""It can be configured as RV32E, RV32I, RV32IC, RV32IM, or RV32IMC core, and optionally
contains a built-in interrupt controller.

### [Bluespac](https://bluespec.com/products#portable)

## 4. Language Specific Solutions

There are a number of RISC-V cores built in languages other than Verilog, or VHDL.  Here are some notable ones worth mentioning. 

### [VexRiscv](https://github.com/SpinalHDL/VexRiscv)

This is an award winning soft core, with great demos, and a great reputation. Is is descibed above.

### [PipelineC RISCV-V + FFT](https://github.com/JulianKemmerer/PipelineC/wiki/Example:-FFT-SoC)

[PipelineC](https://github.com/JulianKemmerer/PipelineC) is a very accessible way to program FPGAs.  Whle Verilog is very hard to learn, data flow using a functional programming approach in C is very understandable for the beginner.     [Slides](https://docs.google.com/presentation/d/e/2PACX-1vTq_OBXkCZ7wBW3qIMDTh55j0FB8w0hHHSCR16SCR8G3qS5QIDEcL-aZhrrkgxP4fehcs-KFkOIVYVL/pub?start=false&loop=true&delayms=5000&slide=id.g3119700989c_0_528) [@PipelineC](https://mastodon.social/@pipelinec@fosstodon.org)

### [Clash RISC-V](https://github.com/adamwalker/clash-riscv)

[Clash](https://clash-lang.org/)  is an HDL written in Haskell, a functional programmign language.  Like the author said, functional programming is very inefficient, but it is a great way to model digital circuits.  There is no way anyyone could know all of the different hardware HDLs, but this one appeals to me the most.  I could be wrong.  Of course getting your organization to approve Haskell could be a hard sell.

## 5. FPGA Vendor Specific Solutions

Most of the FPGA vendors provide RISC-V soft cores optimised for their platform.   They will be listed here.  so this section will really be a comparison between (board+Soft core) from each of the vendors.

- AMD/Xilinx MicroBlaze V

- Altera NIOS

- Microchip**, Mi-V RV32 Soft RISC-V Processor

## 6. Contributing

Contributions are welcome.  What do you want added?  Please get off of corporate social media, and message me [@PythonLinks](https://mastodon.social/deck/@PythonLinks) on open-source, propaganda and censoreship free Mastodon.   For longer discussions, please visit the [FPGA Discord Server, RISC-V channel](https://discord.gg/pZhvTPHf9V) and mention "@Christopher Lozinski".  

## 7. Financial Disclosure Statement

 The author does not produce, support nor endorse any specific RISC-V cores. He does not accept financial inducements from any of the RISC-V core vendors. Instead he wants everyone to port their RISC-V cores to the [pico-ice circuit board](https://pico-ice.tinyvision.ai/), and buy many [$35 pico-ice boards](https://tinyvision.ai/products/pico-ice-fpga-trainer-board).   At some point I will also talk about very small stack machines here. 

## 8. Other Risc-V Soft Core Lists.

There are a number of other RISC-v soft core lists. Two are 5 years old. One is 3 years old.  One if based on vendor submissions, rather than editorial reviews.  One includes hard cores.   Surprising that no one else has created a list like this.  
