[home](README.md) - [gdb](gdb.md) - [git](git.md) - [valgrind](valgrind.md) - [makefile](makefile.md) - [objdump](objdump.md)
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