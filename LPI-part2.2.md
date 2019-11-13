# Topic 2: Finding Your Way on a Linux System

## 2.2 Using the Command Line to Get Help

### Lecture: Man Pages

Traditional form of sofware documentation found on UNIX systems. They are included with the software they document

`man <command>`

`echo $?` - check exit status

`/` search in man page ; e.g. `/backslash`, `/-k`

`man -k block` == `apropos block`

### Lecture: Info Pages

Provides more detailed information about a command than its respective page, pages in a book.

`info <command>`

`/` search, `P` previous, `N` next, `Up` up

## Hands-On Lab

### Using the Command Line to Get Help

*Determine How Many Lines the File Contains*
1. The documentation found in the man and info pages suggests that the -l option may be used to determine the total number of lines.
		`wc -l longfile.txt`
2. Run the command and output the result into a new file named value.txt.
		`wc -l longfile.txt > value.txt`

*Determine the Number of Characters on the Longest Line*
1. The documentation found in the man and info pages suggests that the -L option may be used to determine the number of characters on the longest line.
		`wc -L longfile.txt`
2. Run the command and append the result to the value.txt file.
		`wc -L longfile.txt >> value.txt`

*Determine the Total Number of Characters in the File*
1. The documentation found in the man and info pages suggests that the -m option may be used to determine the total number of characters in the file.
		`wc -m longfile.txt`
2. Run the command and append the result to the value.txt file.
		`wc -m longfile.txt >> value.txt`
