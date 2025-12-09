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

## Quality of Service

Influence packet performance of traffic queues

How high priority are certain types of traffic?

- Tos (Type of Service)
- CoS (Class of Service)
- DSCP (Differentiated Services Code Point)
- Wi-Fi Multimedia (WMM)

## Questions

- 802.x (port security)
    - uses things like RADIUS to control access per user on the port level

- EAP (extensible authentication protocol)
    - This is a protocol framework - not a protocol itself.
    - It defines requirements for protocols that share authentication information
    - Consists of 3 components:
        1. EAP Peer (the device or user seeking authentication)
        2. EAP Authenticator (Network entity that recieves the authentication requests from the peer (switch, etc). Forwards requests to the EAP Server)
        3. EAP Server (Verifies credentials and grants/denies access)

- RADIUS
    - [RADIUS](https://www.cbtnuggets.com/blog/technology/networking/what-is-radius)
    - Remote Authentication Dial-In User Service
    - RADIUS is a network protocol providing centralized authentication and authorization for network access
    - RADIUS provides Authentication, Authorization, and Accounting managment for users on a network (AAA)
    - Users are required to authenticate before being granted network access
    - Client vs Server:
        1. RADIUS Client is a switch or other network device that is configured to restrict access with RADIUS
        2. RADIUS Server is a server that the client reports to when a user requests access. The server looks up the user in the company's identity system (Azure AD, ect.) to check if the user has access.
    - Example:
        - A user connects their laptop to an ethernet port leading to a switch that is a RADIUS client.
        - The switch asks the user for credientials
        - The switch (client) forwards the credentials to the RADIUS server
        - The server queries Azure AD with the credientials. The is allowed access.
        - THe server responds to the switch saying the user has access. The switch grants the user access to the network.

- Routing tables
    - Are routes just within your local network?
    (NO, routes tell the router how to reach another network)
    - [Routing Tables](https://www.youtube.com/watch?v=CGmTvukObOw)

- PPPoE
    - PPP (point to point protocol) over ethernet
    - used in DSL networks or other networks where you need to be able to authenticate before using internet
    - Allows ISPs to monotor and control who can use the internet when many locations are using the same cabling

- Border Gateway (and internal border gateway)

- Peering tables (and how they could bring down the internet)

- Site magic and OSPF(Open Shortest Path First) (SW-WAN) (Hello/dead intervals)

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

- What is AV

- Autonomous Systems
    - Stub
    - Multihome
    - Transit

- Dynamic Routing Protocols
    - Interior Gatway Protocol (IGP)
    - Exterior Gateway Protocol (EGP)