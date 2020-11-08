---
layout: default
---

## Command line tools for linguistis -course

Introduction to the course

***

## Week 1

In the first week we started by learning how to set up a command line environment on our computers.
We learned some of the basic commands (like `mv` to move or rename files or `rm` to remove them) and how
to navigate the directories and files on our computer using the command line (with the `cd` command).
We went over how to use a text editor called "emacs". We installed "homebrew" and with that "wget". 

This week's material was of course quite basic and just an introduction, so there isn't that much more.

***

## Week	2

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

***

## Week	3

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

***

## Week	4

This week we moved onto more advanced corpus processing. We started by reading a bit about `sed` command,
which has a lot of different things it can do. We didn't go through everything, but the most useful to us.
You can for example remove or replace things in text files. An important thing we learned is how to
manipulate a text file in a way that you can create a word frequency list. You can do it by runnig these
commands:

> cat file.txt | tr -s '\n\r\t' '\n' | tr -dc "[:alnum:]\n'" | sort | uniq -c | sort -nr 

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

***

## Week	5

This week...

***

## Week	6

This week...

***

## Week	7

This week...