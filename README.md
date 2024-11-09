# RISC-V Shoot Out

This repository compares RISC-V soft cores in order to help you choose the best one for your application.  There are so many of these soft cores, it is very hard to choose the right one.  This repository should help you choose. 

This document will soon cover a vast amount of code.  If there are any mistakes, please forgive us and create an issue or make a pull request. 

## ICE40 RISC-V Soft Cores

This section compares RISC-V soft cores which can run on the less expensive, more popular Lattice ICE40 UP5K FPGA.  

### [FemtoRV](https://github.com/dloubach/femtorv32)

This is a great cpu for learning verilog. Starting with a blinky, the system goes through 20 metamorphosii and becomes a RISC-V chip.  The creator Bruno Levy is this charming professorial type, and his hench man Matthia Koch is a brilliant technologist.  

### [NEORV32](https://github.com/stnolting/neorv32)

A platform independent VHDL processor with an emphasis on error-checking. 

> Special focus is paid on **execution safety** to provide defined and predictable behavior at any time.  For example, the CPU ensures *all* memory accesses are properly acknowledged and *all* invalid/malformed
> instructions are always detected as such. Whenever an unexpected state occurs the application software is informed via *precise* and resumable hardware exceptions.   

### [VexRiscv](https://github.com/SpinalHDL/VexRiscv) [[Video](./images/video.png)](https://www.youtube.com/watch?v=dR_jqS13D2c))

Video

This is a very configurable CPU written in its own langauge SpinalHDL whitten in Scala.  it is perfect for pipelined CPUs.  You can edit code in one file which affects different parts of the pipeline.  Don't even think of trying to do that in Verilog or VHDL. 
Of course there is a huge learning curve here.  Scala and SpinalHDL are both quite large. Like the author says, do not start by reading the code of an expert SpinalHDL developers, start with the much simpler tutorials, and slowly build up to understanding more complex ideas. 

Getting your organization to accept SpinalHDL is a huge challenge.  But building complex configurable pipelined CPUs in Verilog is a bigger challenge. 

### [MicroRV32](https://github.com/agra-uni-bremen/microrv32)

## Larger Portable Soft Cores

Here are the larger portable soft cores, ones which cannot run on an ICE40 board.  

- [Bluespac](https://bluespec.com/products#portable)

## FPGA Vendor Specific Solutions

Most of the FPGA vendors provide RISC-V soft cores optimised for their platform.   They will be listed here.  so this section will really be a comparison between (board+Soft core) from each of the vendors.

- AMD/Xilinx MicroBlaze V

- Altera NIOS

- Microchip**, Mi-V RV32 Soft RISC-V Processor

## Financial Disclosure Statement

 The author does not produce, support nor endorse any specific RISC-V cores. He does not accept financial inducements from any of the RISC-V core vendors. Instead he wants everyone to port their RISC-V cores to the [pico-ice circuit board](https://pico-ice.tinyvision.ai/), and buy many [$35 pico-ice boards](https://tinyvision.ai/products/pico-ice-fpga-trainer-board).  
