# 1- Introduction to Bash scripting

### Questions
- What is a Bash script? Why do I need it?
- How do I write a Bash script?
- How can I save and re-use commands?

### Objectives
- Write a simple script that runs a command or series of commands for a
fixed set of files.
- Run a shell script from the command line.
- Use shebang and run the script without bash interpreter prefix

A Unix shell interprets user commands, either directly entered from the command line,
or read from a file called shell script. Shell scripts are directly interpreted
by the operating system, no need to be compiled like C++.

```bash
cat /etc/shells
history
```

When we want to reuse commands, we can find older commands using the
up/down arrow keys or `history` command.

When we need to accomplish many tasks and repeat them frequently, using
arrow keys or `history` will be inefficient. It is better to save your
commands to a file. Instead of executing the commands one by one on the
command line, we can execute the file. This file is called a shell
script. If you shell is using Bash, then we can call this file a Bash
script.

Let's start with a simple command and reproduce its function the using a
script. We will use some input files from "shell-novice-data" folder.

Remember `head` command prints out a number of lines from the top of the
file and `tail` command prints out a number of lines from the bottom of
the file. Using these commands let's print out the contents of
"octane.pdb" file omitting the header.

```bash
cd /absolute/path/to/shell-novice-data/bash-scripting/molecules
pwd
ls -hl
alias ll='ls -hl'
ll
head -n 12 octane.pdb
head -n 12 octane.pdb | tail -n 10
```

If you get suspended, the system is waiting for further commands from you,
you can just hit
```
Ctrl + c
```

Now, if we want to re-use these commands, a script is the best way to
store them for future use. We will use a text editor called nano to
create our first script.

```bash
nano middle.sh
```

This will open the interface of nano and let's you write to the file.
Let's write the first `head` command in the file:

> Code
```code
    #!/bin/bash
    head -n 12 octane.pdb
```

After writing the first line, save (via <kbd>CRTL</kbd>+<kbd>o</kbd>
then hit <kbd>Enter</kbd>/<kbd>Return</kbd>) and exit (via
<kbd>CTRL</kbd>+<kbd>x</kbd>) the file.

Now we can run our first script with `bash` as the interpreter.

```bash
bash middle.sh
```

When you read Bash scripts you will see the first line of the script
starts with `#!` characters and the path to the Bash interpreter. This line
is called the shebang or hashbang.

```
which bash
ls -hl /bin
```

You may see different ways that shebang can be written:

> Code
```code
    #!/bin/bash
```

> Code
```code
    #!/usr/bin/env bash
```

When your script starts with a shebang, the system will know what
interpreter that it needs to use to run the script. In our case, the
interpreter is bash. When shebang is included in your script, you can
run the script without prefixing with the interpreter on the command line.

When shebang is added to the script, we can make our script an
executable by giving execute permission to the user. Then we can run the
script without using `bash` prefix.

```bash
ls -hl
chmod +x middle.sh
ls -hl
```

We should see the same output as before. Let's continue to enter more
commands in our script and run it.

```bash
nano middle.sh
```

> Code
```code
    #!/bin/bash

    head -n 12 octane.pdb
    echo ""
    head -n 12 octane.pdb | tail -n 10
```

Running this script again:

```bash
bash middle.sh
```

Now we will see a single output that is a combination of both commands
that is in "middle.sh" file.

# 2- Variables and Arguments

### Questions
- How do I introduce and manipulate variables in a bash script?
- How do I use arbitrary inputs without changing the script every time?

### Objectives
- Make your bash script more flexible with arguments and variables.
- Write a shell script that operates on a set of files defined by the
user on the command line.
- Explain why spaces and some punctuation characters should not be used in
file names.
- Demonstrate how to see what commands have recently been executed.
- Re-run recently executed commands without retyping them.


## Variables

In programing, variables are information holders, or labels of
information. You can access the same information through out your
program by calling its label. You can also assign new information to the
labels. Using variables make your code more flexible.

Variables can be defined by the system, which are called environmental
variables:

```
echo $PWD
echo $HOME
env
```

Users can also define their own variables:
```
myName=Raymond
echo $myName
```

`$` symbol tells the shell interpreter to treat *myName* as a
**variable** and look what is inside this label. So `$myName` returns
the value of the variable which becomes "Raymond". In some bash code,
you may see `${myName}` which is equivalent to `$myName`

Variable names are case-sensitive and cannot start with a number.

Let's edit our first Bash script "middle.sh".

```bash
nano middle.sh
```

We will type the following code block in the script file to look at
variable 'myinput'.

> Code
```code
    #!/bin/bash
    myinput="octane.pdb"
    echo "My input file is" $myinput

    head -n 12 $myinput
    head -n 12 $myinput | tail -n 10
```

Running the script again:
```bash
bash middle.sh
```

## Arguments

The input to our commands was file "octane.pdb" last time. It would be
ineffective to change our script every time when we want to examine another
file.

It is possible to provide our input as an argument to our script when we
want to run it. Let's edit "middle.sh" again:

```bash
nano middle.sh
```

> Code
```code
    #!/bin/bash

    myinput=$1
    echo 'My input file is' $myinput

    head -n 12 $myinput
    head -n 12 $myinput | tail -n 10
```

In this code sample we replaced "octane.pdb" value for `myinput`
variable with `$1`. This is called positional parameter and its value
will be the first argument to our script on the command line.

```bash
bash middle.sh octane.pdb
bash middle.sh pentane.pdb
```
We can also directly supply positional parameter to our commands.

```bash
nano middle.sh
```

> Code
```code
    #!/bin/bash

    # myinput=$1
    echo 'My input file is' $1

    head -n 12 $1
    head -n 12 $1 | tail -n 10
```

Here, we first comment out the line setting the `myinput` variable. A
comment starts with a `#` character and runs to the end of the line. The
computer ignores comments. Then, we replaced all instances of `myinput`
with `$1` which takes the value of our first script argument on the
command line.

Let's run our script to see if there is any change in the output:
```bash
bash middle.sh octane.pdb
bash middle.sh pentane.pdb
```

Some more introduction to commenting. It is a good coding practice to add
comments in your script to explainwhat is being done to another user of
your script.

```bash
nano tmp.sh
```

> Code
```bash
    #!/bin/bash
    # This is a comment, the line above is a shebang
    ## This is also a comment
    echo "Hello" # A comment can also come after a command
    # some other commands...
```

```bash
bash tmp.sh
```

We will only see the `echo` command output Hello.

Comments are invaluable for helping people (including your future self)
understand and use scripts. However each time you modify the script, you
should check if the comment is still accurate.

Now we will simplify our script and add more positional parameters so
that we can use more arguments with our script.

```bash
nano middle.sh
```

> Code
```code
    #!/bin/bash
    # head -n 12 octane.pdb | tail -n 10
    head -n $2 $1 | tail -n $3
    # take a look at the argument variables
    echo ""
    echo "\$0 is" $0
    echo "\$1 is" $1
    echo "\$2 is" $2
    echo "\$3 is" $3
```

After changing our code as above, we run it:

```bash
bash middle.sh octane.pdb 12 10
```

The positional parameters `$1`, `$2` and `$3` receive their values in
the same order as arguments given on the command line. Consequently the
output of the script remained the same.

In case the argument happens to contain any spaces, we surround both the
argument and positional parameter with double-quotes. If the argument
name does not have spaces, double-quotes make no difference. Coding is
simpler and straightforward if avoid using spaces (or other special
characters) in file names.

```bash
nano middle.sh
```

> Code
```code
    #!/bin/bash
    # head -n 12 octane.pdb | tail -n 10
    head -n "$2" "$1" | tail -n "$3"
    # take a look at the argument variables
    echo ""
    echo "\$0 is" "$0"
    echo "\$1 is" "$1"
    echo "\$2 is" "$2"
    echo "\$3 is" "$3"
```

```bash
bash middle.sh "high octane.pdb" 3 2
```

Let's write another script to find the number of lines for each "pdb" files
and sort them according to these numbers.

```bash
nano sorted.sh
```

> Code
```code
    #!/bin/bash
    wc -l "$1" "$2" "$3" | sort -n
```

Let's execute the script but instead of listing all the files exclusively
as script arguments, we use a wildcard notation:

```bash
bash sorted.sh *.pdb
```

As you see we did not get all the files. Only three files reported because
we entered three positional parameters in the script. If we want to enter
any number of input arguments, instead of using `"$1"`, `"$2"` etc., we
could use `"$@"`

```bash
nano sorted.sh
```

> Code
```code
    #!/bin/bash
    wc -l "$@" | sort -n
```

Let's execute the script

```bash
bash sorted.sh *.pdb
```

If you forget to provide input as shown below, the script will start but
not do anything. To exit from this state hit <kbd>CRTL</kbd>+<kbd>c</kbd>.

```bash
bash sorted.sh
```

A shortcut to save some useful commands is to redirect the current
history to a file. Let's record the last five commands that have been
issued.

```bash
history | tail -n 5 > recent-commands.sh
cat recent-commands.sh
```

As you see each command is assigned a number in the first column. Using
that number you can easily reissue any command. We just type `!<number>`
on the command line where <number> is the assigned number for that command.

We can also remove the serial numbers from the file using a text editor
and use the file as a bash script that includes a accurate record of our
recent commands.

# 3- Loops

### Questions
- How can I perform the same actions on many different files?

### Objectives
- Write a loop that applies one or more commands separately to each file
in a set of files.
- Trace the values taken on by a loop variable during execution of the loop.
- Explain the difference between a variable’s name and its value.

Loop structures are common to all programing languages. They are used
for executing a block of code over and over again thus helping us to code
repetitive tasks in an efficient manner.

Let's move to "creatures" folder. We will work with the two files but let's
first create backup copies.

```bash
cd ../creatures
nano list_creatures.sh
```

> Code
```code
    #!/bin/bash
    for filename in basilisk.dat unicorn.dat
    do
        head -n 2 "$filename" | tail -n 1
    done
```

`$` symbol tells the shell interpreter to treat *filename* as a **variable**
(which can also be called loop index). `$filename` returns the value of
the variable which becomes *basilisk.dat* and *unicorn.dat* within the loop.

We run the list-creatures.sh

```bash
bash list_creatures.sh
```

Instead writing all the file names as the argument of the loop, we can use
wildcards to simplify the listing. Using wildcard notation and a loop, let's
create back-up files for all creature files with our script:

```bash
nano copy_files.sh
```

> Code
```code
    #!/bin/bash
    for filename in *.dat
    do
        echo $filename
        cp "$filename" original-"$filename"
    done
 ```

```bash
bash copy_files.sh
```

We can provide the values of the loop index from the command line as
we discussed in Arguments section.

First remove the back-up files:

```bash
rm original*
```

Then recreate the back-up files by providing the list of files from the
command line:

> Code
```code
    #!/bin/bash
    for filename in "$@"
    do
        echo "$filename"
        cp "$filename" original-"$filename"
    done
 ```

Run the script and check if the files are recreated:

```bash
bash copy_files.sh *.dat
ls -al
```

As before, we can delete the back-up files if we don't need them:

```bash
rm original*
```

Now let's explore how we can combine a set of files selected via certain
criterion. For this we will go back to "molecules" folder.  Assume we
want to append all the molecules containing letter "c" in their name:

```bash
nano append-files.sh
```

> Code
```code
    #!/bin/bash
    for molecule in *c*
    do
        echo "$molecule"
        cat "$molecule" >> c_molecules.dat
    done
```

Print the contents of "c_molecules.dat" file on the screen and then delete
the file

```bash
cat c_molecules.dat
rm c_molecules.dat
```

Notice that we used `>>` in redirection to append files instead of `>`.
If we use the latter, you will only see the contents of the last file since
every iteration of the loop "c_molecules.dat" file is overwritten with new
content. We also used double-quotes around the value `$molecule` to capture files
with spaces in their names.

Another common usage of for loops is two run some commands for a number
of times

```bash
cd ..
pwd
mkdir make_files
cd make_files
nano generate_files.sh
```

>Code
```code
    #!/bin/bash

    # loop over 1-10
    for i in {1..10}
    do
        touch file-$i.dat
        echo $i > file-$i.dat
    done
```

Now we want to increment 2 each time
>Code
```code
    #!/bin/bash

    # loop over 1, 3, 5, 7, 9
    for i in {1..10..2} #{START..END..INCREMENT}
    do
        touch file-$i.dat
        echo $i > file-$i.dat
    done
```

An equivalent method
>Code
```code
    #!/bin/bash

    # loop over 0, 2, 4, 6
    for ((j=0; j<7; j=$((j+2))))
    do
        echo $j > file-$j.dat
    done
```

# 4- Conditionals

Here we introduce some basic conditionals for Bash scripting, where the system
performs different operations at different conditions.

```bash
cd ..
pwd
nano count.sh
```

>Code
```code
    #!/bin/bash

    count=$1
    if [ $count -eq 0 ]
    then
        echo $count "is equal to 0"
    elif [ $count -lt 0 ]
    then
        echo $count "is less than 0"
    elif [ $count -gt 1 ] && [ $count -lt 3 ] # && for logical AND, || for logical OR
    then
        echo $count "is between 1 and 3"
    else
        echo $count "is beyond our scope"
    fi
```

Other common integer comparison commands
```code
    -eq   equal to
    -ne   not equal to
    -gt   greater than
    -ge   greater than or equal to
    -lt   less than
    -le   less than or equal to
```

Check whether a file a directory exists

```bash
nano check_file.sh
```

>Code
```code
    #!/bin/bash

    for filename in $@
    do
        # check whether the file is there
        if [ -e $filename ]
        then
            echo $filename "exists"
        else
            echo $filename "does not exist"
            continue # use break to break out of the while loop
        fi

        # check whether it is a file ro directory
        if [ -f $filename ]
        then
            echo $filename "is a file"
        elif [ -d $filename ]
        then
            echo $filename "is a directory"
        else
            echo $filename "type unknown"
        fi
        echo ""
    done
```

Conditionals in while loops
```bash
nano while_loop.sh
```

>Code
```code
    #!/bin/bash

    cnt=0
    while [ $cnt -lt 10 ]
    do
        cnt=$(( cnt+1 ))
        if [ $cnt -eq 5 ]
        then
            continue # use break to break out of the while loop
        fi
        echo $cnt
    done
```

If we still have some time left, let's take a look at some practical cases where bash scripts
are used to setup system environments for software installation.


# Acknowledgement

The workshop is based on the course provided by Software Carpentry:
[The Unix Shell](https://swcarpentry.github.io/shell-novice/)