# Risc-V Assembly-to-Hex Converter
The Risc-V Assembly-to-Hex Converter is essentially an assembler that reads a .S file containing Risc-V assembly language, converts the instructions into hexadecimal text, and then writes them to a new .txt or .hex file. Note that this assembler only works for the RV32I ISA, and is meant to be used for running bare metal programs (i.e. without an operating system). 

## Using the Assembler
run `python3 riscv_assembler input.s output.txt` to get a text file or run `python3 riscv_assembler input.s output.txt` to get the .hex file.

## Additional Info
* The assembler does not use ".text" or ".data"  directives. It assumes the text segment starts at instruction 0 in the program count. 
* You must manually load the starting address of your stack pointer in your assembly code. 
* Labels must be on their own line. They cannot share the same line as an instruction.
* Branch statements use labels, but not immediate values. 
* The assembler only recognizes the ABI name for each register (with the exception of "x0", which is used in place of "zero").
                [Risc_V Reg Names](https://en.wikichip.org/wiki/risc-v/registers)
* Due to hardware limitations of the RV32I ISA, branch statements can only reach 511 instructions in the positive direction and 512 instruction in the negative direction.
* The call instruction is also limited to this range, so calling a function more than 511 instructions away requires the use of lui (or auipc) and jalr instructions. 
* For more info on Risc-V go to [Risc-V Specs](https://riscv.org/technical/specifications/) and view "Volume 1" under "ISA Specification"

