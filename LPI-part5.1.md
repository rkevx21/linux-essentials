# Topic 5: Security and File Permissions

## 5.1 Basic Security and Identifying User Types

### Lecture: Root and Standard Users

**Standard Users (Standard Unpriviledged Accounts)**

Limited permissions for view system configurations, and no permission for modifying system configuration.
May be granted the ability to perform priveledged actions using `sudo`.

`sudo` - provides a mechanism whereby a user account is permitted the ability to run command with elevated permissions

`cat /etc/groups | grep [user]` - check user groups

**Root Users (The administrative account for the system)**

Has full access to all permissions on the system, and used for system level administration taks.

`sudo su -` - change to root user

`cat /etc/password` - [Username]:[Password]:[User ID]:[Group ID]:[GECOS]:[Home Directory]:[Login Shell]

`cat /etc/shadow` - [Username]:[Password]:[lastchange]:[Minimum]:[Maximum]:[Warn]:[Inactive]:[Expire]

`cat /etc/group` - [Group]:[Password]:[Group ID]:[Group List]

`groups [username]` - check user groups list

	
### Lecture: System Users

**System Users (Application Service Accounts)**

Are generally deployed when application are installed, their home directories are set to applocation folders, and they normally do not jave a login shell. 
The purpose of having discrete users is to separate functional priviledges from other applications and services

- Check apache user
		
`ss -nltp`

check PID of apache under port 80

`ps aux | grep [PID]`

`cat /etc/password | grep www-data`

## Hands-On Lab

### User Accounts

*Determine What Groups sysuser Belongs To*
1. Run one of the following commands:

`id sysuser`

`groups sysuser`

`cat /etc/group | grep sysuser`

*Determine sysuser’s Home Directory*
1. Run one of the following commands:

`getent passwd sysuser`

`cat /etc/passwd | grep sysuser`

*Determine sysuser’s Login Shell*
1. Run one of the following commands:

`getent passwd sysuser`

`cat /etc/passwd | grep sysuser`