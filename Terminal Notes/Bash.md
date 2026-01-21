# Bash

Category: Shell

- `echo $SHELL`  - show which shell am I using
- `which bash` - see the path
- `/usr/bin/bash` - run bash
- `chmod +x <filename>` - make the file executable
- Shabug = #!/bin/zsh
- to run command in shell `variable_name=$(command)`
- `expr 10 + 10` -  run expression
- `expr 10 \* 10` - only for multiplication
- if condition

```bash
if [ <condition> ]
then 
	...
fi
```

- `$x -eq 20` - check (==)value
- `$x -ne 20` - check not equality
- `-f <filename>` - check file
- `-d <directory>` - check directory
- every successful command return 0 `echo $?`
- while loop

```bash
while [ <condition> ]
do
	...
done
```

- `sleep <time_in_second>` - stop terminal
- `-le` - ≤
- `-ge` - ≥
- for loop

```bash
for x in (1..10)
do
	...
done
```

- move the shell file to the `/usr/local/bin` without file extension. So that I can run it from anywhere just writing the file name
- `<command> > <filename>` write the output in the file
- `<command> >> <filename>` write the output in the file at the end
- `find . -type -f 1> <filename>` write the output
- `find . -type -f 2> <filename>` write the error
-