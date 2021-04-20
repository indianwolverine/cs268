### What problem does this paper address?

Congestion collapse on the early internet. Due to how TCP was implemented, senders sent packets at a rate much greater than switches could forward or hold in their buffers. This caused dropped packets, leading to massive observed drops in throughput due to TCP retransmits.

### Do you believe the problem is/was important? Explain.

Of course. Congestion can lead to enough degradation of user experience that if not addressed may have led to people simply not using the internet or enterprises developing their own solutions for data transmission instead of using and working on improving a common service for everyone. 

I'm not sure how much of a problem it still is, but since there really aren't any mechanisms preventing a host from sending packets at whatever rate it desires, it seems like an open problem in some sense. Also, the number of users and devices on the internet is definitely growing very fast and hasn't reached a saturation point yet, so unless infrastructure is growing at the same rate, congestion must still be a significant problem.

### What is the authors' main insight?

The authors model connections as pipes, with overflow resulting in congestion. This follows what they call the conservation of packets principle. They claim that packet conservation is violated due to 3 reasons and detail algorithms that are needed to address each in turn: 

1) The connection doesn't get to equilibrium - addressed by slow start algorithm, exponentially increasing transmission rate for each acked packet
2) A sender injects a new packet before an old packet has exited - addressed by a better RTT estimator which in turn leads to a better retransmit timer ameliorating the dropped packet/retransmit loop inherent in congestion collapse
3) The equilibrium can’t be reached because of resource limits along the path - addressed by exponential backoff and additive increase at steady state, which leads to the TCP sawtooth

### Do you think the solution is a good one? Explain.

It seems that in practice this solution works pretty decently, which indicates that it's a good solution! If we could better understand exactly what kinds of things are happening in a network, we might be able to develop a better model for congestion rather than using packet drops as a proxy for congestion.

### Any other comments/thoughts?

Not really, I'm not sure I even fully understand this problem after reading the paper or what the right way to approach it even is. I guess the ideal goal is to fully saturate network resources while sharing resources equitably, but this isn't an earth-shattering insight.

### Did you enjoy reading this paper?

Not really, reminded me too much of electrical engineering and physics and isn't an architectural paper. Important, nonetheless.