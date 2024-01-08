---
alias: HTTP
---
#networks 
Hypertext Transfer Protocol (HTTP) is the protocol Web Browsers use to access data on the World Wide Web. Originally, its main purpose was simply to transfer static Web pages written in HTML. Now HTTP is also used for general file transfer, downloading and displaying multimedia files and delivering scripts for animated and interactive Web pages.

Because it's often used to transfer large amounts of data over the [[Internet, Intranet, Extranet|Internet]], it uses [[Transmission Control Protocol|TCP]] as its Transport-layer protocol and the default TCP port number is `80`. HTTP identifies and locates network resources by a Uniform Resource Locator (URL).

# Web Client/Server Communication
**Web Clients** communicate with a web server, using HTTP i.e. Chrome, Firefox, etc. Clients will submit a HTTP request to a Web server

A **Web Server** provides response messages to the client. As well as providing web content that can be accessed through the internet. 

The client initiates a contact with the Web server to request for a service. The user types a URL into a Web browser:
![[Pasted image 20230901173411.png|centre|200]]
1. The browser first contacts to a DNS for resolving the targets IP address
2. The DNS replies with the corresponding IP address for the web server
3. The web browser connects to the web server sending a HTTP request for the target website with a TCP 3-way handshake
4. The web server receives the request and checks for the request message. If the requested page exists, then the web server replies it; else it sends a HTTP 404 error message
5. The web browser receives the requested page and then the connection is closed
6. The web browser then parses through the web page information and looks for other page elements it needs to complete the web page
7. For reach element needed, the web browser makes additional connections and HTTP requests to the server for reach element
8. When the browser has finished loading all images, info, etc. the page will be completely loaded in the browser window.

# HTTP Encapsulation
Example of how layers work together:
- You start your Web browser with a web site address
- The web browser formats a request for your home page by using the Application layer protocol HTTP.
- The Application layer protocol passes the request down to the TCP
- TCP adds a head to the request
- The unit of information the Transport layer works with is called a segment
- TCP passes the segment to the internetwork layer protocol (IP)
- IP places its header on the segment
- The unit of information is now called a packet
- The packet is passed down to the Network access layer, where the NIC operators
- A frame header and trailer are added
- The frame is delivered to the network medium as bits 
- The web server processes it and returns a web page

## Locating a Resource Object
Every object on the internet has a unique Uniform Resource Locator (URL). All URLs consist of four parts:
- Service type
- Host or domain name
- Directory or subdirectory information
- File name

