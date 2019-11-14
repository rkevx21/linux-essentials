# Topic 5: Security and File Permissions

## 5.3 Managing File Permissions and Ownership

### File and Directory Permissions and Ownership

	7	5	5
	rwx	r-x	r-x
	user    group   everyone

**Numberic Permission**

`7` - Read, write, execute

`6` - Read, write

`5` - Read, execute

`4` - Read

`3` - Execute, write

`2` - Write

`1` - Execute

`0` - No permissions

**chown** - change ownership
			
`chown [options] <user>:<group> <file>`

**chmod** - change mode

`chmod [options] <permissions> <file>`

Directory Permission (Execute = Enter Directory)

Directories requires execute permissions in order to be entered by the user, group, or everyone

## Hands-On Lab

### File Ownership and Permissions

*Lock Bill's, Susan's, and Juan’s Accounts*
1. Run the following command:
		`for i in bill susan juan; do sudo passwd -l $i; done`

*Create Accounts for Nancy, Greg, and Jeremy*
1. Run the following commands:

`sudo useradd -m nancy`

`sudo useradd -m greg`

`sudo useradd -m jeremy`

*Remove Bill as a User and Transfer Ownership of his Home Directory*
1. Remove the user bill.
		`sudo userdel bill`
2. Change the ownership of Bill's home directory (recursively) to the user nancy and the group jason.
		`sudo chown -R nancy:jason /home/bill`
3. Change the mode of the directory to grant read and execute permissions to the group.
		`sudo chmod g+rx /home/bill`

*Remove Susan as a User and Transfer Ownership of her Home Directory*
1. Remove the user susan.
		`sudo userdel susan`
2. Change the ownership of Susan's home directory (recursively) to the user greg and the group jason.
		`sudo chown -R greg:jason /home/susan`
3. Change the mode of the directory to grant read and execute permissions to the group.
		`sudo chmod g+rx /home/susan`

*Remove Juan as a User and Transfer Ownership of His Home Directory*
1. Remove the user juan.
		`sudo userdel juan`
2. Change the ownership of Juan's home directory (recursively) to the user jeremy and the group sally.
		`sudo chown -R jeremy:sally /home/juan`
3. Change the mode of the directory to grant read and execute permissions to the group.
		`sudo chmod g+rx /home/juan`