[home](README.md) - [makefile](makefile.md) - [git](git.md) - [gdb](gdb.md) - [valgrind](valgrind.md) - [strace](strace.md) - [objdump](objdump.md) - [gprof](gprof.md) - [calgrind](callgrind.md) - [linux](linux.md)- [escape code](ainsi_escape_code.md)

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
