[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)- [escape code](ainsi_escape_code.md)

***

# [gprof](https://sourceware.org/binutils/docs-2.18/gprof/index.html)
## How to use quickly
* add option '-pg' on compilation
* run the program
* a file 'gmon.out' is created
* run gprof <program_name> gmon.out to see result in terminal

otion l permet d'afficher les stats par ligne de commandes.

l'option b permet de ne pas afficher les aides de lecture
