---
alias: DNS
tags: [networks]
Created: 2023-09-01T14:04:57+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Domain Name System (DNS) is a name-to-address resolution protocol that keeps a list of computer names and their [[Internet Protocol|IP]] addresses. Through a correctly configured workstation, a user can use a computer's name rather than a numerical address to communicate with the computer. DNS is thought of as the phone book of the [[Internet, Intranet, Extranet|Internet]].

For example, when you enter "www.cengage.com", in your web browser's address box, the web browser contacts the DNS client service on your computer. The DNS client contacts the DNS server specified in your OS's IP configuration and requests that the web address be resolved to an IP address. The DNS server responds with the IP address assigned to the computer name `www` at the `cengage.com` domain. Using this IP address, your web browser application can contact the web server to request a web page. 

DNS uses the [[User Datagram Protocol|UDP]] Transport-layer protocol because DNS messages usually consist of a single packet of data, so theres no need for the reliability measures [[Transmission Control Protocol|TCP]] offers.
# DNS Structure
The DNS is a hierarchical naming system where the top-level domains (root domain) contains all top level domains (TLDs) of the internet. The two main types of TLDS are: Country-code TLDS (ccTLDs), such as `.au`, `.nz` and Generic TLDs (gTLDs), such as `.gov`,`.edu`,`.com`. Root servers are a network of hundreds of servers for redundancy in many countries around the world.

![[Pasted image 20230901151559.png|centre|400]]

When you put all the names of a branch together, separated by periods, you have the Fully Qualified Domain Name (FQDN) of the network's resource, such as www.cengage.com.

The second-level domains are usually the name of a company or an institution. The subdomain level is optional and can consist of several names separated by a period. Finally, the host level represents individual computers hosting network services. For example, in www.qut.edu.au, `au` is the top-level domain name, `edu` is the second-level domain, `qut` is the subdomain and `www` is the hostname.

## DNS Servers
DNS servers are composed of the following:
- DNS zones: A database of primary hostname and IP address pairs
- Resource records: The unit of information entry in DNS zone files
- Cache: Results of queries are cached so that if the same query occurs again, the local DNS server can respond without having to contact another server.
- Root hints: File containing a list of all IP addresses of Internet root servers
- DNS Server service: Runs in the background and listens for DNS queries on UDP port 53.

## DNS Client
Like the [[Dynamic Host Configuration Protocol|DHCP]] client, the DNS client runs as a service that can be configured in the Services control panel in Windows. The client is responsible for communicating with a DNS server to resolve computer computer and domain names to IP addresses, so it's referred to as a "resolver". 

DNS resolvers maintain a local cache of the results of recent DNS lookups. The resolver cache speeds communication because it eliminates the need to communicate with a DNS server for records looked up recently.

An [[Operating Systems|OS]] must be configured to use DNS. At the very least, a client computer needs one address of a DNS server it can query. In Windows, the first DNS server configured is the preferred DNS server and the second one is the alternate DNS server.
![[Pasted image 20230901152836.png|centre|300]]
## Iterative and Recursive Query 
Recursive Query:
- A query that demands a resolution or the answer
- The initial request the resolver makes to the local server is a recursive query. The local DNS server must provide the information requested by the resolver
Iterative Query:
- A query that does not demand resolution 
- When the local server issues queries to other servers, the other servers only provide information if they have it

# Name Resolution
![[Pasted image 20230901160002.png]]
