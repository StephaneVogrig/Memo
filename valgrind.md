[home](README.md) - [gdb](gdb.md) - [git](git.md) - [valgrind](valgrind.md) - [makefile](makefile.md) - [strace](strace.md) - [objdump](objdump.md)
***
### Memcheck
- `--leak-check=full`
### Process
- `--trace-children=yes`
- `--show-leak-kinds=all`
### File descriptor
- `--track-fds=yes`
### Errors suppression
[howto](https://wiki.wxwidgets.org/Valgrind_Suppression_File_Howto)
- `--error-limit=no`
- `--log-file=error.log`
- `--gen-suppressions=all`
- `--suppressions=<filename>`

### --call
