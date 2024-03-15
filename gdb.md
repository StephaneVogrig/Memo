[home](README.md) - [gdb](gdb.md) - [git](git.md) - [strace](strace.md) - [valgrind](valgrind.md)

***

# Gdb

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