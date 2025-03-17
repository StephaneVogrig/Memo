[home](README.md) - [gdb](gdb.md) - [git](git.md) - [valgrind](valgrind.md) - [makefile](makefile.md) - [strace](strace.md) - [objdump](objdump.md)

# Linux

### Gestion des processus

ctrl-z : suspend le processus courant

fg : reprend le processus en premier plan

bg : reprend le processus en arriere plan

jobs : affiche la liste des processus dans la session courante

ps : affiche la liste des processus en cours sur le terminal courant



crtl + d : envoi eof

#### signaux interceptable
crtl + c : SIGINT : interrompt l'execution d'un processus
crtl + \ : SIGQUIT : interrompt l'execution d'un processus et vide le noyau

#### signaux non interceptable
crtl + z : SIGSTOP : suspend l'execution d'une commande

[Signaux unix](https://www.malekal.com/signaux-unix/)
