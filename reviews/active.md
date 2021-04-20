### What are the key strengths/contributions of this paper?

The authors propose ActiveNet, a new network architecture in which arbitrary application code can be executed at network nodes rather than at endpoints. They motivate this architecture using existing functions which are already present in the internet - middleboxes such as firewalls, web proxies, and nomadic switches are already stateful entities operating on the internet which execute some code per packet in addition to forwarding. 

The main idea here is that with an active network i.e. a programmable network which performs computations on user data, e.g. the load on the network can be reduced by placing computation near users (which edge computing does today!) while allowing various new functions to proliferate on the network. The abstraction moves from a standard way of handling packets to providing a standard programming environment for packets.

Architecturally, the ActiveNet would be organized with a set of active nodes which would run some computation on incoming "capsules". These capsules would be bits of program logic, which could specify how they want to be handled by the node i.e. whether they are to be forwarded just like a normal packet or run some computation on the node.

### What, if any, would you say are the weaknesses of this paper?

There is a fundamental push and pull here between allowing program expressiveness and ensuring safety of the network. If capsule programs are given too much leeway in how they can use network resources, there's likely little that can be done to prevent abuse. On the other hand, if the programming environment isn't expressive enough and limited in scope and accessibility, what's the point? 

I also would've liked to see examples of what might be accomplished on an ActiveNet which isn't possible or intractable on the internet.

### Would you say this is an important paper? Why?

Maybe. This paper brings up ideas which are still very important today such as research related to edge computing where nodes near the users are doing some legwork to reduce the burden on DC nodes and also network resource allocation and safety, which are important considerations in the cloud and especially now with the rise and development of serverless platforms.

However, it's not immediately clear why ActiveNets are much better than the internet. This may be a case where an idea didn't take off simply because the existing technology was good enough, so why waste the engineering resources to build something new and not obviously much superior.

### What, if anything, did you find surprising about this paper?

It's nice to see a reimagining of what an internet might look like and it was surprising to see that the authors were even considering things like resource constraints, sandboxing, authentication etc. 

### Any other comments/thoughts? (This is a good place to note topics that you'd like to see discussed in class)

I'm really curious about what kinds of applications are enabled by this architecture. What can we do easily in an ActiveNet (monitoring, congestion control, load balancing, firewalls)? Also, even if we can do those things, is it advisable to? When is a centralized approach better? Also, not convinced at all that this design does not violate the spirit of the end to end principle as it makes it very hard for higher layer protocols to reason about the underlying network infrastructure.

### Did you enjoy reading this paper?

Yes and no. I like that the authors presented a bold vision, but they focused too much on technology which would enable the architecture (sandboxes, IRs, compiler features) rather than what could be accomplished with the architecture. If the architecture is compelling enough, I feel that the implementation can be figured out. For example, serverless platforms present an enormous engineering challenge if they are to support the API they advertise, but they are compelling enough that a lot of engineering effort is being directed to solving the implementation details.