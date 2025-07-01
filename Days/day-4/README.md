## Day 4: Diving Deeper into Bash Scripting
## Date: [30-06-25]

Today was all about getting hands-on with Bash scripting! From basic commands to more complex logical constructs and functions, I explored how to automate tasks and make my command-line experience even more powerful.

## Core Concepts & Basic Structure
Bash scripts are essentially lists of commands that the Bash interpreter executes. They're incredibly useful for automating repetitive tasks, managing files, and even building small applications.

## The Shebang Line: `#!/bin/bash`
This is always the first line of a Bash script. It tells the system which interpreter to use to exeute the script. ``#!/bin/bash`` is the most common for Bash scripts.

## Comments: `#`
Anything after a ``#`` on a line is ignored by the interpreter. Use them generously to explain your code!

## Executing a Script
1. **Make it Executable:** ``chmod +x your_script.sh``
2. **Run it:** ```./your_script.sh```

## The `echo` command & Variables
The `echo` command is your best friend for displaying output. Variables allow you to store and manipulate data within your scripts.

### Basic `echo`
```Bash
#!/bin/bash
echo "Hello, Bash Scripting"
```
