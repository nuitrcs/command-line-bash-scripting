# 1- Introduction to Bash scripting

### Questions
- What is a Bash script? Why do I need it?
- How do I write a Bash script?

### Objectives
- Learn to write and execute a simple script
- Extend your script with multiple commands

Let's start with a simple command and reproduce its function the using a script.
We will use some input files from "shell-novice-data" folder.

Remember `head` command prints out a number of lines from the top of the file and
`tail` command  prints out a number of lines from the bottom of the file. Using
these commands let's print out the contents of "octane.pdb" file omitting the
header.

```bash
cd /absolute/path/to/shell-novice-data/bash-scripting/molecules
head -n 12 octane.pdb
head -n 12 octane.pdb | tail -n 10
```

Now, if we want to re-use these commands, a script is the best way to store them for
future use. We will use a text editor called nano to create our first script.

```bash
nano middle.sh
```

This will open the interface of nano and let's you write to the file. Let's
write the first `head` command in the file:

```code
    head -n 12 octane.pdb
```

After writing the first line, save (via <kbd>CRTL</kbd>+<kbd>o</kbd>
then hit <kbd>Enter</kbd>/<kbd>Return</kbd>) and exit (via <kbd>CTRL</kbd>+<kbd>x</kbd>)
the file.

Now we can run our first script with `bash` as the interpreter.

```bash
bash middle.sh
```

We should see the same output as before. Let's continue to enter more commands
in our script and run it.

```bash
nano middle.sh
```

> Code
```code
    head -n 12 octane.pdb
    head -n 12 octane.pdb | tail -n 10
```

Now running this script again:

```bash
bash middle.sh
```

Now we will see a single output that is a combination of both commands that
is in "middle.sh" file.

# 2- Variable arguments

### Questions
- How do I use arbitrary inputs without changing the script every time?
- How do I ?

### Objectives
- Learn
- Extend

The input to our commands was file "octane.pdb" last time. It would be
ineffective to change our script every time when we want to examine another
file.
