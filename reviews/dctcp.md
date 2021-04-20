### What problem does this paper address?

Due to how services are structured in datacenters, there is often a lot of fanout for each incoming request, requiring low latency reponses from many servers in order to complete. However, the datacenter network also carries long flows which require high network utilization in addition to these small flows and bursty events. The authors observe that a variety of factors, including incast from the services workload involving small flows as well as pressure on the queue and shared buffers of switches leads to degraded latency for small flows, which then degrades performance for the end user.

### Do you believe the problem is/was important? Explain.

Maybe. One simple fix here might be to just have higher link capacity and maybe route flows/place services better - it's not clear whether the network topology here is similar to VL2 or if its a more primitive topology. 

### What is the authors' main insight?

The authors propose DCTCP, a simple modification to TCP where switches mark packets with the ECN bit if the queue size exceeds some threshold. Receivers coordinate to send selective acks to senders, and sender then adjust their cwnd by calculating the proportion of acks they receive with the ECN bit set and then lowering their cwnd by that (1 − α/2) where α is the proportion. When congestion is low, cwnd decreases gradually, but if it is high then DCTCP approaches the behavior of TCP and cuts cwnd in half.

### Do you think the solution is a good one? Explain.

Yes, probably the coolest thing about this solution is that it leverages the ECN mechanism already present in switches and is motivated by rigorous measurements of the datacenter environment and then evaluation of the algorithm.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes, it seems to be a common theme with these Microsoft papers which are motivated by actual measurements and practical solutions which interface easily with existing technology.