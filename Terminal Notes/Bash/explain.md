## File: Bash.md

- **Purpose**: Cheat‑sheet of common Bash and shell concepts, including detecting shells, running scripts, conditionals, loops, and redirection.
- **Detect current shell**: `echo $SHELL` prints which shell binary you’re currently using.
- **Find Bash path**: `which bash` shows the filesystem path to the Bash executable.
- **Start Bash explicitly**: `/usr/bin/bash` launches Bash even if your login shell is different.
- **Make script executable**: `chmod +x <filename>` gives execute permission so a script can be run directly.
- **Shebang example**: `#!/bin/zsh` at the top of a script tells the system to run it with zsh.
- **Command substitution**: `variable_name=$(command)` runs a command and stores its output in a variable.
- **Basic arithmetic**: `expr 10 + 10` evaluates an expression and prints the result.
- **Multiplication with expr**: `expr 10 \* 10` uses `\*` so the shell doesn’t treat `*` as a glob.
- **If statement template**: The `if [ <condition> ]; then ... fi` block shows the basic structure for conditional logic.
- **Test operators**: Examples like `$x -eq 20` and `$x -ne 20` show numeric equality and inequality checks.
- **File tests**: `-f <filename>` checks for a regular file; `-d <directory>` checks for a directory.
- **Exit status**: Successful commands return exit code 0; `echo $?` prints the last command’s exit status.
- **While loop**: The `while [ <condition> ]; do ... done` template repeats commands while a condition is true.
- **Sleep**: `sleep <time_in_second>` pauses execution for a given number of seconds.
- **Numeric comparisons**: `-le` and `-ge` provide “less than or equal” and “greater than or equal” checks in conditions.
- **For loop**: The `for x in (1..10); do ... done` example demonstrates iterating over a range/list.
- **Install scripts globally**: Moving scripts into `/usr/local/bin` without an extension lets you run them by name from anywhere.
- **Stdout redirection**: `<command> > <filename>` writes command output to a file (overwriting it).
- **Append redirection**: `<command> >> <filename>` appends output to the end of a file.
- **Split stdout/stderr**: `find . -type -f 1> <filename>` sends normal output to a file; `2> <filename>` sends errors to a different file.

