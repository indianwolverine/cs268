### What problem does this paper address?

Not really a problem so much as an exploratory study. The author wants to explore what the dynamics of the internet look like at the time.

### Do you believe the problem is/was important? Explain.

Yes - since we design protocols and architectures based on assumptions about the environment (the internet in this case), it's very important that the model we create of the environment is accurate.

### What is the authors' main insight?

The measurements are based on a framework where there are 35 internet sites which periodically being bulk TCP transfers with each other at distributed intervals and data is gathered at both the sender and reciever using tcp dumps.

There are a number of findings from these measurements:
- packet reorderings are fairly common, and reordering patterns are asymmetric between sites
- heuristics such as increasing window size and reducing the number of dups required before retransmit can improve TCP retransmit accuracy
- packet corruption may occur frequently enough to merit a larger checksum in the TCP header
- a new technique involving sending bunches of packets can be used to estimate bottleneck bandwidth, but must be run at sender and reciever since routing asymmetries are common in the internet
- packet losses occur in bursts and significant portion of TCP retransmissions are rdeundant
- ack packet timing compression could be common, leading to TCP ramp up causing network stress

### Do you think the solution is a good one? Explain.

Yes, I think the experiment setup and statistical analysis of the results are both sound and rather than assuming a certain model of the internet try to build a model by reasoning about the kinds of events which could be happening in the internet and using these events to tweak the model.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Not at all - very boring and dry. I'm not sure the results were so interesting that they merited 14 pages.