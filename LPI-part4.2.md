# Topic 4: The Linux Operating System

## 4.2 Understanding Computer Hardware

### Lecture: Hardware

The physical components used for computing

- **Central Processing Unit (CPU)**

Process computer functions and performs calculations

`[ cat /proc/cpuinfo ]`

- **Random Access Memory (RAM)**

High performance, volatile storage

`[ free -m ]`

- **Secondary Storage (HDD/SSD/DVD)**

Persistent storage for data not currently in use

`[ df -h | grep -v */dev/loop* ]`

- **Network Interface Card (NIC)**

Permits connections to a network

`[ ifconfig ]`

- **Input Devices (Mouse/Keyboard)**

Send data into the computer via human interaction

- **Output Devices (Monitor)**

Send information from the computer to the user

- **Drivers**

Reside in the running kernel (or are loaded as a module) and enable the operating system to use the hardware


## Hands-On Lab

### Getting Hardware Information from the Command Line

*Determine How Much Storage Is Available*
1. Run the following command:
		`df -h`

*Determine the Number of CPUs/Cores*
1. Run any of the following commands:
		`sudo lshw`
		`cat /proc/cpuinfo`
		`lscpu`

*Determine the CPU Speed*
1. Run one of the following commands:
		`sudo lshw`
		`cat /proc/cpuinfo`

*Determine How Much RAM Is Installed*
1. Run any of the following commands:
		`sudo lshw`
		`cat /proc/meminfo`
		`sudo dmidecode`

*Determine How Much Swap Is Being Used*
1. Run the following command:
		`free -m`

*Determine the BIOS Version*
1. Run one of the following commands:
		`sudo lshw`
		`sudo dmidecode`
