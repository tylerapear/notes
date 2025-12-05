# Day 2 Notes

## Authorization, Authentication, Accoutning

### Techniques

1. ACL (Access control list)
    - Lets you specify who can access a specific VLAN (MAC ACL) or between VLANs (IP ACL)

2. RADIUS (Remote Authentication Dial-In User Service)
    - Users provide a username and password when connecting to an access point, and depending on their info, they will be connected to a specific VLAN depending on their credentials

## Accouting

Logging client activity so there is a record of what everyone is doing

## Routing

### Routing Table

How do I get to a specific address?

1. C (connected) Route
    - There is a physical connection on the router
2. S (static) Route
    - You manually specify what the route is
3. O (OSPF) Routes
    - OSPF

RIB - The routing table

FIB - The routes actually being used

- Policy Based Route
    - Routing based on source/dest packet info

## Firewall

### Types

1. Stateful (based on connection)
    - Did the user request this message?

2. Stateless (based on the packet)
    - I don't care if the user requested this message... does the mesage contain malware?
    - More CPU expensive

## Questions

- 802.x (port security)

- EAP (extensible)

- RADIUS

- Routing tables
    - Are routes just within your local network?

- PPOE

- Border Gateway (and internal border gateway)

- Peering tables (and how they could bring down the internet)

- Site magic and OSPF

- R16 routers

- What is a blade device

- Policy based routing

- bit torrent

- DHCP (Dynamic Host Configuration Protocol) (DORA between client and server)
    - DHCP Guarding (you want to just check the box and use your gateway's ip)
        - This blocks other servers from handing out DHCP IPs
    - DHCP Snooping
    - Rogue DHCP servers

- SLAAC