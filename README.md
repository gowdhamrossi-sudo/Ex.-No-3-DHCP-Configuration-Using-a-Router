## Ex. No: 3  DHCP Configuration Using a Router
Date:
________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/962b0ac9-7d41-4f0a-b6ad-78d7e2f793c6" />

________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
•	DHCP IP configuration shown in PC0 and PC1<br>
•	Router configuration screen<br>
•	Successful ping test between the two PCs<br>

# CONFIGURATION 
PC1
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/4c495f21-7984-4281-bc3e-d3b7fa322adf" />



PC2


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/8e4f5958-6ab9-4975-ba6e-26d134490236" />


SWTICH 

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/6e05b296-6512-4eb1-b693-d8119ffd0a2e" />




ROUTER

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/13fd1830-7714-4c20-b16e-6075bb193a9a" />


# PING

PC1

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/a32ed98e-53b0-4c6b-9cf4-21eb2ad5a0b6" />


PC2

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/7ef42313-d43d-4581-be75-333f3ec148f2" />



________________________________________
# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
