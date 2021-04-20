### What problem does this paper address?

From a large study of enterprises, the authors find that companies deploy around the same amount of middleboxes as they do switching and routing hardware. This hardware comes at a steep cost in terms of price and management complexity and introduces hard to diagnose failure modes into the network. The paper tries to find a solution to manage enterprise middlebox deployments more effectively.

### Do you believe the problem is/was important? Explain.

Both in the sense that we should aim to reduce operational cost for managing hardware and in the sense that network hardware vendors make an awful lot of money for their proprietary devices, I think this is an important problem economically. And since systems research is motivated by economics, this is at least a valuable problem to solve.

### What is the authors' main insight?

The authors introduce APLOMB, a gateway and a controller which are used in concert to shuttle enterprise traffic through middleboxes hosted in the cloud. The main idea here is to outsource as much middlebox hardware out to the cloud as possible in order to reduce both hardware and management costs. Basically, the APLOMB controller ensures that the proper forwarding tables and NATs are set up in the cloud and the APLOMB gateway, enacting the network policy. Then, both ingress and egress traffic through for the enterprise network is routed through the cloud middleboxes, ensuring complete mediation, and done so in a latency and locality aware manner in order to preserve the traffic semantics that middleboxes have come to expect and application expectations in terms of latency and bandwidth.

### Strengths/Weaknesses?

It isn't obvious how ABLOMB would work across cloud vendors, which is an important consideration since network traffic through the cloud can get quite expensive. Moreover, now that we've exported this functionality to the cloud, what guarantee is there that cloud vendors will provide native middlebox support?

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Not really, maybe I'm missing some context on the problem, but the solution seems like a bandaid fix to a problem problem which deserves a more integrated solution.