[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)- [escape code](ainsi_escape_code.md)

***

[1h 1outil](C4A_-_1h1_Outil_-_GDB.pdf) 

# [Gdb](https://sourceware.org/gdb/current/onlinedocs/gdb.html/index.html#Top)

### Interface graphique

- option au lancement `--tui`
- apres lancement de gdb `tui enable`

***

### Arguments

##### enregistrer les arguments

- `start arg1 ... argn`

- `run arg1 ... argn

- `set args arg1 ... argn`
  
  ###### Voir les arguments

- `show arg`

***

### Focus

Commande `focus` raccourci `fs`

- `fs cmd` focus le terminal

***

### Multiprocess

- avant le fork ecrire l'instruction `set detach-on-fork off`
- l'instruction `info inferiors` donne la liste des process
- l'instruction `inferior x` (x etant un nombre) permet de passer d'un processus a un autre