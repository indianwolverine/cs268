### What problem does this paper address?

Datacenter applications require high bandwidth and low latency to operate well - TCP doesn't cut it as it ties up the host CPU to some degree and imposes overhead which results in low throughput, especially for smaller messages. RDMA is an attractive option since it allows direct NIC to reciever data transfer without interposing the sender CPU - this results in high throughput and almost no utilization impact on the sender and reciever. However, RDMA over IP networks suffers from its own set of problems related to congestion control and the congestion spreading characteristics of the underlying PFC protocol which ethernet must implement to provide the lossless abstraction. These issues must be fixed in order for RDMA to be widely deployed in the datacenter context.

### Do you believe the problem is/was important? Explain.

In the sense that congestion control is needed for RDMA over ethernet, sure.

### What is the authors' main insight?

Similar ideas as applied in DCTCP, except the receiver explicitly sends congestion notification packets to inform the sender and the sender starts sending at line rate before adjusting in response to congestion.

### Do you think the solution is a good one? Explain.

Maybe? 

### Any other comments/thoughts?



### Did you enjoy reading this paper?

No.