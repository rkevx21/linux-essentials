# Topic 3: The Power of the Command Line

## 3.3 Turning Commands into a Script

### Lecture: Basic Shell Scripting

Essentials of creating and running a shell script. Absolute path and relative path

`#!bin/bash` - interpretor to be used by the shell script


### Lecture: Awareness of Common Text Editors (vi and nano)

Cli applicatop for working with text files

**VIM**

`i` - insert at cursor

`I` -  Quit VIM

`o` - append the line under cursor

`:w` - frite file

`:q` - quit VM

`:wq` - write and quit 

**Nano**

`CTRL + x` - Exit, will prompt to save

`CTRL + o` - Exit, will prompt to save

## Hands-On Lab

### Turning Commands Into a Bash Script


*Determine What Options Should Be Used with the **ssh** Command*
1. View the man page for the ssh command, and determine the option to use to disable host key checking.
		`man ssh`
2. The syntax to use is:
		`ssh -o StrictHostKeyChecking=no user@host`

*Build a Script from the Required Commands*
1. Create a bin folder in cloud_user's home directory.
		`mkdir bin`
2. Use vim or nano to create the file lab.sh in the new bin folder.
		`vim bin/lab.sh`
3. Start with the shebang at the top of the file.
		`#!/bin/bash`
4. Add a line to set a variable for the login user.
		`login_user=cloud_user`
5. Add a line to ssh using the variable from above and taking the first parameter as the host address.
		`ssh -o StrictHostKeyChecking=no $login_user@$1`

6. The completed script should look like this:
		`#!/bin/bash`
		`login_user=cloud_user`
		`ssh -o StrictHostKeyChecking=no $login_user@$1`

Execute and Verify the Script
1. Save the file, and make it executable.
		`chmod u+x bin/lab.sh`
2. Run the script, passing 10.0.1.10 as the first parameter to be assigned to $1.
		`./bin/lab.sh 10.0.1.10`
3. It should immediately prompt for cloud_user's password and not prompt for RSA fingerprint acceptance.

Add the New **bin** Directory to the **PATH** Variable
1. Append to the .bashrc file in cloud_user's home directory to add the new bin folder to the PATH environment variable.
		`echo 'PATH="$HOME/bin:$HOME/.local/bin:$PATH"' >> .bashrc`
2. Source .bashrc to pick up the change.
		`source .bashrc`
3. Verify that you can run lab.sh without specifying the path to the script.
		`lab.sh 10.0.1.10`  
