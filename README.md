# Unix Shell

A Unix shell written in C that parses commands and arguments, manages processes, and works with files.

**Status:** 🚧 Work in progress

## Highlights

- Command parsing with arguments and quoting
- Process creation with `fork`, `execvp`, and `waitpid`
- I/O redirection (`<`, `>`, `>>`) and pipelines (`|`) via `dup2` and `pipe`
- Built-ins: `cd`, `pwd`, `exit`, `echo`
- Signal handling so `Ctrl+C` interrupts the child, not the shell

## Tech

C, POSIX system calls, Linux, Make
