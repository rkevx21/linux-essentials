# Topic 2: Finding Your Way on a Linux System

## 2.1 Command Line Basics

###	Lecture: Basic Shell

The standard Linux shell (BASH) is both a command line interpreter and a programming language

`~` - home directory

`STDIN` - standard input

`STDOUT` - standard output

`STDERR` - standard error

`$` - user

`#` - root

### Lecture: Command Line Syntax

As the shell input is read, it follows a sequence of operations, ignoring comments (#) and divvying the input words and operators

`ls -lsah` - longlisting-size-all-humanreadable

`ls -A` -  A removes . and .. in the list

### Lecture: Variables

Contains a number, a character, or string of characters. These variables do not need to be declared, nor are there data types. They are simple assigned.

`$PS1` the primary prompt string, [user, host, working directory]

### Lecture: Quoting

Used to disable special treatment of certain characters and words, as well as to prevent parameter expansion and preserve what is qouted

- **Escape Character**

A non qouted backslash `\` is the bash escape character and preserves the literal value of the next folowing character with the single exception of newline

`var1=Some value` - this will show error

`var1=Some\ value` - `echo $var1` will output `Some value`

- **Single Qoutes**

Single qoutes **'** preserve the literal value of every character contained within the qoutes, including the escape character

`var1=Some value`
`echo 'this is $var1'` - will output `this is $var1`

`echo 'this is\ $var1'` - will output `this is\ $var1`

- **Double Qoutes**

Double qoutes `""` preserve the literal value of most characters contained within the qoutes, exceptions include `$` for variables, `'` for single qouting, `\` for escaping a character

`echo ''This is a 'qoute''` - will output `This is a qoute`

`echo "This is a 'qoute'"` - will output `This is a 'qoute'`

## Hands-On Lab

### Command Line Basics

*Determine the Current Working Directory*
1. The command prompt povides very little information upon login to the system. Use the following command to determine your current working directory:
		`pwd`
2. Change your working directory to your user's home directory.
		`cd ~`

*Determine Which Users Are Currently on the System and the Last Users to Log In*
1. Verify that you are the only user logged in to the system with the following command:
		`w`
2. Determine which users last logged in to the system, as well as the last time the system was booted by running the following command:
		`last`

*Record Your Findings in **/home/cloud_user***
1. Create a record of your findings by writing the output of the previous commands into a new file in the cloud_user home directory. From the /home/cloud_user directory, run the following commands:
		`w > log.txt`
		`last >> log.txt`
2. View the contents of the file you created using the following command:
		`cat log.txt`

### Command Line Variables

*Examine the Current **$PATH** Variable*
1. List the current environment variables, and locate the $PATH variable.
		`env`
2. Examine the $PATH variable.
		`echo $PATH`

*Append the Path to the **scripts** Directory to the $PATH Variable*
1. Since the path to our scripts directory is missing, we need to append it to the $PATH variable. We can do so with the following command:
		`PATH=$PATH:$HOME/scripts/`
2. We should now be able to run the script without specifying the path to it.

*Make the New **$PATH** Persist*
1. If we log out, we'll lose our ability to run the script without specifiying the path. So we need to make our change permanent. We can do so on this Ubuntu 16.04 system by modifying the `~/.profile` file.
		`echo 'PATH="$PATH:$HOME/scripts"' >> ~/.profile`


### Command Line Quoting

*Set **variable1***
1. Set variable1 to **This is 'just' a "test".**
		`variable1="This is 'just' a \"test\"".`
2. Write the variable to a new file named value.txt.
		`echo -e $variable1 > value.txt`

*Set **variable2***
1. Set variable2 to **This is a backslash "\" and this is a single quote .'**
		`variable2="This is a backslash \"\\\" and this is a single quote '."`
2. Append variable2 to the value.txt file.
		`echo -e $variable2 >> value.txt`

*Set **variable3***
1. Set variable3 to **3 double quotes """, and 3 single quotes ''', and three backslashes \\\.**
		`variable3="3 double quotes \"\"\", and 3 single quotes ''', and 3 backslashes \\\\\\\\\."`
2. Append variable3 to the value.txt file.
		`echo -e $variable3 >> value.txt`

*Set **variable4***
1. Set variable4 to **This is what a newline character looks like \n, it will create a new line.**
		`variable4="This is what a newline character looks like \\\n, it will create a new line."`
2. Append variable4 to the value.txt file.
		`echo -e $variable4 >> value.txt`
