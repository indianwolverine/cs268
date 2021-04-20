### What problem does this paper address?

TCP is inefficient and unstable on networks with high bandwidth-delay product. It's slow start phase can lead to instability in the network, it doesn't ramp up fast enough in the AIMD phase to more optimally utilize bandwidth, and relies on packet loss as a proxy for detecting congestion in the network.

### Do you believe the problem is/was important? Explain.

Yes, even Jacobson and Karels maintain that congestion control will need to evolve as the network does. One especially interesting point the authors bring up is that we will need new protocols which can cope with the delay in e.g. satellite networks. As we move forward and deploy more and more devices in space and eventually to other planets, we'll have to completely reimagine networks and protocols to work in these drastically different environments.

### What is the authors' main insight?

There are a few key ideas which contribute to XCP, the new TCP-like protocol devised by the authors. 

First, as part of the XCP packet header, senders can communicate their current cwnd and rtt estimates to routers as well as a desired sending rate. Based on this information, bottleneck routers can then set feedback for the sender each rtt to adjust their sending rate. 

Second, utilization and fairness are separated into distinct modules in XCP routers rather than per flow. At each average rtt interval, the router determines the utilization of the link aggregate over all the flows and determines an aggregate feedback. This aggregate feedback is the distributed proportionally by the fairness module to each flow in proportion to their share.

Using these techniques, senders are able to quickly adjust their rates to maximize utilization through a bottleneck link while avoiding congestion.

### Do you think the solution is a good one? Explain.

Yes, the control theory work around proving stability was compelling as well as the fact that this protocol maximizes utilization of network resources while imposing minimal overhead and allowing simple mechanisms for fairness and QoS. It doesn't seem like XCP is widely deployed, which I'm guessing is due to the changes required in routers as well as the protocol headers? 

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes, it was very thorough in exploring a design from first principles, proving it with rigorous math, and conducting a nice evaluation.