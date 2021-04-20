### What problem does this paper address?

This paper tackles the same problem as RMT, namely bringing programmability AND performance to routers, but approaches it from the angle of making software routers performant rather than building programmable hardware.

### Do you believe the problem is/was important? Explain.

Yes, programmability is very important in the network in order to increase the pace of innovation. Whether or not the RB architecture is actually adopted is not as relevant as showing that high performance is possible in software routers.

### What is the authors' main insight?

There are two main insights, each with their own important details. First, the authors introduce a cluster server architecture connected in a full mesh (or optionally a butterfly topology) with each server acting as a port on a switch. Packets are processed by the ingress server then forwarded directly (or through an intermediate node) to the correct output server which simply forwards the packet. This architecture shows that if certain performance constraints can be met, the hardware costs of using commodity servers instead of a proprietary switch are much smaller. 

The second task is to dramatically improve performance at each server. To do this, the authors use a few tricks such as utilizing a multicore architecture, with each core processing one queue from the NIC, using polling instead of interrupts to avoid livelock, and processing the packets in batches to increase performance. These optimizations allow the servers to meet their performance targets and realize a performant and programmable (based on Click) software router architecture.

### Strengths/Weaknesses? Explain.

Failure scenarios? Lot of work based on very specific hardware assumptions. What happens to performance as more more custom packet processing is added.

### Any other comments/thoughts?

What happens when a server goes down - does the system fail gracefully? With so much more hardware than a switch, there are bound to be more failures.

### Did you enjoy reading this paper?

Yes!