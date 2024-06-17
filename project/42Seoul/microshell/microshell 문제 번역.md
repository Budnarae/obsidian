
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

프로그램은 절대 경로와 상대 경로 둘 다 실행 가능하지만 경로를 직접 빌드해선 안됩니다.

- You must implement "|" and ";" like in bash

당신은 파이프("|")와 세미콜론(";")을 bash 에서와 같이 동작하도록 구현하여야 합니다.

- we will never try a "|" immediately followed or preceded by nothing or "|" or ";"

우리는 파이프("|")의 앞과 뒤에 아무것도 없는 경우, 또는 파이프가 위치한 경우, 또는 세미콜론(";")이 위치한 경우를 시험하지 않습니다(syntax error 검사하지 않겠다는 뜻).

- Your program must implement the built-in command cd only with a path as argument (no '-' or without parameters)

당신은 빌트 인 커맨드로 cd를 구현해야 합니다. 단, 매개인자가 입력되지 않는 경우는 고려하지 않습니다.

- if cd has the wrong number of argument your program should print in STDERR "error: cd: bad arguments" followed by a '\n'

만약에 cd가 잘못된 개수의 매개인자를 받으면 당신의 프로그램은 STDERR로 "error: cd: bad arguments"에 개행을 붙힌 문자열을 출력해야 합니다.

- if cd failed your program should print in STDERR "error: cd: cannot change directory to path_to_change" followed by a '\n' with path_to_change replaced by the argument to cd

만약 cd에 잘못된 경로명을 입력하여 프로그램이 실패할 경우 STDERR로 "error: cd: cannot change directory to path_to_change"에 개행을 붙힌 문자열을 출력해야 합니다(path_to change는 cd가 입력받은 경로명으로 대체)

- a cd command will never be immediately followed or preceded by a "|"

cd 커맨드는 파이프라인과 같이 사용될 수 없습니다.

- You don't need to manage any type of wildcards (*, ~ etc...)

당신은 와일드카드(\*, ~ 등등)을 구현할 필요가 없습니다.

- You don't need to manage environment variables ($BLA ...)

당신은 환경변수($BLA ... 등등)와 관련된 기능을 구현할 필요가 없습니다.

- If a system call, except execve and chdir, returns an error your program should immediatly print "error: fatal" in STDERR followed by a '\n' and the program should exit

execve와 chdir을 제외한 시스템 콜이 에러를 반환하면 프로그램은 즉시 STDERR로 "error: fatal"에 개행을 붙인 문자열을 출력하고 exit하여야 합니다.

- If execve failed you should print "error: cannot execute executable_that_failed" in STDERR followed by a '\n' with executable_that_failed replaced with the path of the failed executable (It should be the first argument of execve)

만약 execve가 fail한다면 STDERR로 "error: cannot execute executable_that_failed"에 개행을 붙힌 문자열을 출력해야 합니다(executable_that_failed는 execve가 입력받은 첫번째 매개인자로 대체해야 함).

- Your program should be able to manage more than hundreds of "|" even if we limit the number of "open files" to less than 30.  

프로그램은 백 단위의 파이프("|")와 30개 이하의 열린 파일들을 처리할 수 있어야 합니다.

for example this should work:

예를 들어 아래와 같은 명령문이 동작해야 합니다.

$>./microshell /bin/ls "|" /usr/bin/grep microshell ";" /bin/echo i love my microshell

microshell

i love my microshell

$>

Hints:
Don't forget to pass the environment variable to execve

execve에 환경변수를 전달하는 것을 잊지 마세요.

Hints:
Do not leak file descriptors!

fd의 누수는 허용하지 않습니다(파이프 잘 닫고 열린 파일 잘 닫으라는 뜻).