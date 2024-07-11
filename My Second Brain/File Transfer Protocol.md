---
alias: FTP, TFTP
tags: [networks]
Created: 2023-09-02T13:13:40+10:00
Modified: 2024-07-03T19:35:33+10:00
---
File Transfer Protocol (FTP) is a client/server protocol used to transfer and manage files across a network. FTP uses [[Transmission Control Protocol|TCP]] port `20` and `21`:
- Port `21` is for sending control commands and 
- Port `20` is for transferring file data.
It is not considered a secure protocol, as a users credentials and data are sent in plaintext

# Trivial File Transfer Protocols
Trivial File Transfer Protocol (TFTP) is a simple protocol for transferring files, but it has little file management capability. It uses [[User Datagram Protocol|UDP]] port `69`, so its not reliable for long file transfers across the internet. It's used primarily in a LAN to transfer configuration and firmware files to network devices, such as managed routes and switches. TFTP is also used by some devices that boot an OS from a network server rather than local storage. Like FTP, TFTP isn't a secure protocol, but because its rarely used across the internet and doesn't require credentials, security isn't as much of a concern.

# Is FTP Still Used?
FTP was revolutionary developed when it was first introduced in the 1970s. Within the last 40+ years, FTP has served as the foundation for various methods of sending data. **FTP and TFTP is outdated and insecure**.