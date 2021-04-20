### What problem does this paper address?

Network configuration and management is a massive pain involving sets of arcane rules and incantations needed to achieve the desired effect. The main problem lies in the colocation of control and data plane functions in the same modules, which makes every action a distributed one and makes it very hard to define and execute policy over the entire network easily.

### Do you believe the problem is/was important? Explain.

Yes. As Professor Shenker mentioned in his one of his SDN lectures, networking like this is about mastering complexity when it should be about extracting simplicity. This coupled with the analogy of moving from closed, proprietary interfaces, hardware, and standards, to open analogues, underscores the importance of the work done in this and future SDN papers. The internet is beautiful architecturally, but I think the model of policy definition and distribution on the internet should match the policy domain one-to-one i.e. if I own a network, it should be trivial for me to control the policy enacted by it.

### What is the authors' main insight?

The authors take all of the control plane logic out of switches and put it in a centralized controller. Names are bound to each user and service trying to use the network, and these entitites must authenticate with the controller before they are allowed to use the network. When a new flow is initialized by a known entity, the first-hop switch forwards this packet to the controller, which then inserts flow entries into each switch along the path for this particular flow. The flow is then able to proceed. Policy can be enacted by programming the controller to undertake specific actions for certain entities such as dropping all packets from a given malicious host, or requiring questionable packets to traverse a specific path in the network. Thus, policy which is centrally defined the controller gets distributed to the entire network. 

There are many other important details in the paper which are relevant to achieving the vision outlined, but the key ideas presented concern separting control plane concerns from data plane concerns and logically centralizing the control plane for ease of management.

### Do you think the solution is a good one? Explain.

Yes, I think the idea follows naturally from an understanding of abstractions in the network. I also think this is a good use of the E2E principle in the sense that the network probably shouldn't be involved in all the control decisions required of it today but should instead do one thing very well. Policy is centrally decided per organization and it follows that policy should be centrally distributed as well.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

This was a really cool paper - excited to read more in this and related areas!