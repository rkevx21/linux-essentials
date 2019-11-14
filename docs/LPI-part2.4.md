# Topic 2: Finding Your Way on a Linux System

## 2.4 Creating, Moving, and Deleting Files

### Lecture: Files and Directories

**Directory**

- make - `mkdir <NAME>`
- copy - `cp -r <SOURCE> <DESTINATION>`
- move - `mv <SOURCE> <DESTINATION>`
- delete - `rm -r <DIRECTORY>`

**Files**

- create - `touch <NAME>`
- copy - `cp <SOURCE> <DESTINATION>`
- move - `mv <FILE> <NEW LOCATION>`
- delete - `rm <FILE>`

### Lecture: Case Sensitivity

` touch newfile` is not equal to `touch Newfile`

`lsblk` , important sda (disk)

`cat fstab` , ext4 (case sensitive)

### Lecture: Simple Globbing

Use to match pattern in filenames or text by using wildcard character to create a pattern
					
- `?` - match any single character

`file1 file2 file3 file4 file File`

`ls file?` it will display `file1 file2 file3 file4`
								
`ls ????` it will display `file File`

- `*` - match any number of character(s)
					
file1 file2 file3 file4

`ls file*` it will display `file1 file2 file3 file4`

`ls *4` it will display `file4`


- `[]` - match character from a range

`file1 file2 file3 file4`

`ls ????[1-3]` will display `file1 file2 file3`

`ls *[[:digit:]]` will display `file1 file2 file3 file4` - returns all wth digit/number at last character

- `^` - uset to match starting character
- `$` - use to match ending character
- `{}` - use to match more than one pattern
- `|` - used for applying more than one condition

## Hands-On Lab

### Creating, Moving, and Deleting Files

*Copy/Move the Requested Files and Folders*
1. Copy ~/Practice/Test to ~/Report/.
		`cp -R Practice/Test/ Report`
2. Rename and move ~/Report/sos_commands/filesys/mount_-l to ~/Report/mounts.txt.
		`cd Report/`
		`mv sos_commands/filesys/mount_-l mounts.txt`

*Remove the Requested Files and Folders*
1. Remove etc/selinux/.
		`rm -rf etc/selinux/`
2. Remove var/log/boot.log.
		`rm -rf var/log/boot.log`
3. Remove anything in proc/ that is or starts with a number.
		`rm -rf proc/[1-9]*`
4. Remove anything in etc/ that ends in .conf.
		`rm -rf etc/*.conf`
5. Remove anything in sys/module that starts with ip6t.
		`rm -rf sys/module/ip6t*`

*Create a New File in `~/Report/`*
1. Create a new file named Done.txt in ~/Report/.
		`touch Done.txt`