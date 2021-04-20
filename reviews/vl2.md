### What problem does this paper address?

Many enterprises have moved to a service oriented architecture model within their datacenters. These services are often hosted on VMs or containers running on top of servers. To maximize utilization of datacenter resources, it is important to be able to dynamically reallocate services to servers on demand, whether in response to load, planned maintenence, or outages. Current tree-like network architectures however limit fast reallocation - due to bandwidth limitations between arbitrary servers, services must often be collocated in order for efficient communication.

### Do you believe the problem is/was important? Explain.

Yes, since the success of datacenters depends on the promise of economies of scale, near optimal utilization of resources is very important to acheiving this vision. I'm not sure if this is still an open problem - at least at Facebook there didn't seem to be anything too crazy going on with how datacenter networks were structured.

### What is the authors' main insight?

VL2 is structured to provide the illusion to services that they are connected via a single Ethernet switch. This means that services should be able to communicate with each other at NIC line rate, services should be able to be arbitrarily assigned to any server, service traffic should appear to be isolated from other services' traffic, and services should simply be able to communicate via IP agnostically.

To acheive this vision, VL2 structures switches in a folded Clos network using commodity switches, which provides maximum bisection bandwidth to servers. Each server has an application address (AA) and each switch has a topology dependent location address (LA). Servers send packets to other servers using the AA, which is transparently translated to a LA for the switch the reciever is connected to by the VL2 agent on each machine. The AA to LA mapping is maintained by a directory service backed by a replicated state machine running Paxos under the hood. Switches calculate paths via link state routing and this scheme allows servers to communicate without regard to toplogical addressing as in the Fat-tree paper. To avoid congestion, traffic per flow is spread over random paths to intermediate switches using anycast and ECMP.

### Do you think the solution is a good one? Explain.

Yes, the design is motivated by actual observations and measurements in the datacenter by the authors which lends it credibility. The decoupling of addressing in communication from the underlying topological address is probably the key idea here which makes VL2 feasible in for an enterprise compared to Fat-tree for example. Furthermore, the thorough evaluation of VL2 in the paper shows that it is a good solution.

### Any other comments/thoughts?

Instead of having IP addresses act as names, why not service names as names with static IP's underneath? I guess how services were coded by default required some knowledge of IPs and that's why this approach was taken, but what's the story now at Azure? More importantly, what are some of the big problems being tackled now in the datacenter context, in the edge context, in the mobile context etc. regarding networking and Azure?

### Did you enjoy reading this paper?

Yes, I like that actual data motivated the design of VL2 rather than conjectures about datacenter traffic characteristics and I think this is a very important thing to keep in mind. And I really liked the evaluation following the design.