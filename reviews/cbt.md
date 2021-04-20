### What are the key strengths/contributions of this paper?

The authors first discuss the key properties they seek in a multicast protocol: 
1. Conformance to the Host Group Model (defines API and semantics of multicast)
2. High probability of delivery
3. Low delay (latency)
4. Scalability (Internet scale)
5. Robustness
6. Information hiding
7. Routing algorithm independence
8. Multicast tree flexibility (tune tree per application requirements)

Then, they detail the problems plaguing current multicast implementations, some of which include - the lack of scalability in DVMRP due to flooding of packets required through entire internet for each (source, group) tuple, requirement for routers not involved in a multicast tree to maintain state for that tree, tight dependence on underlying unicast algorithm.

Their solution is the core based tree (CBT) architecture. Essentially, a router (or many) is chosen as the core of a spanning tree which connects all members of a multicast group (one such tree per group). Packets intended for the group are first routed to the tree, and then propagated throughout the tree to all recievers.

There is a protocol which accompanies this architecture. For each multicast group there is a group name. A directory service is used to map group names to core addresses and a group id. Packets are forwarded first to the core addresses using unicast, then on the tree they are forwarded using the group id. Joining and pruning semantics also exist.

### What, if any, would you say are the weaknesses of this paper?

There's no evaluation of the architecture, simulated or in reality! Although it seems like this solution would scale, it would still have been nice to see some comparison to the current multicast proposal.

The authors are essentially proposing a system of centralization which is quite static and I imagine prone to misconfiguration. In todays internet, surely there are far too many multicast groups to be statically allocated among a set of core routers. Why not use a mechanism where packets are sent from some source to a core router or routers, then recievers can register with these routers for updates, kind of like an internet-wide pub-sub system. The directory service could be used to advertise sets of routers which are responsible for distributing packets for certain groups dynamically. Also, instead of having a separate complex protocol for multicast routing, such a system could piggyback on unicast with the directory service and the core routers scaling independently.

The authors mention multicast tree flexibility as a goal but then don't talk about how this architecture will accomplish that.

### Would you say this is an important paper? Why?

Yes. I think this is powerful way of thinking about multicast. The solution is elegant and not all that complex, and it doesn't interfere with the current operation of the internet. There are a number of open issues which arise from the architecture, such as allocation and ownership of core routers, but this paper seems like a step in the right direction. Maybe different multicasts could be used for different administrative layers, such as something for LAN's, something else between AS's etc.

### What, if anything, did you find surprising about this paper?

No built in mechanisms for security! We've been here before, and it's clearly a problem on the internet. Now, with multicast and it's potential to dynamically generate loads of packets, denial of service becomes even more of a problem.

### Any other comments/thoughts? (This is a good place to note topics that you'd like to see discussed in class)

Based on a quick google search it seems like CBT is at least partially used in the current multicast solution for the internet. I wonder what relative performance of different solutions looks like and if this is still an open problem? Maybe things like remote online gaming present stringent requirements which current multicast can't handle? How prevalent is network layer multicast in the internet? 

### Did you enjoy reading this paper?

Yes! It's neat to see a clean simple design address the scalability issues of the original multicast proposal and then an in depth protocol spec. I really would've liked to see at least a minimal implementation though.