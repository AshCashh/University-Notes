---
alias: SSH
---
#networks
Telnet and Secure Shell (SSH) are used to connect to a device across a [[Networks|Network]] via a command-line interface (CLI). Network administrators might use Telnet or SSH to connect to a mangled switch or router and view status information or perform configuration tasks by using the device's CLI. 

# Telnet
Telnet uses [[Transmission Control Protocol|TCP]] port `23` and like [[File Transfer Protocol|FTP]] isn't a secure protocol. 
# SSH 
SSH uses TCP port `22` and provides an encrypted channel between the client and server, so it's preferred over Telnet when both devices supports
# PuTTy
PuTTy is a client program that supports Telnet along with SSH and Rlogin (remote login) network protocols.

# Remote Desktop Software
Remote Desktop Protocol (RDP)
- Uses graphic user interface to manage/access windows computers remotely
Independent Computing Architecture (ICA)
Virtual Network Computing (VNC)