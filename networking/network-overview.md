# Networking Overview

## Basics

#### URL (Uniform Resource Locator) vs FQDN (Fully Qualified Domain Name)

- A URL is the _full path_ to a resource: "https://www.github.com/tylerapear/notes/networking/overview.md"

- A FQDN is just the domain name of the website: "www.github.com"

#### Other Random Notes:

- **RFC 1918**
    - A standard that reserves three blocks of IPv4 addresses for private networks:
    - 10.0.0.0 - 10.255.255.255
    - 172.16.0.0 - 172.31.255.255
    - 192.168.0.0 - 192.168.255.255

## Types of Netorks

1. **WAN (Wide Area Network):** A number of LAN's joined together. Most common is the Internet, but some large companies have their own WAN.

2. **LAN (Local Area Network):** Group of local devices connected through a network. May be connected to a WAN through a gateway. Uses IP address specified by *RFC 1918*. Also, WLANs (Wireless LANs) are just the wireless version of a LAN (Wi-Fi).

3. **VPN (Virtual Private Network):** Simulates a device being connected to a different network. There are 3 main types:
    1. **Site-To-Site VPN:** Used to simply connect multiple networks together so they act like one LAN. Usually used to join locations within a company.
    2. **Remote Access VPN:** A client device sets up a virtual network interface that acts like it is connected to another network
    3. **SSL VPN:** A VPN that is created within a browser. Used to stream applications or entire desktop environments through a browser.