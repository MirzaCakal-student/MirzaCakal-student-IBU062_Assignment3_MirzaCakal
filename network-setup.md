Router0 - 1941

Router:
GE 0/0:168.90.0.1
GE 0/1:210.3.14.1

----------------------------LAN1
Switch0-2960-24TT
PC0 - PC-PT - 168.90.0.2
PC1 - PC-PT - 168.90.0.3
PCc - PC-PT - 168.90.0.6
Laptop0 - Laptop-TP - 168.90.0.4
Server0 - Server-PT - 168.90.0.5


----------------------------LAN2
Switch1-2960-24TT
Server1 - Server-PT - 210.3.14.2
Server2 - Server-PT - 210.3.14.3
PC2 - PC-PT - 210.3.14.4
PC4 - PC-PT - 210.3.14.5

---------------------DHCP EXPLANATION-------------------------
ip dhcp excluded-address 168.90.0.1
ip dhcp excluded-address 210.3.14.1
The IP addresses 168.90.0.1 and 210.3.14.1 are the router's own addresses (default gateways for the respective networks).

------FIRST_NETWORK----------
ip dhcp pool FIRST_NETWORK: Creates a new pool named FIRST_NETWORK for DHCP configuration.
network 168.90.0.0 255.255.0.0: Specifies the range of IP addresses within the subnet 168.90.0.0/16 (subnet mask 255.255.0.0) that can be assigned to devices.
default-router 168.90.0.1: Assigns 168.90.0.1 as the default gateway for devices in this network.


ip dhcp pool FIRST_NETWORK
network 168.90.0.0 255.255.0.0
default-router 168.90.0.1


------SECOND_NETWORK---------
ip dhcp pool SECOND_NETWORK: Creates a new pool named SECOND_NETWORK.
network 210.3.14.0 255.255.255.0: Specifies the range of IP addresses within the subnet 210.3.14.0/24 (subnet mask 255.255.255.0) that can be assigned to devices.
default-router 210.3.14.1: Assigns 210.3.14.1 as the default gateway for devices in this network.

ip dhcp pool SECOND_NETWORK
network 210.3.14.0 255.255.255.0
default-router 210.3.14.1
