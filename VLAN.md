VLAN:
:::ISP:::
step 1 - create VLAN:
interface > vlan(4) > plus button > name, id , interface

step 2 - create IP for different vlan:
ip > address > plus button > different ip for different vlan(user(10.100.1.1/24), FNA(10.100.2.1/24), GGC(10.100.3.1/14), BDIX(10.100.4.1/24)) > select vlan interface

:::USER:::
step 3 - create VLAN:
interface > vlan(4) > plus button > name, id(same id provide from isp) , interface

step 2 - create IP for different vlan:
ip > address > plus button > different ip for different vlan(user(10.100.1.2/24), FNA(10.100.2.2/24), GGC(10.100.3.2/14), BDIX(10.100.4.2/24)) > select vlan interface


