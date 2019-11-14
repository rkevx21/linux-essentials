# Topic 3: The Power of the Command Line

## 3.2 Searching and Extracting Data from Files

### Lecture: Command Line Pipes

Process of taking the output from one command as the input to another command

- **grep** - searches any given input files, selecting lines that match one more more partners

`ls | grep 1]`

### Lecture: I/O Redirection
	
Use to feed input to a command line from a file, or to send the ouput of a file

###  Lecture: Basic Regular Expressions

**regex** - used to match patterns in text, similar to globbing

- Match Start of Line `"^Apple"`
- Match End of Line `"Apple$"`
- Match Start and End of Line `"^Apple$"`
- Match Either String or Character `"Apple|Ball"`
- Match an **A** followd by zero or more **ps**  followed by **le** `"Ap*le"`
- Match an **A** followd by one or more **ps**  followed by **le** `"Ap+le"`
- Match an **A** followd by maybe or more **ps**  followed by **le** `"Ap?le"`
- Match an **A** followed by a **p** through **z** follwed by **le** `Ap[p-z]le`

## Hands-On Lab

### Command Piping and Redirection

*Determine the Number of Files and Folders in `/usr/share`*
1. Run the following commands:
		`ls /usr/share/ | wc -l`
		`ls /usr/share/ | wc -l > ~/value.txt`

*Determine the Number of Unpacked Entries in `/var/log/dpkg.log`*
1. Run the following commands:
		`cat /var/log/dpkg.log | grep unpacked | wc -l`
		`cat /var/log/dpkg.log | grep unpacked | wc -l >> ~/value.txt`

*Determine the Total Number of Entries in `/var/log/dpkg.log`*
1. Run the following commands:
		`cat /var/log/dpkg.log | wc -l`
		`cat /var/log/dpkg.log | wc -l >> ~/value.txt`