[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)
***
pour creer le profilage :
valgrind --tool=callgrind ./filename


pour visualiser les resultat :
callgrind_annotate <file_name>