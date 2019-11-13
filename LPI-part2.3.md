# Topic 2: Finding Your Way on a Linux System

## 2.3 Using Directories and Listing Files

### Lecture: Files and Directories

The hierarchy of storage on the Linux operating system

`cd /` - top/root level dir

`cd -` - go back to last location

### Lecture: Hidden Files and Directories

Hidden from basic listing, preceding their name with a period

### Lecture: Home Directories

Contains user files and directories, under /home

### Lecture: Absolute and Relative Paths

The path to the uniques location of a file or a directory

`/home/cloud_user/file1`

- relative path : **file1**

- absolute path : **/home/cloud_user/file1**

## Hands-On Lab

### Using Directories and Listing Files

*Determine Which File Is the Oldest*
1. To list the directory and sort by date, we use -l for "long listing", -A for "almost all", and -t for "sort by time".
		`ls -lAt ~/Practice/Test/var/log/`

*Determine Which File Is the Largest*

1. To list the directory and sort by file size, we use -l ("long listing") and -S ("sort by file size").
		`ls -lS ~/Practice/Test/var/log/`

*Determine When the File `~/Practice/Test/sos_commands/networking/netstat_-W_-neopa` Was Last Modified*

1. We use a simple -l for "long listing" to view the last modified time and date.
		`ls -l ~/Practice/Test/sos_commands/networking/netstat_-W_-neopa`

Determine When the File `~/Practice/Test/sos_commands/networking/netstat_-W_-neopa` Was Last Accessed

1. To view access times, we use -l  ("long listing") and-u (access time).
		`ls -lu ~/Practice/Test/sos_commands/networking/netstat_-W_-neopa`


### Using Absolute and Relative Paths

*Use Absolute Paths to Move the File*

1. Use cat and redirection to place the contents of the file Practice/Test/free into a new file named value.txt in your home directory.
		`cat /home/cloud_user/Practice/Test/free > /home/cloud_user/value.txt`

*Use Relative Paths to Move the File*

1. Change to the /usr/share directory.
		`cd /usr/share`
2. Use cat and redirection to place the contents of the file Practice/Test/sys/fs/xfs/stats/stats into the newly created file value.txt in your home directory.
		`cat ../../home/cloud_user/Practice/Test/sys/fs/xfs/stats/stats >> ../../home/cloud_user/value.txt`