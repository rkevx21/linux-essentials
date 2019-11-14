# Topic 4: The Linux Operating System

## 4.4 Your Computer on the Network

### Lecture: Internet, Network, and Routers

- **Network** - A group of connected devices that are able to communicate with each other

- **Switch** - Forward packets in the same network

- **Router** - Gateway, forward packets in between network

`ip addr show`

`ping -c 1 example.com`


### Lecture: Querying DNS Client Configuration

- **DNS : Domain Name System**

Maps domain names to their respective IP addresses

`dig www.linuxacademy.com`

Translates an IP address or a hostname into an IP address, translates IP addresses into hostname

- **Configuration**
	
`/etc/resolv.conf` - this configuration file used to determine which hosts to use for DNS queries

`/etc/hosts` - used for statically mapping IP addresses to hostnames

`host <SITE>`

- **DNS Resolution Sequence**

1. `.`
2. `.COM.`
3. `EXAMPLE.COM.`
4. `WWW.EXAMPLE.COM.`

### Lecture: Querying Network Configurations

**Address Configuration**

`ip route show` - show the current routing table

`ip addr show` - show the current addresses

`ifconfig` - view and change the interface configuration

`netstat` and `ss` - view listing services and active connections

`netstat -ntlp` and `ss -ntlp` - numeric, tcp, listening, port#

`netstat -nulp` and `ss -nulp` - numeric, udp, listening, port#

`cat /etc/services | grep 22`

`cat /etc/services | grep 53`

`nmcli` - network manager


## Hands-On Lab

### Locating Network Configuration from the Command Line

*Determine the IP Address*
1. Run the following command:
		`sudo ip addr show`
2. Note the IPv4 and IPv6 addresses in the output.

*Determine the MAC Address*
1. Run the following command:
		`sudo ip addr show`
2. Note the MAC address in the output.

*Determine the Gateway*
1. Show the routing table.
		`sudo ip route show`
2. Note the gateway in the output.

*Determine the DNS Server*
1. Show the DNS nameserver:
		`cat /etc/resolv.conf | grep nameserver`
Note the DNS server in the output.


###  Querying DNS Client Configuration from the Command Line
		
*Determine the Configured DNS Host*

		`cat /etc/resolv.conf`

*Perform a DNS Lookup of www.linuxacademy.com Using the Configured DNS Server*

		`host www.linuxacademy.com`

		`dig www.linuxacademy.com`

*Perform a DNS Lookup of www.linuxacademy.com Using Another DNS Host*

		`dig @1.1.1.1 www.linuxacademy.com`

We could also use:

		`host www.linuxacademy.com 1.1.1.1`

*Test Connectivity to www.linuxacademy.com*

Try ping:

		`ping -c1 www.linuxacademy.com`

Then curl:

		`curl -I www.linuxacademy.com`