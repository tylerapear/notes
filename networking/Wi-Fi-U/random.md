# Random Notes

Rj45 A was designed for AT&T, the center two wires are "tip and ring"
QBasic (Bill Gates, Punchcards)
Port 666 was used for DOOM

The OSI model was developed by ISO to stop propritary protocols

Encapsulating: Wrapping Protocol Data Units (PDU)s into larger units with "headers" and "footers" with source/destination info
Decapsulating: Stripping the PDU to get to the data

A group of switches is called a Fabric
The most powerful switch should be the root bridge

broadcast and multicast cant go through an isolated port
Example: you might isolate a port that has a busy access point on it that you dont want all broadcasts from 
May be better to just create a vlan rather than isolating a port

7. Application - Payload (HTTPS, FTP)
6. Presentation - Payload (any kind of ecryption (jpeg, mpeg))
5. Session - Payload
4. Transport - TCP, UDP
3. Network - IPv4(6),ARP
2. 802.3, 802.11, ARP, Frame
1. Cables, Modems, WiFi

## Server-Client Model

Registered Ports: 0-1023 (not available, well known. Like port 80 is HTTP)
Ephemeral Ports: 49152-65535 (dynamic and available)

Things we need to communicate on the internet:

1. Public IP
2. Private IP
3. DNS
4. NAT

## TCP vs UDP

### TCP

Connection-oriented
Relialbe
Orderly
Error-checking (uses ACK)

### UDP

Connectionless
Unreliable
Disorderly
Best Effort
Doesn't use ACK

## Network Interfaces

Hosts pass traffic via interfaces

- Physical
    Hardware
    Ethernet (eth0), Switch (sw0), Wireless (wifi0)

- Virtual Interface
    Loopback (lo0) for testing network functionality
    Bridge (br0) joins interfaces on same segment
    Tunnel (tun0) encasulates (VPN)
    VLAN (eth0.20) add logical segment to eth0
    Link Aggregation - bond channels for throughput (multiple switch ports talk to multiple switch ports, redundancy and speed)

    Cisco originally did not allow any communication between VLANS
    Unifi does allow this (router on a stick)


## Traffic Types

Unicast (IPv4/6)
    Purpose - 1-1
    ICMP ping reply, DHCP release

Broadcast (IPv4)
    Purpose - One to all

Multicast
    One to many
    OSPF

Anycast
 O

## IPv4 Addressing

xxx.xxx.xxx.xxx
4 bytes of data

Terms
- IP - denotes address assigned to an interface on the network
- Net Mask - Indicates the size of the IP network
- Gateway - Router for forwarding packets designed to other networks
- Network ID - Starting address of a network; unavilable for hosts
- Broadcast ID - Final address and used with broadcasts; unavailable for hosts

10 = class A address (not referred that way anymore)

## Subnetting

Dividing your network into smaller networks
Lower subnet -> larger network
Higher subnet -> smaller network

In ubiquity, we don't really subnet, we create VLANs

## ARP

Address Resolution Protocol

Router Sends a request to devices on the network: Router sends to all macs on the network "Who is 10.5.1.25? I'm 10.5.1.30, let me know". 10.5.1.25 then says to 10.5.1.30, "That's me!"

Very chatty, sends out requests a lot

## IPv6

2001:db8::ff00:42:8329

translates to

2001:0db8:0000:0000:0000:ff00:0042:8329

Leading 0s are dropped from hextets
Omit largest group of consecutive zeros -> "::"
128 bits total

## Neighbor Discovery Protocol (NDP)

RFC 4861
Replaces/enhances ARP

Functions:
    Stateless Address Auto-Configuration (pick your own address)
    Neighbor discovery
    Router Discovery
    Duplicate Address detection
    Neighbor Unreachability Detection

Messages:
    Router Solicitation: request RAs from routers when hosts furst connect
    Router Advertisement: Routers advertise their presence and network config parameters to al hosts

## SLAAC and Global Unicast Addresses

2003:1234:ABCE:5678:0221:2FFF:FEC5:xxxx

1-12: Global Routing Prefix
13-16: ISP owned (subnet ID)
Remaining: Interface ID

## Network Architechture

Edge (WAN/LAN) - Gateway

Core (Aggregation/Distribution) - Switches, High availability/redundancy

Access (users)

## Power Distribution

## Power over Ethernet

Power Sourceing Equipment - switch, injector, etc
Power Devices - AP, switch, camera, VoIP

## Fiberoptio and Small Form-Factor Pluggable Types

### Cable Types

Single-Mode - long range
Multi-Mode - medium range (multiple signals allowed)

### Module Types

Bi-Directional (1 cable sends and recieves)
Uni-Directional (a send cable and a recieve cable)

An twisted pair cable goes 100 meters

## Broadcast storm

A device sends out a broadcast to all ports
Another switch gets the broadcast
That switch forwards the broadcast
Now you have an infinate loop, and you just need to unplug stuff to get it to stop

## VLANs

VLAN Awareness
    Hosts are VLAN unaware - they always send untagged traffic
    USW/AP are VLAN aware - they "tag", "untag" and inspect vlan id before forwarding traffic

## Shadow Mode

## Switch Behavior

MAC Table
    Also known as Content Addressable Memory (CAM) Table
    Track which port each mac address is reachable

Behavior
    Forward - pass traffic on a port
    Flood - pass traffic on all but port in which recieved
    Filter - discard traffic (refer to MAC ACL)

Blocking
Listening
Learning 
Forwarding

Layer 3 Switch: can route between vlans on a lan
Layer 2 Switch: only routes within a lan?

### Layer 2 attacks

MAC Spoofing
ARP poisoning
MAC Flooding
Rogue DHCP Server
Rogue AP

Most important rule... DONT let people have physical access to your ports!!!

## Link Redundancy and Loop Detection

LR helps produce maximum uptime
without loop detection, LR causes loops and crashes mac tables

## Port Isolation

method for restricting traffic only to uplink/service ports
help isolate guests and limit impact of broadcast traffic

how to config?

enabled on downlink access ports (hosts, aps,)
disabled on uplink and service ports

## Software Defined WAN (SD WAN)

Connecting sites under a logical WAN

Hub & Spoke
    Connect branch sites to a hub site (up to 1000)

Mesh
    Connect all sites together (up to 20)

## Region Blocking

Important Contries:

North korea
Nigeria
Iran
Iraq 
Syria
Russia
Yemen
Isreal

Blocking these contries both ways is more secure than blocking just incoming for all but USA

## Multi-Chassis LAG (MC-LAG)

Basically connect an entire rack through LAG to another rack

## Questions

- What is a wisp
    - Lets you temporarily cancel service
    - Lets you buy much lower speeds
    - WISP stands for "wireless internet service provider". Its just an ISP but wireless instead of wired. It's much more flexible.

- What is a broadcast address
    - A Broadcast is a message that is sent to every single device on a newtork or subnet.
    - The network/subnet's broadcast IP is the address a device needs to send to if it is broadcasting.
    - The broadcast address is always the final usable IP of the subnet
    - [resource](https://www.ionos.com/digitalguide/server/know-how/broadcast-address/)

- What is a subnet ID
    - Its the "network" part of the address that all devices on the network have in common
    - Always ends with all 0s.

- What is a spanning tree
    - [spanning tree](https://networklessons.com/spanning-tree/introduction-to-spanning-tree)
    - STP (spanning tree protocol) creates loop-free networks by blocking redundant links between switches.
    - BPDUs (Bridge Protocol Data Unit): a frame sent by a switch with their MAC address and the Priority number (32768 is the defualt, half way in a 16 bit number)
    - STP does a few things:
        1. Elect a root bridge
            - each switch sends BPDUs to the other swtiches
            - The switch with the lowest priority number wins the election and becomes the root bridge
            - If there is a tie, the lowest MAC wins
        2. Mark all ports on the root bridge as designated and put them in forwarding state
        3. each other switch marks a "root port" that is the fastest port to get to the root bridge
        4. Redundant ports are set in Blocking state

Look into IPv6

- Learn about LAG (link aggregation)
    - [LAG](https://www.auvik.com/franklyit/blog/network-basics-link-aggregation/)
    - You're saying "treat these multiple (redundant) links as the same logical link"
    - Increases redundancy and throughput
    - divides load between links (3 cables carry data 3x as fast)


- Look more into traffic types
    - [traffic types](https://ipcisco.com/lesson/unicast-broadcast-multicast-anycast/)
    - Unicast:
        - There is only 1 sender and 1 reciever (what I normally think of)
    - Multicast:
        - There are multiple recievers (a multicast group)
        - Examples: casting television to many viewers, playing online games in a lobby, OSPF, etc.
    - Broadcast
        - All recievers on the network recieve the traffic
        - Example: when a device joins a network, it does DHCP discovery. It broadcasts to all devices on the network "is there a DHCP server out there?". Most devices ignore this, but the DHCP server will respond.
    - Anycast
        - used in IPv6 networks
        - Many servers share the same IP address, and anycast routes you to the nearest one
        - 8.8.8.8 (google dns) has many servers all providing the same service. Anycase to 8.8.8.8 will get you to the nearest google dns server.

Find out more about adoption
[device adoption](https://help.ui.com/hc/en-us/articles/360012622613-UniFi-Device-Adoption)

- Learn: Switch behavior
    - These four port states are used in Spanning Tree Protocol:
        - Blocking: traffic is not allowed to pass
        - Listening: Sending and retrieving BPDUs and performing STP calculations
        - Learning: Learning everyone's MAC addresses and building a table for them
        - Forwarding: The port is active and sending frames
    - [states](https://networklessons.com/spanning-tree/spanning-tree-port-states)

What is Dante

Learn about layer 7 switches

Learn about root bridge and priority
Bridge Protocol Data Units (BPDUs)
[bpdu](https://jumpcloud.com/it-index/what-is-a-bridge-protocol-data-unit-bpdu)
[bridge](https://www.cbtnuggets.com/blog/technology/networking/what-is-network-bridge)

what does turnkey mean?

Ethernet blueprint DNS

Look more at MC-LAG

PDU
    Layer 2 -Frame
    layer 3 -packet
    layer 7 -payload

