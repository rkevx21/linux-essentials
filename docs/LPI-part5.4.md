# Topic 5: Security and File Permissions

## 5.4 Special Directories and Files

### Using Temporary Files and Directories

Creating and working with temporary files and folders

**Cleared upon system reboot**

`/tmp`

All content is cleared upon system reboot. This directory is used by programs or scripts that requires files or directories.

**Cleared every 30 days (depending on distro)**

`/var/tmp`

All contents persists through a system boot. This directory is used by programs or scripts that require temporary files or directories with more persistence than `/tmp` offers

**Create a temporary file or directory**

`mktemp [options] [name template]`

Can be use to create ad hoc files and directories with a randomized file name portion. These files are not automatically removed

### Symbolic Links

**Ceating and working symbolic links**

Creating a symbolic link to a file or directory

`ln -s [target] [link name]`

## Hands-On Lab

### Using Temporary Files and Directories

*Retrieve and Unpack the Archive*
1. Change to the /tmp directory.
		`cd /tmp`
2. Use wget to retrieve the file.
		`wget https://github.com/mscjr/LA/raw/master/RH342/sosreport-ip-10-0-1-11-2019-03-22-wxoxhnk.tar.xz`
3. Unpack the archive.
		`tar xf sosreport-ip-10-0-1-11-2019-03-22-wxoxhnk.tar.xz`

*Create a Temporary File from the Directory Listing*
1. Create a temporary file from a recursive directory listing of the archive folder.
		`tmp_file=$(mktemp)`
		`ls -R sosreport-ip-10-0-1-11-2019-03-22-wxoxhnk/ >> $tmp_file`

*Move the `version.txt` File to a More Persistent Temporary Directory*
1. Move the version.txt file to /var/tmp.
		`mv sosreport-ip-10-0-1-11-2019-03-22-wxoxhnk/version.txt /var/tmp`



### Using Symbolic Links

*Create the ~/ bin Directory and Add it to the PATH*
1. Make the ~/bin directory.
		`mkdir bin`
2. Add ~/bin to the $PATH environment variable.
		`echo 'PATH=$HOME/bin:$PATH' >> .bashrc`

*Create the Symbolic Links*
1. Create a symbolic link ("symlink") for rpm_verify.
		`ln -s /usr/lib/rpm/rpmdb_verify bin/rpm_verify`
2. Create a symlink for rpm_dump.
		`ln -s /usr/lib/rpm/rpmdb_dump bin/rpm_dump`
3. Create a symlink for rpm_load.
		`ln -s /usr/lib/rpm/rpmdb_load bin/rpm_load`

*Test the Symbolic Links*
1. Verify that the rpm_verify symlink works.
		`rpm_verify /var/lib/rpm/Packages`