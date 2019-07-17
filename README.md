# z80emulator

This repository contains a simple z80 emulator, which allows loading and executing programs.  It was written by Lin Ke-Fong, and lightly modified by [myself](https://steve.kemp.fi/).

The original source is here:

* [https://github.com/anotherlin/z80emu](https://github.com/anotherlin/z80emu)


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
    OUT (1), a

To read a single character:

    IN a, (1)

(i.e. In both cases the I/O address is 1).


## Sample Code

To test the emulator, and the I/O support you can save the following program to `sample.z80`:

     org 0
     in a,(1)
     sub a, 32
     out (1), a
     halt

The intention is that this program will read a single character from STDIN, and converts from lower-case to upper-case, with no error-checking, before outputting the result.

Compile via [z80asm](https://packages.debian.org/z80asm), which will generate `a.bin`:

    z80asm ./sample.z80

Now you have the compiled file, `a.bin`, you can emulate it via:

    ./z80emulator ./a.bin
    Testing "./a.bin"...
    a
    A
    33 cycle(s) emulated.
    For a Z80 running at 4.00MHz, that would be 0 second(s) or 0.00 hour(s).
    Emulating ./a.bin took a total of 1 second(s).


Steve
--
