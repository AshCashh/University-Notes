#networks
A VPN is a private network that uses a public network (usually the internet) to connect remote sites or users together. VPNs are used to provide secure remote access to a private network.
### Benefits
- Allow mobile users to connect with corporate networks securely
- Allow multiple sites to maintain permanent secure connections via the internet instead of using expensive leased lines
- Reduce costs by using the ISP's support services instead of paying for more expensive leased line support
### Common VPNs:
- IPSec $\to$ Network layer
- Transport Layer Security (TSL)/ Secure Sockets Layer (SSL) $\to$ Transport Layer
### VPN Communicate Model:
- **Site-to-Site VPN**: A VPN that connects two or more remote sites together
- **Client-to-Site VPN**: A VPN that connects a remote user to a remote site
- **Client-to-Client VPN**: A VPN that connects two remote users together
![[Pasted image 20230916170859.png|centre|300]]
## IPSec VPN
An IPSec VPN can be implemented using two modes:
- **Transport Mode**: A host-to-host VPN where only the payload is authenticated and protected
- **Tunnel Mode**: A network-to-network VPN where the entire packet is authenticated and protected