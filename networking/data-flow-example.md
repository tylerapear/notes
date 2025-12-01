# Data Flow Example

Here is an example, from beginning to end, of a user accessing a website using their laptop in their home network.

### 1. **User Accesses the Internet**

1) The laptop identifies the SSID of the wireless network.
2) If the network uses WPA2/WPA3 security, the user provides credentials to access the network.
3) Connection is established to the local network
4) The laptop is given a local IP address (Let's say `192.168.0.100`) by the DHPC server on their router.
5) The laptop can now access the internet.

### 2. **Checking Local Network Configuration (DHCP)**

1) The user opens Chrome and types in `www.example.com` into the address bar.
2) The laptop's operating system checks that it has a valid local IP address before sending the request. If it doesn't have one, it requests one from the router's DHCP server.
3) The laptop has already been given the IP address `192.168.0.100`. It is ready to send the request.

### 3. **DNS Resolution**

1) The laptop needs to find the IP address of `www.example.com`.
2) The laptop sends a DNS query to a DNS server. In this case, it sends the query to `8.8.8.8`, one of Google's DNS servers, from the laptop's local port `49152` (This could be any port in the range 49152-65535). It accomplishes this by first sending the request to the home router. The home router then repackages the request and sends the request from it's own public IP address. Let's say the public IP address is `71.71.71.71`. It sends this new packet to `8.8.8.8` port `53`.
3) The home router records in its NAT table that this session is active:

    |Internal Local IP|Internal Local Port|Public IP|Public Port|
    |-|-|-|-|
    |192.168.0.100|49152|8.8.8.8|53|

    When the router recieves a reponse from `8.8.8.8`, it will know to forward those packets to local IP `192.168.0.100`.

4) The DNS server recieves the request from our router (`71.71.71.71`), and, through some internal routing of it's own, looks up the IP address of `www.example.com`. It turns out that the IP address of this website is `99.99.99.99`
5) The DNS server returns the IP address it found to `71.71.71.71`, our router's public IP address.
6) Our router notices that it just recieved a reponse from `8.8.8.8`'s port `53`. It looks up in its NAT table which local device sent a request to this IP. It sees that the request originally came from `192.168.0.100`, the local IP of our user's laptop. It forwards the response on to the laptop.

### 4. **Data Encapsulation and Local Network Transmission**

- The laptop now knows that `www.example.com` is located at the IP address `99.99.99.99`. It then works through layers of the TCP/IP Model:

1) **Application Layer:** The browser first performs a TSL Handshake with `99.99.99.99`. Then, it creates an HTTPS request for the webpage located at `99.99.99.99`:

    ```
    GET / HTTP/1.1
    Host: www.google.com
    User-Agent: CustomClient/1.0
    Accept: */*
    Connection: close
    ```

2) **Transport Layer:** The request is wrapped in a [TCP Segment](packets.md). The TCP Header specifies the source and destination ports. It will choose a port on the laptop to send from, let's say `49152` again. Since the default port for HTTPS is `443`, it will mark this as the destination port.

3) **Internet Layer:** The TCP segment is placed into an IP packet and given an IP header. The IP header specifies that the source IP address is `192.168.0.100` (the laptop's local IP), and the destination address is `99.99.99.99` (www.example.com's IP).

4) **Link Layer:** The IP packet is placed into an Ethernet or WiFi frame. Source and destination MAC (Media Access Control) addresses are included. The source MAC is the laptop's network interface, and the destination MAC is the router's network interface. It determines the router's MAC address by either checkign the laptop's own ARP (Address Resolution Protocol) table, or sending an ARP request. Then, the laptop finally sends the full frame to the home router's MAP address.

### 5. **Network Address Translation (NAT)**

1) When the router recieves this frame, it then creates another NAT table record for the request:

    |Internal Local IP|Internal Local Port|Public IP|Public Port|
    |-|-|-|-|
    |192.168.0.100|49152|99.99.99.99|443|

    It then re-packages the packet with it's own public IP address, and send the packet to the ISP's network, which then routes the packet through intermediate routers in the best path to reach it's destination.

### 6. **Server Recieves the Request and Responds**

1) The destination network's firewall (if there is one) checks if this traffic is allowed. If so, it passes it through to the server hosting `www.example.com`. This server will have web server software running (Apache, Nginx, etc.). This software processes the request, then packages and returns its own HTTPS response, wrapped in a TCP segment, IP packet, and Ethernet/Wi-Fi frame. The server then sends the frame in the same way our user's laptop and home network sent the request. The body of the response is this:

    ```
    <html>
        Welcome to example.com!
    </html>
    ```

### 7. **Decapsulation and Display**

1) The laptop finally recieves the response and strips away the Ethernet/Wi-Fi frame, IP Header, and TCP header. Now, it has just the applicaiton layer data. The browser reads the HTML/CSS/JavaScript and displays the webpage:

```
Welcome to example.com!
```