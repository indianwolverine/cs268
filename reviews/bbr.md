### What problem does this paper address?

THe authors argue that loss-based congestion control is no longer optimal for the network as network transmission speeds have increased by several orders of magnitude and as it leads to buffers constantly being full and packet loss to occur, which leads to high latency for packet transmission at bottleneck links. The authors seek to develop a congestion control protocol which aims to saturate bottleneck link capacity only, and keep buffers as empty as possible.

### Do you believe the problem is/was important? Explain.

Yes, definitely the problem of high latency in the network seems like an important one, and if there really is a better operating point the network can converge to, it seems valuable to develop a protocol to get there.

### What is the authors' main insight?

The authors develop an algorithm which tries to estimate bottleneck bandwidth and RTT, and use these values to calculate the bandwidth delay product, which is the optimal operating point for sending traffic into the network.

### Strengths/Weaknesses?



### Any other comments/thoughts?



### Did you enjoy reading this paper?

No, again a lot of control theory kind of thing, not very fun to read.