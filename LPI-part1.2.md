# Topic 1: The Linux Community and a Career in Open Source

## 1.2 Major Open-Source Applications

### Lecture: Desktop Applications	

**Desktop Application** - open-source application for desktop and office use
- Libre Office
- Open Office
- Mozilla Firefox
- Thunderbird
- Gimp

### Lecture: Server Applications

**Server** - open-source application that provide client services

**Web Server**
- **Apache** - is a hightly popular, free , and open source web server service application. Permits web content to be served by the host, and may use compiled modules to extend the core functionality of the service
- **Nginx** - is a web server that can also be used for reverse proxy, load balancing, mail proxy, and HTTP caching


**Database Server Application**
- **MySQL** - is an open-source relational database management system. Used by many database driven web application.
- **MariaDB**	- a community developed fork of MySQL, claims some performance optimizations and speed improvement and a powerful and feature-rich alternative

**File Sharing Application**
- **Samba**	- open source file sharing software for Linux that permits file sharing with Windows clients throufh native connectivity using Common Internet File System (CIFS)
- **NFS** - Network File System, a distributed system protocol, permitting client hosts to access files and directories over the network as local	storage

**Private Cloud Application**
- **ownCloud** - is client/server suite of application for creating and using hosting services
- **NextCloud** - fork ownCloud, where Fork is simply taking a source coude in creating a parallel project

### Lecture: Development Languages

**Development**	- open-source languages for application development

- **Shell** - a shell script is designed to be run by the command line interpreterr using various scripting languages (Bash)
		for i in {1..100}; do touch newfile_$i; done | rm -f newfile*
				
- **C** - a general purpose inperative programming language designed to be compiled to require minimal runtime support
- **Java** - is a classed-based, object oriented general purpose programming language designed to be compile and run on any system supporting the Java runtime via a Java Virtual Machine (JVM)
- **Javascript** - a technology that enables interactive web pages
- **Perl** - a general purpose Unix scripting langauge "Duct Tape of the Internet"
- **Phyton** - an interpreted, general purpose programming language similar to Perl but with different principles in terms of flexibility
- **PHP** - Hypertext Process, a programming language originally designed for web development


### Lecture: Package Management Tools and Repositories

**Package Management** - How installation packages are tracked and managed

- **dpkg : Debian Package** - package archive format, containing some package metada
- **apt-get : Advanced Package Tool** -  free and open source interface that works with core libraries to handle the installation and removal of software on Debian-based system
- **Repository** - collection of packages
- **rpm : RedHat Package Manager** - package managment system system used by a wide variety of Linux distributions
- **yum : Yellowdog Updater, Modified** -free and open source command line package management utility for RPM-based Linux system


## Hands-On Lab

### Installing an RPM Package


*Install the **htop** RPM Package*

1. The htop RPM package is located in the cloud_user home directory. In order to install the package, we need to elevate our permissions.
Use the following command to install the package:
		sudo rpm -i htop-2.2.0-3.el7.x86_64.rpm

*Run the **htop** Application*
1. Now that htop is installed, we can run it with the htop command.
		htop
	This utility shows us system load and running processes.
2. We can exit the application by pressing the Q key.

*Remove the **htop** Package*

1. Use RPM to remove the htop package.
		sudo rpm -e htop

### Installing a DEB Package

Check version
		
		cat /etc/issue

*Install the **htop** DEB*

1. The htop DEB package is located in the cloud_user home directory. In order to install the package, we need to elevate our permissions.
Use the following command to install the package:
		sudo dpkg -i htop_2.0.2-1_amd64.deb

*Run the **htop** Application*
1. Now that htop is installed, we can run it with the htop command:
		htop
This utility shows us system load and running processes.
2. Press Q to exit the application.

*Remove the **htop** Package*
1. Use dpkg to remove the htop package:
		sudo dpkg --remove htop

### Compiling from Source

Check version

		cat /etc/redhat-release

*Locate and Extract the Source File Archive*
1. The source file archive has been placed in the /home/cloud_user directory and must be extracted prior to use. Use the following command to extract the archived .tar file in /home/cloud_user :
		tar xzf htop-2.2.0.tar.gz
This extracts the archive into the newly created folder htop-2.2.0 within /home/cloud_user.

*Run the Configure Script to Prepare the Source for Installation*
1. Change to the htop source directory.
		cd htop-2.2.0
2. Run the configuration script to prepare the source.
		./configure

*Compile the Source Code into Usable Binaries*
1. Compile the source code.
		make
This command will display output to the screen as it compiles the source code into binaries.

*Install the Binaries*
1. Once the source code has compiled, run the following command to install the resulting binaries on the system:
		sudo make install

*Run the **htop** Utility to Verify That Installation Was Successful*
1. When the binaries are installed, execute the htop command to verify that the installation was successful.
		htop

*Remove the Installation*
1. Removing the installation is similar to installation. From the source directory /home/cloud_user/htop-2.2.0, execute the following command:
		sudo make uninstall
