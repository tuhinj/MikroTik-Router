Basic Configration:
a) WAN an LAN IP assigning (address)
b) Gateway IP assining (Router)
c) DNS IP assigning and NAT rule creation (DNS)

....................................................................
1. Microtik Basic Configration (LAN DHCP, WAN [DHCP Client/ Static IP/ PPPOE Client]).

	::LAN DHCP::
	>>> ip > address > plus button > creat static ip > select LAN interface > ok

	::DHCP Client::
	>>> ip > DHCP client > plus button > select WAN interface > ok
	
	::Static IP:::
	>>> ip >>> address > plus button > IP (ISP provide ip)  > select WAN interface > ok
	>>> ip > routers > plus button > add getway(ISP provide ip address) > ok
	
	
	::PPPOE Client::
	>>> ppp / interface > plus button > general > select interface "WAN' > Dial out (ISP provide 'username' 'password', tikemark 'use peer DNS' > ok
	
....................................................................
2. Configure Microtik as a Router where WAN is useing Static IP and LAN is useing DHCP server.

	::Static IP:::
	>>> ip >>> address > plus button > IP (ISP provide ip)  > select WAN interface > ok
	>>> ip > routers > plus button > add getway(ISP provide ip address) > ok
	
	::LAN > DHCP Server::
	>>> ip > DHCP server > DHCP setup > select LAN interface and configration
	
...................................................................
3. Configure Microtik router as a Gateway where WAN haveing DHCP protocol, and configure LAN network.

	::WAN getway::
	>>> configer WAN interface (static ip or DHCP client)
	>>> IP > routers > plus button > add WAN ip in getway > ok
	::Assigning DNS IP::
	>>> IP > DNS > plus button > add getway (8.8.8.8 or 8.8.4.4)
	
	
	::LAN configer::
	>>> ip > DHCP server > DHCP setup > select LAN interface and configration

4. Configure PPPOE Client on WAN interface, and implement local network(Using DHCP or PPPOE).

	::PPPOE Client::
	>>> ppp / interface > plus button > general > select interface "WAN' > Dial out (ISP provide 'username' 'password', tikemark 'use peer DNS' > ok
	
	:: NAT rull::
	>>> ip > firewall > NAT > General (Chain"srcnat",out.interface"pppoe.out interface") > Action (masquerade) > ok
	
..................................................................
5. Design ISP for (100Mb Bandwidth) and Create 4 packages for customer.

	::Pool create::
	>>>ip > pool > plus button > pool name, pool ip range > select ok
	
	::pppoe profile::
	>>> ppp > profile > plus button > profile name, local ip (out of pool range), remote ip (pool name select) > limits (rx/tx range by MB) > select apply and ok
	
	::pppoe user::
	>>> ppp > secrets > plus button > username, password, service name(pppoe), profile select > select apply and ok
	
	::pppoe server::
	>>>pppoe > pppoe servers > plus button > server name, select LAN interface, profile > select apply and ok
	
	
			::All done::
	


