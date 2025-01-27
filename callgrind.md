[home](README.md) - [gdb](gdb.md) - [git](git.md) - [valgrind](valgrind.md) - [makefile](makefile.md) - [strace](strace.md) - [objdump](objdump.md)

***
pour creer le profilage :
valgrind --tool=callgrind ./filename


pour visualiser les resultat :
callgrind_annotate <file_name>