### What problem does this paper address?

This paper looks at the BitTorrent protocol, which claims to provide positive incentives for swarm participants to contribute capacity, and try to show that this incentive scheme does not in fact work, and is vulnerable to exploitation by strategic clients.

### Do you believe the problem is/was important? Explain.

Not really, is BitTorrent even used at any scale? This seems like more of a economics problem than anything else, and in that sense I guess insights/approach here may be useful for determining incentives on the internet at large. I think it would have served the paper well to try to suggest a protocol which provides a better incentive structure than BitTorrent.

### What is the authors' main insight?

The authors conduct a series of tests to identify sources of altruism in the network. For example, they find that high capacity clients contribute a high amount of altriusm in the network as they take quite a while to reach a point where they download in equal proportion to their uploads. Moreover, beyond 14KB/s, reciprocal peering is almost guaranteed, indicating that any additional upload is purely altruistic. 

Given this information, the authors develop BitTyrant, a strategic client which takes advantage of the altriusm in the swarm by attempting to maximize reciprocation bandwidth (try to peer with highest capacity clients first), maximize number of reciprocating peers (budget upload bandwidth to maximize probablity of reciprocation from maximum number of clients), and finally lower upload contribution (as long as reciprocation is still assured).

### Strengths/Weaknesses?

This paper conducts a detailed exploration of the BitTorrent space, which I found was very valuable, and uses this exploration to inform the implementation of the strategic client. 

However, a more important problem in my opinion is the construction of an incentive structure, or set of clients in the current structure, which cannot be exploited and instead encourage contribution to the swarm.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes!