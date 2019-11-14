# Topic 4: The Linux Operating System

## 4.3 Where Data Is Stored

### Lecture: Programs and Configuration

Common locations for system and configuration data

**System Configuration**

- System Boot Configuration: `/boot`

Contains boot loader configuration files and parameters, Linux kernel, and initial RAM disk

- Partition Mount Points: `/etc/fstab`

Contains a list of partitions to mount automatically and where they mount in the filesystem

- User Attribute: `/etc/passwd`

Contains a list of local users and their attributes

- Group: `/etc/group`

Contains a list of local users and attributes

- Hosts File: `/etc/hosts`

Contains a list of IP addresses and the hostname we want the system to associate with them

`/etc/resolv.conf` - specified the nameserver

- Application Configuration: `/etc/<APPLICATION>`

Applications place their respective configuration files in the /etc directory, normally as a .conf file

`/sys` - ram based filesystem

`mount | grep sysfs` - export information about various kernel subsystems hardware devices and associated drivers


### Lecture: Processes

**Data used by running processes**

- Process ID: `PID`

All process are given an ID number

- Process Data: `/proc/<PID>/`

Process data is stored in /proc/ within individual /<PID> folders

- Viewing Running Process

`ps aux` - list all processes (BSD format)

`ps -ef` - list all processes (Linux format)

`top`	- utility to view running processes and resource usage

**Devices**

- Device Data: `/sys`

Provides system information regarding attached hardware

- Device Filter: `/dev`

Contains device files (normally block or character devices)


### Lecture: System Messaging

Viewing and accessing system messaging

**Kernel Messaging**

- Kernel Ring Buffer

Holds messages related to the operation of the kernel

`dmesg | grep sda`

`dmesg | grep -1 usb`

`dmesg | grep -1 memory`

### Lecture: Logging

Common locations for system and applocation log data

**Log Daemon**

- System Logging Protocol: `syslog`, `rsyslogd`

Syslog is a service performs log message collection

**Common Logs**

`/var/log/messages` - general system logs and messages

`/var/log/syslog` - for Debain-based systems

`/var/log/auth.log` - authentication logs

`/var/log/secure` - for Red Hat-based systems

`/var/log/boot.log` - system boot logs

`/var/log/cron.log` - cron job logs

`/var/log/ker.log` - kernel logs

`/var/log/faillog` - authentication failure logs

## Hands-On Lab

### View Running Processes from the Command Line


*Determine How Many Processes Are Currently Running*
1. Run the following command:
		`ps aux | grep -v grep | wc -l`

*Determine the Current System Load*
1. Run one of the following commands:
		`uptime`
		`cat /proc/loadavg`
		`top`

*Determine How Many Processes Are Running as `cloud_user`*
1. Run one of the following commands:
		`ps -u cloud_user | wc -l`
		`ps aux | grep -v grep | grep -E "^cloud" | wc -l`

*Determine the PID of the `xfce4-session` Process*
1. Run the following command:
		`ps aux | grep xfce4-session | grep -v grep`

*Determine How Many Threads the `xfce4-session` Process Is Using*
1. Determine the PID:
		`ps aux | grep xfce4-session | grep -v grep`
2. View the current threads reported in the PID's status:
		`cat /proc/PROCESS_PID/status | grep Threads`

*Write a Small Shell Script that Returns the Number of Threads in a Process*
1. Create a new file named /home/cloud_user/bin/threads.sh, and add the following script:


		`#!/bin/bash`

		`if [ -n $1 ]`

			`then`

			`_pid=$(ps aux | grep -E "$1\$" | grep -v grep | grep -v threads.sh | awk '{print $2}')`

			`cat /proc/$_pid/status | grep Threads`

		`fi`

### Viewing System Logs


*Attempt to `curl` the Address on the Local Host*
1. Run the following command:
		`curl -I localhost`

*Determine How Many Times 10.0.1.10 Has Accessed the Website*
1. Run the following command:
		`sudo cat /var/log/httpd/access_log | grep -E "^10.0.1.10" | wc -l`

*Attempt to Reach the Web Server via `http://PUBLIC_IP/index.html`*
1. Run the following command:
		`sudo tail -f /var/log/httpd/access_log`
2. Attempt to reach the website via public IP (not 10.0.1.10) from your computer as http://PUBLIC_IP/index.html.

*Find the New Entry in the Log*
1. Run the following command to view the entry that was appended to the end of the log:
		`sudo tail -f /var/log/httpd/access_log`
Note the "200" after "HTTP/1.1"; this signifies a valid destination.

*Attempt to Reach the Web Server via `http://PUBLIC_IP/server.html`*
1. While running tail on the access log, attempt to reach the /server/html path.
		`curl http://PUBLIC_IP/server.html`
Note the 404 status code; this signifies the path did not resolve to a valid page.
