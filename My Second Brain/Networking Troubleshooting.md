#cs #networks 
The daunting task of supporting a complex internetwork can be both challenging and rewarding. Successful network administrators need to draw on a variety of skills, technologies and techniques to meet the increasing demands of [[LAN, WAN, MAN|LANs]] and [[Networks]]. 

There are many approaches to troubleshooting and different situations call for different approaches. 

If further information is required, refer to the textbook.
# The Problem Solving Process
One of the most difficult aspects of network problem solving is deciding where too begin. What's described below is a general framework for approaching problems that you can apply in almost any situation. The specific actions you take depend on the situation. Here are the steps of the problem solving process:
1. Determine the problem definition and scope
2. Gather information
3. Consider possible causes
4. Devise a solution
5. Implement the solution
6. Test the solution
7. Document the solution
8. Devise preventive measures
![[Pasted image 20230827112934.png]]

# Trail and Error
The trail and error approach ti network problem solving isn't very scientific, and technical purists often frown on it. Nevertheless, few network specialists can deny having used it in everyday practice. There's a time and place for it, although you shouldn't rely on this method exclusively because you can do more harm than good in some situations.

This approach can be used under the following conditions:
- The system is being newly configured, so no data can be lost
- The system isn't attached to a live network, so no other users are affected by changes
- You can undo changes easily
- Other approaches may take longer
# Solving by Example
This is the process comparing something that doesn't work with something that does and then making modifications to the non-functioning item until it performs like the functioning one.

A copy of configuration can be used as a model to base on or to modify from. Often you should only use when the working sample has a similar environment as the machine with the problem. Don't make changes that could cause conflicts and be careful to not destroy data.
# The Replacement Method
Considered a favourite among PC technicians. It requires narrowing down possible sources of the problem and having known working replacement parts on hand so that they can swapped out.

Follow these rules in order when using this method
1. Narrow the list of potentially defective parts down to a few possibilities
2. Make sure you have the correct replacement part on hand
3. Replace only one part at a time
4. If your first replacement doesn't fix the problem, reinstall the original part before replacing another part.

# Step by Step with the OSI Model
In this approach you test a problem starting at the Application layer and keep testing at each layer until you have successfully tested or reached the Physical layer. Depending on the problem, you could instead start at the Physical layer and work your way up.

### Scenario 
A user at PC A complains that an error occurs when she tries to access files on the File Server, but users at PCs B and C are not having the same problems. Using the File Explorer to browse the network, no devices are shown.

Bottom up approach (Physical -> Application):
- Check the cabling, is it damaged? Is it plugged in? Are the link lights on the NIC
- Check the NIC driver is functional and installed correctly
- Check the addressing settings
- Use ping and tracert to check

# Common Problems
![[Pasted image 20230827115925.png]]

# Network Troubleshooting Tools
- ICMP-based utilities
- Network monitors
- Protocol analyser
- Cable testers
- The Internet
- Vendor support services
- Experience
- Network Documentation
## Use Ping for connectivity troubleshooting
- Run `ipconfig /all` to display all related addressing information
- Ping the loopback address to verify that TCP/IP stack is functioning correctly
- Ping the local IP address to verify the computers capability to receive ICMP packets
- Ping the default gateway to identify the scope of the network problem
- Ping the target host
- Ping DNS servers
