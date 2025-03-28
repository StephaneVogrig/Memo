[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)- [escape code](ainsi_escape_code.md)

***

# [strace](https://strace.io/)
[man en](https://man7.org/linux/man-pages/man1/strace.1.html)  
[math-linux.com](https://www.math-linux.com/linux/tutoriels-linux/article/strace-outil-de-depannage-linux-debugging)

# tracer bash
dans un terminal ou seront saisie les commandes bash
```bash
strace - f -tt -o trace bash
```
dans un deuxieme terminal pour voir les appels systemes
```bash
cat trace
```