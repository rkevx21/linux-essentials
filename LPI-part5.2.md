# Topic 5: Security and File Permissions

## 5.2 Creating Users and Groups

### Lecture: User and Group Commands

- **Creating New Users**

**useradd** - a utility that is use to add or create users. Options are available for specifying the UID, GID, home directory, and group membership 
		
`useradd [options] <username>`

- **Boilerplate files and folders for new accounts**
	
Contents are automatically copied when a new user's home directory is created via `useradd` utility

`/etc/skel`

- **Update a user's password**

**password** - a utility may be use to update the current user's password or another user's with sufficient priviledges

`password <username>`

- **Creating new groups**

**groupadd** - a utility is use to add or create groups

`groupadd [options] <groupname>`

`sudo usermod -a -G <groupname> <username>` - add user to a group

- **Set usergroup to add sudo/root permission**

`sudo visudo`

add `%<groupname> ALL=(ALL:ALL) ALL`

`sudo cat /etc/sudoers`

In group, the 1st in the list , will be the initial group use when creating a file


### Lecture: User IDs

**Numeric ID** - all local users given an identification number that is stored along which the corresponding username in `/etc/passd`

`UID 0 `- always the `root` account

`UID 1` - 99 - traditionally reserved for system users

`UID 100+` - standard users (same distibutions start higher)

`UID 65534` - reserve for the user `nobody`

**Remote Users** - typically, a range of UIDs is reserver for non local users in order to prevent UID collisions with local users

## Hands-On Lab

### Creating Users and Groups from the Command Line

*Create the Required Users*
1. Run the following command:
		`for i in jen william matt sam anne danny kate bruce; do sudo useradd -m $i; done`

*Create the Required Groups*
1. Run the following commands:

`sudo groupadd management`

`sudo groupadd sales`

`sudo groupadd operations`

*Add Members to the Appropriate Groups*
1. Add jen to all groups.
		`for i in management sales operations ; do sudo usermod -a -G $i jen; done`
2. Add william to all groups.
		`for i in management sales operations ; do sudo usermod -a -G $i william; done`
3. Add the users matt, sam, anne, and danny to the sales group.
		`for i in matt sam anne danny; do sudo usermod -a -G sales $i; done`
4. Add the users kate and bruce to the operations group.
		`for i in kate bruce; do sudo usermod -a -G operations $i; done`
5. Run one of the following commands to verify that group membership has been configured correctly for all users:
		`tail -n3 /etc/group`
		or
		`for i in jen william matt sam anne danny kate bruce; do groups $i; done`


### Working with User and Group IDs

*Determine the UID Scheme*
1. Run the following command:
		`cat /etc/passwd`
2. Determine the UID range for system users (root, chrony, etc.).
3. Determine the UID range for standard users (cloud_user, jbillings, etc.).
4. Determine the absolute highest UID value for the current users.
5. Choose a higher value for where UIDs on a remote host should begin.

*Determine the GID Scheme*
1. Run the following command:
		`cat /etc/group`
2. Determine the highest GID value.
3. Choose a higher value for where GIDs on a remote host should begin.