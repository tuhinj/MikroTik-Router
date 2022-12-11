:::::::::Steps to set up DHCP Server on Ubuntu::::::::

1. Install DHCP Server::
	- sudo apt update && sudo apt upgrade -y
	- sudo apt install isc-dhcp-server
2. Configure the DHPC Server::
 Backup Original Configuration file:
	-sudo mv /etc/dhcp/dhcpd.conf{,.backup}
	-sudo mv /etc/dhcp/dhcpd.conf /etc/dhcp/dhcpd.conf.backup
 Create and edit the new configuration file:
	-sudo nano /etc/dhcp/dhcpd.conf
 Assigning Random IP Addresses from a pool:
 	"
# a simple /etc/dhcp/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
authoritative;
 
subnet 192.168.1.0 netmask 255.255.255.0 {
 range 192.168.1.100 192.168.1.200;
 option routers 192.168.1.254;
 option subnet-musk 255.255.255.0;
 option domain-name-servers 192.168.1.1, 8.8.8.8;
 option domain-name "mydomain.example"
}
#option domain-name "mydomain.example";

	"

 According to this configuration:

=> The default lease time for a client is 10 mins(600 seconds) and the maximum lease time is 2 hrs(7200 seconds).
=> This DHCP Server is the official server for the local network. (indicated by authoritative).
=> subnet your present ip address subnet (Ex:192.168.43.0), and net
=> The Server will hand over the IP Address from the range 192.168.43.100 to 192.168.43.200.
=> The server will also “advise” the client to use 192.168.43.254 as the default-gateway and 192.168.43.1 and 192.168.43.2 as its DNS servers.
=>You may also include a domain name.

3. Restart DHCP server and check status:::
	- sudo systemctl restart isc-dhcp-server
	- sudo systemctl status isc-dhcp-server
	*check dhcp lease::
	- dhcp-lease-list


** Add a DHCP Client...


*Check again lease list
	- dhcp-lease-list
	


