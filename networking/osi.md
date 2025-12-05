# The OSI Model

The OSI model describes the different layers of encasulation that wrap data in order for it to travel various medium and nodes, from remote servers all the way down through routers, your device's network interface, and even down to the circuitry in your computer.

There are 7 layers.

- 7. Application Layer
        - The application sending data formats it in a certain standardized way (called a protocol). (HTTP, FTP, etc)

- 6. Presentation Layer
        - The formatted data is encrypted in whatever format it needs to be (SSL/TLS, JPEG, etc)

- 5. Session Layer
        - A session is established between the client and server for continuous exchange of data

- 4. Transport Layer (for the remote server)
        - Once a session is established, the sender wraps the data in a **segment or datagram** using a Layer 4 protocol (TCP, UDP, etc). This gives the reciever information about what to do with the data inside (which port to send it to? is it urgent? does it need special processing?).

- 3. Network Layer (for your router/gateway, or layer 3 switch)
        - The segment/datagram is then wrapped in a **packet** with an IP header. This gives routers information sending the data over the network (what address? is it urgent? does it need any special processing?)

- 2. Data Link Layer (the switches and bridges in your local network)
        - The packet is then wrapped in an Ethernet or Wi-Fi **frame**. This tells your local network how to get this data to your gateway.

- 1. Physical Layer (the hardware on your device)
        - The entire frame is then sent as bits (1s and 0s) across the network through whatever medium (cabling, optics, radio waves, etc.)

When the other side recieves these 1s and 0s, it then strips off each layer of encapsulation until the application has its hands on the original data itself, just as the sender originally composed it.

![OSI](images/net_models_pdu2_updated.png)

A PDU is a Protocol Data Unit. A Frame is a PDU that Layer 2 creates and passes it to Layer 3. Layer 3 takes the frame, an makes a new PDU, called a Packet, and passes it to Layer 4. Etc.