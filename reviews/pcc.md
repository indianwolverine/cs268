### What problem does this paper address?

Congestion control!

### What is the authors' main insight?

The authors treat the network as a black box and perform congestion control, in the form of PCC, based on active measurements. The essential idea is that traffic is sent at say 2 different rates, the one which yields better performance is then used as an indicator to move rate towards. This is continued as long as the connection is active.

### Strengths/Weaknesses?

This is a very different approach for congestion control than the ones we have seen previously, and in a wider internet environment, seems more promising than any of them due to its black box approach. It will be interesting to see what other kinds of black box approaches are applied to this problem and how they interect with each other.

In a datacenter environment, where network characteristics are better known, this is probably not the way to go, since the network can likely be modeled more accurately here.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes.