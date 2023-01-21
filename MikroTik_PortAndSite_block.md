Port and Site block:
====================
Login Router with username and password.

Comment Interface:
------------------
> interface/options/comment (WAN or LAN)

Basic Configrations:
--------------------
> IP/DHCP-Client/add/select interface "WAN interface (apply and ok)
> IP/Addresses/add/create IP address(Ex.192.168.0.1/24)/select interface "LAN Interface" (apply and ok)
> IP/DHCP-Server/DHCP-Setup/select interface "Lan interface"
> IP/Firewall/Nat/add/Genaral (Chain:srcnat, Out.Interface: "WAN interface), Action (Action:masquerade) 

Block address and port:
-----------------------
> IP/Firewall/Layer7 Protocols/add (name:block_facebook, Regexp: ^.+(facebook.com).*$) (apply and ok)
> IP/Firewall/Filter Rules/add/General (Chain:forward, Protocal:6(tcp), Any. Port:80, 443), Advanced (Layer7 Protocol:block_facebook), Action (Action:drop) (apply and ok)

====
Done
====
