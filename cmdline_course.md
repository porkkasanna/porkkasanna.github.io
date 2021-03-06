---
layout: default
---

## Command line tools for linguistis -course

This course teaches us how to use our computers with UNIX system for more streamlined work.
It shows us the basic commands of how to navigate and use (in my case, because I have a mac) terminal, how to
set up directories and projects and of course since this is specifically meant for linguists,
how to do some basic corpus processing.

***

## Week 1: Introduction to Command Line Environment

In the first week we started by learning how to set up a command line environment on our computers.
We learned some of the basic commands (like `mv` to move or rename files or `rm` to remove them) and how
to navigate the directories and files on our computer using the command line (with the `cd` command).
We went over how to use a text editor called "emacs". We installed "homebrew" and with that "wget". 

This week's material was of course quite basic and just an introduction, so I found these quite easy.

***

## Week	2: Navigating the UNIX System

The second week brought us more general information about how to use UNIX systems. We visited the root
directory on our systems. We learned how to modify the permissions of files. Files have read, write and
execute permissions and you can edit them with a few different commands like `chmod`. For example:

`chmod 764 file.txt`

This command let's the user read, write and execute the file, the group read and write the file and others just read
the file.

| Permission class | Read | Write | Execute |
|------------------|:----:|:-----:|:-------:|
|User              |4     |2      |1        |
|Group             |4     |2      |0        |
|Others            |4     |0      |0        |

In the `chmod` command there are three numbers, each determining different user's permissions. The numbers 
represent how many permissions each user has. 1 means execute, 2 means write and 4 means read. So if you want 
to give someone all the permissions, you add it up to 7.

This week we also learned how to compress files using `gzip` and `tar`. Another important thing was how processes
work and how to kill a process with its PID (process ID). Then we learned how to use remote servers like Puhti.

This week's material was still quite simple, so I didn't find them too hard to do. It was slightly harder,
but definitely doable.

***

## Week	3: Basic Corpus Processing

Third week's most important thing was how to process text files. We learned the differences between different
encoding systems, like ASCII and UTF-8. We learned about `grep` which helps to find certain parts of file
by us giving specifications like with regex (regular expressions). For example `grep "\. The" file.txt` would find all the occurances
of new sentences that start with "The" or other words that start that way, like "There". We learned about
CSV (**c**omma-**s**eparated **v**alue) files, which are simple text files that have values separated with
commas, and different programs can make tables out of them. It could look something like this:

> Edna,boston terrier,5 years old  
> Rocky,collie,2 years old  
> Spot,jack russell terrier,11 years old  
> Emmett,shiba inu,7 years old  

And that it would look like this in a table:

| Name   | Breed                | Age          |
|--------|----------------------|--------------|
| Edna   | boston terrier       | 5 years old  |
| Rocky  | collie               | 2 years old  |
| Spot   | jack russell terrier | 11 years old |
| Emmett | shiba inu            | 7 years old  |

We learned some more commands like `tr` (can be used to replace something from the original file,
for example all the commas, and make them in to for example tabs), `uniq` (removes repeated lines and can
count how many times they occur) and `sort` (sorts the contents in numerical or alphabetical order).

This week's stuff was already a bit harder. I was mostly able to do the tasks, but had some difficulties
too.

***

## Week	4: Advanced Corpus Processing

This week we moved onto more advanced corpus processing. We started by reading a bit about `sed` command,
which has a lot of different things it can do. We didn't go through everything, but the most useful to us.
You can for example remove or replace things in text files. An important thing we learned is how to
manipulate a text file in a way that you can create a word frequency list. You can do it by runnig these
commands:

> cat file.txt \| tr -s '\n\r\t' '\n' \| tr -dc "[:alnum:]\n'" \| sort \| uniq -c \| sort -nr 

You can use pipes `|` to put a lot of commands in a row and do everything by once. `cat file.txt`
is used to view the file, but here this is just used to determine that "file.txt" is the specific
file that we want to modify. `tr -s '\n\r\t' '\n'` is used to replace all the different white spaces
with newlines, so that there isn't useless space there. `tr -dc "[:alnum:]\n'"` is meant to delete
all the punctuation. "-d" means delete and "-c" means that you want this command to delete everything
but the things you specify. So there we specify, that we want to keep "[:alnum:]", which means all
letters and numbers. We also want to keep newlines ("\n") and apostrophies ('). Then `sort` sorts
everything to alphabetical order. `uniq -c` will then remove all the same occurances of words
and count them with "-c". Lastly `sort -nr` will sort the words in a reverse numerical order,
and that is how we get a frequency list. We also learned how to modify a file to a sentence
per line format and how to list N-grams, like trigrams, so that a file has all the trigrams
that the original file had.

This week was very interesting, because I have previously used a program that makes me the frequency
list, but it was actually quite simple to do it with just the command line.

***

## Week	5: Scripting and Configuration Files

Scripts were week 5's topic. Scripts can be written to run many commands at the same time,
so that you don't have to run them one by one. This is an example of a script:

![A script](assets/images/pic1.png)

This does the same kind of a thing as the last week's example command, so this makes
a frequency list. `#! /bin/bash` shows the path to the intepreter that inteprets the
rest of the commands on the script. `if [ $# -ne 2 ]` means that if there are not two
variables when using the script, it should echo an error and then exit. But if the two
variables required are given, it goes to the actual commands. `dos2unix` makes the file
to be unix-type. The other commands are explained in the last week's section. `> $2`
defines that the results should be saved as a new file that is given when you run the script.

We also learned how to modify our configuration files. For example we learned how to add
more to our $PATHs, like adding a path so that we can easily use our new scripts.
We learned what are environmental variables, and that you can use them as long as you
are using the same environment. So every time you close your terminal, those variables
disappear, but you can set new variables. You can also make the variables permanent by
adding them to your configuration file. You can also make aliases for your most used
commands. If you for example use the `clear` command a lot, you could set an alias
for it, for example "c", and then just by typing "c" you can use the `clear` command.

I found scripts quite hard. I understand the basic way it works, but the actual code
I was supposed to write so that the script works was quite difficult for me to
understand.

***

## Week	6: Installing and Running Programs

This week's focus was on installing and running programs. We learned how to use the `sudo`
command. With it you don't have to use the root password, just your user password. With
`sudo` you can execute commands as root. We learned how to use package managers to
install programs. Because I have a Mac, I use homebrew. With homebrew it is very easy
to install programs and it always updates itself when you use it. We learned about pip,
which is a package manager for python. You can install programs with it with simple
command: `pip install <program name>`

Another important subject that we learned about was makefiles. This is a very simple
makefile:

> all: say_hello generate
>
> say_hello:  
>         @echo "Hello World"  
>
> generate:  
>         @echo "Creating empty text files..."  
>         touch file-{1..10}.txt  
>
> clean:  
>         @echo "Cleaning up..."  
>         rm *.txt

`all: say_hello generate` means that when you do a command `make all` it does what this
command says, so "say_hello" and "generate". `say_hello` echos "Hello World". `generate`
creates 10 empty files (file-{1..10}. Then when you do a command `make clear`, it echos
"Cleaning up..." and removes all the files that are in the directory.

Week 6 felt a bit easier and more understandable that week 5. Installing was pretty
straight forward, and makefiles took a little bit of time to completely understand,
but it wasn't too difficult.

***

## Week	7: Version Control

This week we learned about git and version control. We first created accounts for
ourselves on GitHub. Then we learned how to set up a git repository. With git you
can save different versions of your project, so that if you noticed that you made
a mistake changing something you made earlier, you can possibly recover the old
data. With git there are a couple of ways to save things. When you just work with
for example a text file, you save it normally on your computer. Then you `git add`
it and then `git commit` it, and that is now one new version. When you have committed
the changes, you can then `git push` it to a remote repository you have. This
website is made with GitHub, so I have my remote repository there, and before any
changes are seen on the website, I have to first `git push` them, and then they
are on my website.

You can also add branches, where you can maybe try something that you're not sure
you will want to keep, and don't want to disturb the project in case the thing you
want to try doesn't work out the way you hoped. This is how you go about it:

* `git branch` - With this you can see what branches you already have. The main branch is
called "master". The branch you're on is marked with a star (*).

* `git branch <branchname>` - This is how you create a new branch.

* `git checkout <branchname>` - When you want to change the branch you're on, you "chekcout"
to it. Now you can work on your experiment.

* `git merge <branchname>` - When you are sure you want to unify the branches, you can
do it with this command. Make sure you are on the branch that you want the experimental
branch to connect to, so in a normal case probably the master branch.

* `git branch -d <branchname>` - Now that you have merged the branches, you can delete
the experimental branch with the "-d" option.

Git seems like a very useful tool, and pretty simple to use too. I didn't feel too
much difficulty learning to use it. I feel like it is something that I really
can use in the future projects.