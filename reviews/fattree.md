### What problem does this paper address?

Because of the service oriented architecture of web facing products, there is a significant amount of traffic generated within a datacenter for each request as often may subservices must be queried to fulfill an incoming request. Because nodes in clusters need to communicate so much, inter-node communication bandwidth is a bottleneck to performance. To fix this, you can either use faster tech such as Infiniband which is not compatible with TCP/IP or buy custom high end hardware to provide greater bandwidth, but this is quite expensive.

### Do you believe the problem is/was important? Explain.

Yes, given the cost of hardware used to build a cluster, it's very important for enterprises to be able to use their resources effectively. I'm not sure whether network bandwidth in inter-node communication is a bottleneck to performance any longer, but certainly the idea of using commodity hardware for networking hasn't fully taken over yet and I think there's a lot of potential there.

### What is the authors' main insight?

The authors basically bring back a topological idea very common in circuit switching networks - they propose a Clos network, or what they call a fat-tree topology, constructed out of commodity switches, to provide maximum bisection bandwidth while remaining inexpensive. Essentially, a regular tree-like structure is created with several redundant paths for node to node communication. Each host and switch in this tree is given a predefined address and the switches contain two level routing tables which are preinstalled by a central controller with full knowledge of the topology. Because of how addressing is done as well as the two level routing scheme (which is fast due to TCAM), any node to node communication follows a set unique path, which allows nodes to reach full bisection bandwidth during communication and prevent congestion at links while only requiring commodity switches.

### Do you think the solution is a good one? Explain.

Yes. Ordinarily, a static scheme such as this would not the first choice in an internet environment, but given the special case that this topology is meant for data centers, the static scheme actually works really well. Datacenters are planned with a set amount of hardware from the outset, and this scheme allows planners to not only connect nodes with a high bisection bandwidth, but to do it cheaply and avoid throwing away money on custom hardware. Moreover, the centralized route distribution is also an attractive property within the datacenter context since it simplifies management.

### Any other comments/thoughts?

How widely is this deployed? Optimizations?

### Did you enjoy reading this paper?

Yes!