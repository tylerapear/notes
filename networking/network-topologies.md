# Network Topologies

- _Physical_ Topology is the layout of the physical devices
- _Logical_ Topology is how the devices are configured to conduct data flow

There are three concepts behind network topology:

## 1. Connections

|Wired|Wireless|
|-----|--------|
|Coaxial Cabling|Wi-Fi|
|Glass Fiber Cabling|Cellualar|
|Twisted Pair Cabling|Satelite|
|Others|Others|

## 2. Nodes

- Repeaters
- Hubs
- Bridges
- Switches
- Router/Modem
- Gateway
- Firewall

## 3. Classifications

### Point-to-Point

A simple direct link exists between two hosts.

![Point-to-Point](images/topo_p2p.png)

### Bus

All devices are connected through a medium (ex. a cable) without any intermidiary node. Only 1 device can send a signal, and all other devices must determine whether the message is meant for them.

![Bus](images/topo_bus.png)

### Star

One central device recives and forwards traffic to the appropriate devices on the network. This device can be under a fairly heavy load. Typical from home networks.

![Star](images/topo_star.png)

### Ring

No nodes required for physical rings. Devices each have in incoming port, and an outgoing port. Traffic flows from device to device in a ring. Can be implemented as a _logical_ topology by a router sending traffic from one device to the next in a ring.

![Ring](images/topo_ring.png)

### Mesh

Many node devices all connect to each other and to client devices, creating redundancy. In fully meshed networks, every node is connected to all other nodes.

![Mesh](images/topo_mesh.png)

### Tree

Nodes branch out in a hierarchical structure, each providing connection to it's children. Typical in company networks.

![Tree](images/topo_tree.png)

### Hybrid

Two or more basic topologies are combined.

![Hybrid](images/topo_hybrid.png)

### Daisy Chain

Hosts are chained togther in a line. Those further up the chain pass data to those below.

Example: My IP phone is connected directly to my switch, and my PC is daisy chained from the IP phone.

![DaisyChain](images/topo_daisy-chain.png)
