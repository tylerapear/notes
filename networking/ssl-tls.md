# Secure Sockets Layer (SSL) / Transport Layer Security (TLS)

[SSL Encryption Video](https://www.youtube.com/watch?v=j9QmMEWmcfo)

## History

SSL was created in 1995 by Netscape. It was later improved upon and replaced by TLS. Because of habit, however, people still say SSL when they are really using the new and improved TLS.

True SSL is considered now to be deprecated in favor of TLS

## Why SSL/TLS?

Originally, traffic on the internet was all in plaintext. Of course, this leads to much sensitive information being compromised. So SSL/TLS was created to encrypt data before it goes over the internet so that it is nearly impossible to decrypt if intercepted.

## Handshake

After a TCP connection is established, the Client initiates a TLS handshake with the server. The server responds with a certificate (verifying it's identity). Then, the client generates a session key and securely sends it to the server. The key is either encrypted using the server's public key, or the key is generated using prime number math, in which case it does not need to be encrypted. The client and server are then all set to send encrypted data back and forth using the session key.