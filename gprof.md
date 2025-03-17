[home](README.md) - [gdb](gdb.md) - [git](git.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [linux](linux.md)

# [gprof](https://sourceware.org/binutils/docs-2.18/gprof/index.html)
## How to use quickly
* add option '-pg' on compilation
* run the program
* a file 'gmon.out' is created
* run gprof <program_name> gmon.out to see result in terminal

otion l permet d'afficher les stats par ligne de commandes.

l'option b permet de ne pas afficher les aides de lecture
