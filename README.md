# z80emulator

This repository contains a simple z80 emulator, which allows loading and executing programs.  It was written by Lin Ke-Fong, and lightly modified by myself.

## Compilation & Usage

You should be able to compile via:

    make

Once you've compiled the program you can launch your z80 binaries via:

    z80emulator path/to/file


## I/O

The emulator has been modified to allow single character input/output.  This
is done by executing the IN/OUT instructions.

To output a single character:

    LD a, 's'
    OUT 1, a

To read a single character:

    IN a, 1

(i.e. In both cases the I/O address is 1).

Steve
--
