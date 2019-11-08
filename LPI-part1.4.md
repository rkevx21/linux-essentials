# Topic 1: The Linux Community and a Career in Open Source

## 1.4 ICT Skills and Working in Linux

### Lecture: Desktop Skills

Using the Linux Desktop, config, options, web usage, and privacy

**Linux Desktop Environments**
	
- LXDE
- XFCE
- Mate
- Cinnamon
- Gnome
- Unity
- KDE

### Lecture: Getting to the Command Line
	`ssh USER@REMOTE_IP`

### Lecture: Industry Uses of Linux, Cloud Computing, and Virtualization

*How linux is used in virtualization and clound computing*

Virtualization and Cloud Computing have changed shaped of modern computer workloads, and Linux has been the forefront of this digital transformation

- VMVare
- VirtualBox

**Virtualization** - physical computer

**The Cloud** - software and services that run and are available on the internet

## Hands-On Lab

### Determining Which Distribution Is Running on a Host
		
*View the Release Files*
1. We can view the release files by using globbing to pick up every file that contains the word "release" in the /etc/ directory.
		`cat /etc/*release*`

*View the Issue Files*
1. We can view the issue files by using globbing to pick up every file that contains the word "issue" in the /etc/ directory.
		`cat /etc/*issue*`

*Run a Utility to Determine the Linux Distribution*
1. We can use a couple of utilities to determine the distribution. We can either use 
		`lsb_release -a` 
	or for systemd-based systems, we can use 
		hostnamectl