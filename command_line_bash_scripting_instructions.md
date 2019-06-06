# COMMAND LINE:  BASH SCRIPTING 

##Note: 

Mostly follow software carpentry workshop material
[Software Carpentry Bash Script Module](https://swcarpentry.github.io/shell-novice/06-script/index.html)
[Software Carpentry Looping Module](https://swcarpentry.github.io/shell-novice/05-loop/index.html)
and in a small part (sections 4.2.2 and 4.2.3) from the book Data Science at the Command Line
[Data Science at Command Line Converting one Liner to Script Chapter](https://www.datascienceatthecommandline.com/chapter-4-creating-reusable-command-line-tools.html#converting-one-liners-into-shell-scripts)


## Learning objective I Make a script

Introduce a problem by listing files and file contents.

Show what commands head and tail will do.

Show how to find commands in history and mention other ways to do it. 

Introduce vi command and insert mode. Follow the handout for the rest of the vi commands.

Follow the software carpentry example show the script middle.sh

## Learning objective II Argument

Follow the software carpentry to introduce filename as an argument.

## Learning objective III Quote your variable

Show that without quotes around variable we are not able to handle file names that include special characters (including whitespaces).

## Learning objective IV Multiple arguments

Follow the software carpentry to introduce other arguments and show the script middle.sh in its final form.

## Exercise

Introduce sort and uniq. List the files and file contents.
Make a script that will print out top 10 unique elements from a file.

## Learning objective V Loops

Follow the software carpentry looping through files to find creatures. Use the file middle.sh to make a new file list_creatures.sh

## This is a point where short break could be introduced

## Learning objective VI Expanding the wildcard

Introduce wildcard * 
List the files and file contents. Show how the expansion works.

Follow software carpentry Loops part from cp *.dat original-*.dat.

## Learning objective VII Processing files

Use the above example to show echo and how the usual command line workflow looks like. 
Make copy_files.sh and first observe what is copied and where before actually copying anything.

## Learning objective VIII Introduce $@

Use the above example to show what to do when we are not able to name all the arguments. 

## Learning objective IX Permission to Execute and Define Shebang

Follow 4.2.2. and 4.2.3. from Data Science at Command line. Show that scripts we made will not execute without bash preceding the command we made.

Explain permissions and how to add them and what else to add to be able to execute a command. Mention adding to the path.









