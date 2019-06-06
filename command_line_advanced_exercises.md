
# COMMAND LINE EXERCISES WITH BASH SCRIPTING AND LOOPING
<hr>

### I. Loop Exercises

**I.01)** Write a loop command to print out integers 1 to 20 (increasing order) to the screen where each number should be printed out on a separate line.


```bash

```

**I.02)** Write a loop command to print out integers 20 to 1 in (decreasing order) to the screen where each number should be printed out on a separate line.


```bash

```

**I.03)** In addition to `for`, loops can be created with `while` statement in bash scripts. Using `while` loop  repeat the last twp exercises i.e.:
- Write a loop command to print out integers 1 to 20 (increasing order) to the screen where each number should be printed out on a separate line.
- Write a loop command to print out integers 20 to 1 in (decreasing order) to the screen where each number should be printed out on a separate line.<br>
(Hint: When using  `while`, the loop continues until some condition is false. The argument of the condition should change during the loop operation. Otherwise you would end up with an infinite loop. Explore `while` loops on the web for further details.)


```bash

```

**I.04)** Write a loop command to print out integers 20 to 1 in (decreasing order) to the screen where all the numbers printed on the same line separated with a space.


```bash

```

**I.05)** Write a loop command to print out integers 1 to 20 (increasing order) to a file (called "integers.txt") where each number should be printed out on a separate line.


```bash

```

**I.06)** Write a command including a loop to add 1 to each integer in "integers.txt" file and write it to "plusone.txt". Assume you don't know the number of lines in "integer.txt".


```bash

```

**I.07)** Do the same as operation in the last question  but this time use sed function witin the loop to access each line in "integers.txt". Search for sed function on the web or read `man sed` or `sed --help` for its use. Again, assume you don't know the number of lines in "integer.txt".


```bash

```

**I.08)** Write a loop to create 100 folders with names "1","2","3",...,"100". Echo which folder is created each step. Use `seq` function to identify the values over which the loop iterates. Search for `seq` function on the web or read `man seq` or `seq --help`.


```bash

```

**I.09)** Delete the 100 folders using a similar loop as the last question.


```bash

```

**I.10)** Write a loop to create 100 folders with names "001", "002",...,"100". Echo which folder is created each step. Again, use `seq` function to identify the values over which the loop iterates. Search for `seq` function  on the web or read `man seq` or `seq --help`. <br>
(Hint: Read flags of `seq` function.)


```bash

```

**I.11)** Delete the 100 folders using created in the last question.


```bash

```

**I.12)** Write a loop to create 10 folders with names "1", "2",...,"10" but after a folder is created make the code to wait for 3 seconds before creating another folder. Echo which folder is created each step.


```bash

```

### II. VIM Text Editor Exercises

**II.01)** Print your name the one million times (each on one line) along with the line number to the file "ilikemyname.txt". Use VIM text editor to open "ilikemyname.txt" and delete 783219th line.


```bash

```

**II.02)** While you are viewing ilikemyname.txt with VIM, set VIM to show line numbers.


```bash

```

**II.03)** Undo your deletion.


```bash

```

**II.04)** Only erase the number after your name on line 783219.


```bash

```

**II.05)** While viewing ilikemyname.txt with VIM editor, go to the last line and enter the text "Last" before your name. Then go to the first line of the file and enter the text "First" after your name.


```bash

```

**II.06)** Save the file, then save the file as "ilikemayname_bckp.txt" and quit to command line.


```bash

```

**II.07)** Open "ilikemyname.txt" and "ilikemayname_bckp.txt" both in a single VIM window side-by-side. Delete the first 134000 lines in "ilikemyname.txt". Delete your name in all lines of "ilikemayname_bckp.txt"


```bash

```

**II.08)** You can work with VIM without opening the editor window. This is called batch mode. Copy ilikemyname.txt" to "ilikemayname_bckp.txt". Now both files have your name. Delete your name in all lines of "ilikemayname_bckp.txt" and save the file with VIM without opening editor window.
(Hint: Explore `vim -c ...` i.e. -c flag)


```bash

```

### III. Writing Scripts

**III.01)** Write a script to find if a file exists in "/lib64". Input the filename as a parameter and if the file is in the folder, the script should print out "yourfilename file exists". Otherwise the script should print out "yourfilename file does not exits"


```bash

```

**III.02)** Write a bash script which outputs:<br>
 - "True" when you run it with 1 as the parameter (i.e. bash yourscript.sh 1) <br>
 - "False" when you run it with 0 as the parameter (i.e. bash yourscript.sh 0) <br>
 - "Enter 0 or 1" when you run it with any other integer (i.e. bash yourscript.sh 4) <br>
(Hint: Explore the use of conditionals if, elif, else in bash)


```bash

```

**III.03)** Write a bash script to generate 1000 random numbers between 1 and 1000 and write them to a file. Find out how many unique numbers are obtained. <br>
(Hint: Try issuing `echo $RANDOM`, what do you get?)


```bash

```

**V.04)** Write a script to run the script you have developed for unique random numbers n times. n is a variable parameter you will set as an input when you are starting your script.


```bash

```
