# Proxies

A proxy is when a device or service sits in the middle of a connection and acts as a mediator

A **_Mediator_**. That means in must be able to inspect traffic. Without this, it would just be a gateway.

There are three main types.

## 1. Dedicated Proxy / Forward Proxy

A proxy that forwards reqests from a client to remote servers.

`Client -> Forward Proxy -> Website`

Example: A company could set up a forward proxy as a web filter. The proxy hides the client's ip from the website, and can block certain content or scan for malware.

![ForwardProxy](images/forward_proxy.png)

## 2. Reverse Proxy

The oposite of a forward proxy. It filters content coming into a server.

`(Web) Server <- Reverse Proxy <- Client`

This can be used to control what kind of traffic reaches your server. Often used to prevend DDOS attacks

If an attacker gains access to a device device within a network, they may set up a reverse proxy on that device. The reverse proxy can then send data to the attacker, and since the proxy is a 'trusted' device from inside the LAN, firewalls and IDS/IPS may not catch the dubious activity.

## 3. Transparent (vs Non Transparent) Proxy

A transparent proxy is invisible to the client. The client does not know that a proxy exists between it and the server.

A non-transparent proxy requires extra configuration from the clinet in order to forward anything to/from the client.

