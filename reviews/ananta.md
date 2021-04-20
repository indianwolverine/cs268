### What problem does this paper address?

Load balancers for datacenters are under heavy load since they have to handle all inbound traffic. As such, they are often a major point of failure and need to be engineered to be scalable, robust, and graceful in failure scenarios. The goal of this paper is to design and implement an L4 load balancing service to meet these demands.

### Do you believe the problem is/was important? Explain.

Yes, in the context of load balancers being a mojor cause for site outages, it's very important to design load balancing to be scalable and resilient.

### What is the authors' main insight?

There are several key ideas here which fit together to acheive the goals outlined in the paper. First comes the observation that there is a significant amount of ingress and inter-service traffic in the datacenter and that these are the classes which form the bulk of traffic in the datacenter, so any solution must be optimized for these traffic patterns.

There are three layers in the data plane: the first tier load balances traffic at L3 to tier 2, a pool of muxes. The muxes use consistent hashing to the correct DIP (physical address) given the incoming packet VIP (virtual address associated with service) so the tier 1 routers can send traffic to any mux using ECMP allowing efficient scale out. Importantly, the muxes are implemented on commodity servers, which relaxes the constraints of traditional network hardware and APIs but also limits performance to a degree. The third tier, a host agent on every machine, intercepts packets, decapsulates them for the DIP and forwards them to the correct VM. Services can then communicate directly with the source using DSR and the host agent will translate the DIP to a VIP associated with the service. A separate Ananta Manager maintains fully replicated (backed by Paxos) mappings of VIPs to DIPs which it distributes to muxes. Further interposition by the host agent allows services to communicate directly without use of the muxes - called fastpath, this covers the important case of intra-DC traffic.

### Do you think the solution is a good one? Explain.

Yes, there are a number of important principles here such as the decision to do most of the network computation at end hosts to relieve the network, direct server return to reduce mux burden, consistent hashing for mapping flows to instances of services, and direct service to service communication fully leveraging the Clos topology. Moreover, the work is motivated by actual observations in the datacenter and evaluated in both a simulated and real world environment, which likely indicates that it is good.

### Any other comments/thoughts?

Since packets from a flow can end up at any mux, how significant of a problem is packet reordering in TCP flows? The upgrade problem seems like a bigger deal than elaborated on in the paper - what is the process for upgrading something like a load balancer which must pretty much always work? Does the solution involve hot pluggable code as in Erlang, or is their a backup tier which traffic is directed towards or do tenants just take the performance hit during upgrades? 

### Did you enjoy reading this paper?

Yes. Clean design and implementation running in a real environment. This kind of thing and bold architectural visions are the coolest things in CS research in my opinion.