
# COMMAND LINE EXERCISES WITH BASH SCRIPTING AND LOOPING
<hr>


### I. Loop Exercises

**I.01)** Write a loop command to print out integers 1 to 20 (increasing order) to the screen where each number should be printed out on a separate line.


```bash
for ((i=1;i<=20;i+=1)); do echo $i; done

#or

for i in `seq 20`; do  echo $i; done
```

**I.02)** Write a loop command to print out integers 20 to 1 in (decreasing order) to the screen where each number should be printed out on a separate line.


```bash
for ((i=20;i>0;i-=1)); do echo $i; done
```

**I.03)** In addition to `for`, loops can be created with `while` statement in bash scripts. Using `while` loop  repeat the last twp exercises i.e.:
- Write a loop command to print out integers 1 to 20 (increasing order) to the screen where each number should be printed out on a separate line.
- Write a loop command to print out integers 20 to 1 in (decreasing order) to the screen where each number should be printed out on a separate line.<br>
(Hint: When using  `while`, the loop continues until some condition is false. The argument of the condition should change during the loop operation. Otherwise you would end up with an infinite loop. Explore `while` loops on the web for further details.)


```bash
i=1; while [ $i -lt 21 ]; do echo $i; i=$((i+1)); done
```


```bash
i=20; while [ $i -gt 0 ]; do echo $i; i=$((i-1)); done
```

**I.04)** Write a loop command to print out integers 20 to 1 in (decreasing order) to the screen where all the numbers printed on the same line separated with a space.


```bash
for ((i=20;i>0;i-=1)); do echo -n "$i "; done; echo " "
```

**I.05)** Write a loop command to print out integers 1 to 20 (increasing order) to a file (called "integers.txt") where each number should be printed out on a separate line.


```bash
rm integers.txt; touch integers.txt; for ((i=1;i<=20;i+=1)); do echo $i>> integers.txt; done
```

**I.06)** Write a command including a loop to add 1 to each integer in "integers.txt" file and write it to "plusone.txt". Assume you don't know the number of lines in "integer.txt".


```bash
rm plusone.txt 
i=`cat integers.txt | wc -l` 
touch plusone.txt 
for j in `seq $i`; do l=`head -n $j integers.txt | tail -1`; echo $((l+1))>>plusone.txt; done
```

**I.07)** Do the same as operation in the last question  but this time use sed function witin the loop to access each line in "integers.txt". Search for sed function on the web or read `man sed` or `sed --help` for its use. Again, assume you don't know the number of lines in "integer.txt".


```bash
rm plusone.txt 
i=`cat integers.txt | wc -l`
touch plusone.txt
for j in `seq $i`; do l=`sed -n "$j"p integers.txt`; echo $((l+1))>>plusone.txt; done
```

**I.08)** Write a loop to create 100 folders with names "1","2","3",...,"100". Echo which folder is created each step. Use `seq` function to identify the values over which the loop iterates. Search for `seq` function on the web or read `man seq` or `seq --help`.


```bash
for i in `seq 100`; do mkdir $i; echo $i; done
```

**I.09)** Delete the 100 folders using a similar loop as the last question.


```bash
for i in `seq 100`; do rm -Rf $i; done
```

**I.10)** Write a loop to create 100 folders with names "001", "002",...,"100". Echo which folder is created each step. Again, use `seq` function to identify the values over which the loop iterates. Search for `seq` function  on the web or read `man seq` or `seq --help`. <br>
(Hint: Read flags of `seq` function.)


```bash
for i in `seq -w 100`; do mkdir $i; done
```

**I.11)** Delete the 100 folders using created in the last question.


```bash
for i in `seq -w 100`; do rm -Rf $i; done
```

**I.12)** Write a loop to create 10 folders with names "1", "2",...,"10" but after a folder is created make the code to wait for 3 seconds before creating another folder. Echo which folder is created each step.


```bash
for i in `seq 10`; do mkdir $i; echo $i; sleep 3; done
```

### II. VIM Text Editor Exercises

**II.01)** Print your name the one million times (each on one line) along with the line number to the file "ilikemyname.txt". Use VIM text editor to open "ilikemyname.txt" and delete 783219th line.


```bash
rm ilikemyname.txt
touch ilikemyname.txt 
for i in `seq 1000000`; do echo "Alper Kinaci" $i >> ilikemyname.txt; done
vim ilikemyname.txt

#-- Go to the command-line mode (hit "esc" then ":"), two alternatives after that: 
#1- write 783219 and hit enter/return, 
#2- write ?783219 and hit enter/return. Hit d two times

```

**II.02)** While you are viewing ilikemyname.txt with VIM, set VIM to show line numbers.


```bash
#-- Go to the command-line mode (hit "esc" then ":") and write set nu, hit enter/return
```

**II.03)** Undo your deletion.


```bash
#-- Hit "esc" to go to the normal mode and hit "u"
```

**II.04)** Only erase the number after your name on line 783219.


```bash
#-- Again you have many options here:

#1- Hit "esc" to switch to the normal mode, move the cursor to the beginning of the 
#number and hit "x" 6 times to erase the number on that line one character at a time

#or

#1- Hit "esc" and "6" and then "x" to erase 6 characters. There are several more ways.
```

**II.05)** While viewing ilikemyname.txt with VIM editor, go to the last line and enter the text "Last" before your name. Then go to the first line of the file and enter the text "First" after your name.


```bash
#-- Follow the steps below

#1- Hit "esc" and ":" to go to the command-line mode
#2- Write "$", hit enter/return
#3- Hit "i" to enter insert mode and type "Last" before your name
#4- Hit "esc" and ":" to go to the command-line mode
#5- Write "0", hit enter/return
#6- Hit "i" to enter insert mode, move the cursor after your name and type "First"
```

**II.06)** Save the file, then save the file as "ilikemayname_bckp.txt" and quit to command line.


```bash
#-- Follow the steps below:

#1- Hit "esc" and ":" to go to the command-line mode
#2- Write "w", hit enter/return. The file is saved
#3- Hit "esc" and ":" to go to the command-line mode
#4- Write "w ilikemayname_bckp.txt", hit enter/return. You created ilikemayname_bckp.txt
#5- Hit "esc" and ":" to go to the command-line mode
#6- Write "wq", hit enter/return to save and quit
```

**II.07)** Open "ilikemyname.txt" and "ilikemayname_bckp.txt" both in a single VIM window side-by-side. Delete the first 134000 lines in "ilikemyname.txt". Delete your name in all lines of "ilikemayname_bckp.txt"


```bash
vim -O ilikemyname.txt ilikemayname_bckp.txt

#-- The command above will open 2 files in one VIM editor window. Now, follow the step below:

#1- Make sure the cursor is on ilikemyname.txt tab
#2- Hit "esc" to go to normal mode
#3- Write 134000 and hit "d" 2 times. 134K lines deleted
#4- To move the cursor to ilikemayname_bckp.txt tab hit "esc" (normal mode) and do "Ctrl+w" and hit "w" again.
#5- Hit "esc" and ":" to go to the command-line mode
#6- Write %s/Your Name//g, hit enter/return. All your names are deleted from ilikemayname_bckp.txt tab
#7- Hit "esc" and ":" to go to the command-line mode
#8- Write "wq", hit enter/return to save and quit rom ilikemayname_bckp.txt tab
#9- Hit "esc" and ":" to go to the command-line mode
#10- Write "wq", hit enter/return to save and quit

```

**II.08)** You can work with VIM without opening the editor window. This is called batch mode. Copy ilikemyname.txt" to "ilikemayname_bckp.txt". Now both files have your name. Delete your name in all lines of "ilikemayname_bckp.txt" and save the file with VIM without opening editor window.
(Hint: Explore `vim -c ...` i.e. -c flag)


```bash
cp ilikemyname.txt ilikemayname_bckp.txt
vim -c ":%s/Your Name//g" -c ":wq" ilikemayname_bckp.txt
```

### III. Writing Scripts

**III.01)** Write a script to find if a file exists in "/lib64". Input the filename as a parameter and if the file is in the folder, the script should print out "yourfilename file exists". Otherwise the script should print out "yourfilename file does not exits"


```bash
#!/usr/bin/env bash

filename=$1

if [ -f /lib64/$filename ]; then
    echo "$filename"  'file exits'
else
    echo  "$filename"  'file does not exist'
```

**III.02)** Write a bash script which outputs:<br>
 - "True" when you run it with 1 as the parameter (i.e. bash yourscript.sh 1) <br>
 - "False" when you run it with 0 as the parameter (i.e. bash yourscript.sh 0) <br>
 - "Enter 0 or 1" when you run it with any other integer (i.e. bash yourscript.sh 4) <br>
(Hint: Explore the use of conditionals if, elif, else in bash)


```bash
#!/usr/bin/env bash

myflag="$1"

if [ $myflag -eq 1 ]; then
    echo 'True'
elif [ $myflag -eq 0 ]; then
    echo 'False'
else
    echo 'Enter 0 or 1'
fi
```

**III.03)** Write a bash script to generate 1000 random numbers between 1 and 1000 and write them to a file. Find out how many unique numbers are obtained. <br>
(Hint: Try issuing `echo $RANDOM`, what do you get?)


```bash
#!/usr/bin/env bash

rm randomnumbers.txt
touch randomnumbers.txt

for i in `seq 1000`
    do
        echo $(((RANDOM%1000)+1)) >> randomnumbers.txt
    done

sort -n randomnumbers.txt | uniq | wc -l
```

**III.04)** Write a script to run the script you have developed for unique random numbers n times. n is a variable parameter you will set as an input when you are starting your script.


```bash
#!/usr/bin/env bash

for j in `seq $1`; do
    rm randomnumbers.txt
    touch randomnumbers.txt

    for i in `seq 1000`; do
        echo $(((RANDOM%1000)+1)) >> randomnumbers.txt
    done

    sort -n randomnumbers.txt | uniq | wc -l
done
```
