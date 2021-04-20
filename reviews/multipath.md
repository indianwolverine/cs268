### What problem does this paper address?

The single path assumption in TCP creates a number of problems in load balancing and is not congruent with the inherent multipath nature of networks today.

### What is the authors' main insight?

The authors propose multipath TCP in which subflows are opened up along separate paths in the network and a subset of packets is sent along each subflow depending on path characteristics.

### Strengths/Weaknesses?

For long flows in a datacenter context, this seems like a good solution in terms of load balancing.

For short flows, this doesn't seem like a good solution, since we now have multiple handshakes which need to be completed even to use multipath TCP.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes.