# IP Addresses

## MAC Addresses

"Media Access Control" address

Uniquiely identifies a device. One device (network interface) has one MAC address for it's whole life

MAC addresses alone would allow devices on a single network to communicate. It is not enough, however, to route traffic across multiple networks. That is where IPs come in.

- IPv4 and IPv6: It's like the address of an apartment
- MAC: It's like the exact floor and unit in the aparetment.

An IP can route to multiple hosts (broadcasting)

A host may respond to multiple IPs

But, each IP must only be assigned once.

## IPv4

A 32-bit address:

0111 1111.0000 0000.0000 0000.0000 0001 (in binary)

127.0.0.1 (in decimal)

 4,294,967,296 unique addresses possible

 There are 2 parts of an IPv4 address: The Network ID, and the Host ID. For example, if the network is `192.168.0.0`and the netmask is `255.255.255.0` (only 256 hosts), and a host has the address `192.168.0.55` then `192.168.0` is the Network ID (all hosts on the network will have this as the first part of their address) and `55` is the Host ID.

 There used to be 5 classes of networks: A-E. A networks were very large, B were medium, and C were smaller:

 |Class|Range|Subnet Mask Equivalent|IPs Available|
 |-----|-----|----------------------|-------------|
 |A|`1.0.0.0 - 127.255.255.255`|`255.0.0.0`|16,777,214 + 2|
 |B|`128.0.0.0 - 191.255.255.255`|`255.255.0.0`|65,534 + 2|
 |C|`192.0.0.0 - 223.255.255.255`|`255.255.255.0`|254 + 2|
 |D|`224.0.0.0 - 239.255.255.255`|Multicast|Multicast|
 |E|`240.0.0.0 - 255.255.255.255`|reserved|reserved|

 This system meant that network size was determined by the first octet. If it was less than 128, then the size was 16 million IPs (the largest size here). Subnet masks were implied and automatically set based on this. However, there were problems with only having 3 size options. If you only needed 300 hosts on your network, you were stuck with having 65,534. This was abandoned in favor of configurable subnet masks (CIDR), which give more granular control over network size.

 The _default gateway_ of a network is a host on the network that is the network's link to other networks. It is common for the defualt gateway to have the first or last assignable address.