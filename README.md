# Unix Shell

A small Unix shell with pipes, redirection and a few built-ins, written in C. Built January to March 2025.

**Status:** 🚧 Work in progress. The source isn't published here yet.

## Why

My operating systems course covered `fork` and `exec` in one slide. I wanted to see what actually happens between `cat` and `grep` when I type a pipe.

## What I did

A tokenizer that understands quotes, then `fork`, `execvp` and `waitpid` for each command. Redirection is `open` plus `dup2`, and a pipeline is one `pipe` per `|`. The shell ignores `SIGINT` itself and each child puts it back, so Ctrl+C stops the program and not the shell. Built-ins: `cd`, `pwd`, `exit`, `echo`.

My first pipelines hung forever. The parent still held the write end of each pipe, so `grep` never saw end of file. Closing every unused pipe end, in the parent and in each child, fixed it. It also taught me to reach for `strace` before guessing.

## Result

- About 1,100 lines of C.
- 40 small scripts run the same commands in bash and in this shell and compare the output.
- The first of my three systems projects, and where most of what I know about debugging came from.

## Tools

C on POSIX system calls, tested on Linux, built with Make.

More at [ernestbaffour.com](https://ernestbaffour.com/#shell).
