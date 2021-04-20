### What problem does this paper address?

This paper addresses the problem of building datacenter networking architecture with high bisection bandwidth while allowing for flexibility in incrementally deploying new servers and switches on the network - something the fat-tree topology doesn't account for in it's rigid topology specification. 

### Do you believe the problem is/was important? Explain.

I'm not sure I buy the argument that incremental expansion is an important problem now. Maybe enterprises hot plug servers in response to prolonged unanticipated load, but it's hard for me to imagine that datacenters aren't constructed very regularly with plans set in stone years in advance.

### What is the authors' main insight?

The authors introduce Jellyfish, a new datacenter network topology constructed out of a random regular graph. The motivations for such a topology are twofold - it achieves the goal of incremental expansion since it's very easy to plug in new servers and switches in this topology while maintaining the guarantees promised, and it achieves the goal of greater network utilization since in a random regular graph it is possible to reach more nodes with fewer hops than in fat-tree which leads to more paths available for packet forwarding. 

### Do you think the solution is a good one? Explain.

Using a k-shortest paths with MPTCP approach for routing, Jellyfish certainly outperforms fat-tree in a variety of different evaluation scenarios such as being able to support more servers for the same cost and being more resilient to failures. The evaluation certainly lends credibility to Jellyfish being a competitive datacenter networking topology. It seems however that the setup complexity and overhead of Jellyfish are too high to replace Clos network topologies which are much easier to reason about and possibly maintain for operators.

### Any other comments/thoughts?

What does this do for debugging? A less regular network architecture seems like it might be more difficult to reason about in failure scenarios. 

I also wish there had been more said about the degree-diameter graphs which seem to have interesting properties useful for maximizing bisection bandwidth and network utilization since I'm not entirely convinced incremental expansion is really a huge use case now for large enterprises.

### Did you enjoy reading this paper?

Yes - a very simple idea on the surface leading to several interesting properties with a thorough evaluation. After reading this, fat-tree, and Ananta, I'm very curious about the state of datacenter networking today and what kind of considerations are actually the most important when building and running datacenter networks. This is an instance where I really wish large enterprises would expose the latest work they've done for the benefit of the research community.