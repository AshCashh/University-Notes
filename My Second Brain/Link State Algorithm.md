---
tags: [algorithm, networks]
Created: 2024-04-20T15:58:58+10:00
Modified: 2024-07-03T19:35:33+10:00
---
Based on the Dijkstra's Least-Cost algorithm, the algorithm finds all possible paths between two locations and in doing so, gets the least cost path. It does this by having each router generate information about only its direct connected links, hence building adjacencies with neighbouring routers. Most common implementation: [[Dynamic Routing#Open Shortest Path First]] (OSPF).
![[Pasted image 20230820133413.png|center|300]]
Link state advertisements (LSAs) are exchanged throughout the network in order to update routing tables. LSAs are advertised only upon startup and when changes in topology are detected (not periodically).