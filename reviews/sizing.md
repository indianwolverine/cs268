### What problem does this paper address?

Commonly held wisdom states that bottleneck routers should have enough buffer space (RTT x C) so that they are fully utilized during TCP congestion avoidance phases when the cwnd gets cut in half due to packet loss. The idea is that during this period of catching up for the sender, the buffer should have already had enough packets queued up from the sender such that it can keep sending packets while it waits for the sender to saturate the link again. The authors argue that this buffer space requirement is too large, and places undue stress on router manufacturers.

### Do you believe the problem is/was important? Explain.

Maybe? What are the trends for memory in routers - is it getting cheaper anyway? If so, then I don't see much of a problem. Otherwise, it doesn't seem like overprovisioning buffer space is necessarily a bad thing, given that there are a host of other reasons buffer space can be useful besides just maximizing bottleneck link utilization.

### What is the authors' main insight?

The authors observe that the RTT x C rule comes from assuming that TCP flows are synchronized through a bottleneck router and so their behavior is in phase and has dynamics identical to a single large TCP flow. In practice however, the authors observe that bottleneck routers handle on the order of tens of thousands of flows, and at that scale, TCP synchronization is not observed, and instead the aggregate flow looks more like a smooth line. Given this insight, the authors then do some math to show that much less buffer space (RTT X C / sqrt(N)) is required to keep the bottleneck link saturated in response to TCP dynamics.

### Strengths/Weaknesses?

UDP?

### Any other comments/thoughts?



### Did you enjoy reading this paper?

It was presented well, but I find this kind of work boring in comparison to architectural work.