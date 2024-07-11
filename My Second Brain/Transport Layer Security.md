---
aliases:
  - TLS
tags:
  - networks
Created: 2024-04-28T13:08:16+10:00
Modified: 2024-07-03T19:35:32+10:00
---
TLS is a [[Network Security]] protocol designed specifically to provide privacy and secure data communications over the [[Open System Interconnection#Transport Layer|Transport Layer]]. A major use-case of TLS is its use in encrypting communications between web applications and servers. 

[[Hypertext Transfer Protocol|HTTP]] is an implementation of TLS on top of the HTTP protocol. There are three main components of TLS: encryption, authentication and integrity. In the terms of secure data transfer the main point of encryption is to hide the data in transit from third parties. Authentication ensures that the parties in the data transaction are who they claim to be. Finally, integrity verifies that the data that has been sent has not been edited, tampered or altered in any way or form by a third party.

These certificates are issued by trusted third-party certificate authorities (CA). The CA will generate and sign a certificate with their private key and issue it out for it to be installed on the websites origin server. These certificates can also be self-signed meaning technically anyone can generate and create an SSL certificate by generating a public-private key pairing and including all relevant information. Self-signed certificates however are not considered trustworthy by browsers and will still mark the site as not being secure even though there does exist a HTTPS connection.