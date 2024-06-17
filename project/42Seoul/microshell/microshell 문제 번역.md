
---

#42Seoul 

---

Assignment name  : microshell
Expected files   : microshell.c
Allowed functions: malloc, free, write, close, fork, waitpid, signal, kill, exit, chdir, execve, dup, dup2, pipe, strcmp, strncmp

과제 이름 : microshell
제출 파일 : microshell.c
허용 함수 : malloc, free, write, close, fork, waitpid, signal, kill, exit, chdir, execve, dup, dup2, pipe, strcmp, strncmp

Write a program that will behave like executing a shell command

쉘 커맨드를 실행시키는 역할을 하는 프로그램을 작성하시오.

- The command line to execute will be the arguments of this program

실행시킬 명령문이 곧 프로그램의 매개인자입니다.

- Executable's path will be absolute or relative but your program must not build a path (from the PATH variable for example)



- You must implement "|" and ";" like in bash

- we will never try a "|" immediately followed or preceded by nothing or "|" or ";"

- Your program must implement the built-in command cd only with a path as argument (no '-' or without parameters)

- if cd has the wrong number of argument your program should print in STDERR "error: cd: bad arguments" followed by a '\n'

- if cd failed your program should print in STDERR "error: cd: cannot change directory to path_to_change" followed by a '\n' with path_to_change replaced by the argument to cd

- a cd command will never be immediately followed or preceded by a "|"

- You don't need to manage any type of wildcards (*, ~ etc...)

- You don't need to manage environment variables ($BLA ...)

- If a system call, except execve and chdir, returns an error your program should immediatly print "error: fatal" in STDERR followed by a '\n' and the program should exit

- If execve failed you should print "error: cannot execute executable_that_failed" in STDERR followed by a '\n' with executable_that_failed replaced with the path of the failed executable (It should be the first argument of execve)

- Your program should be able to manage more than hundreds of "|" even if we limit the number of "open files" to less than 30.

  

for example this should work:

$>./microshell /bin/ls "|" /usr/bin/grep microshell ";" /bin/echo i love my microshell

microshell

i love my microshell

$>

  

Hints:

Don't forget to pass the environment variable to execve

  

Hints:

Do not leak file descriptors!