### What problem does this paper address?

Interdomain routing via BGP suffers from a number of issues: routers are running complex distributed computations to determine forwarding paths and as such often do not operate on a consistent view of the network, there are a number of nuanced interactions between eBGP, iBGP, and IGP which are hard to reason about, debug, or control, and BGP exposes its implementation details which are complex and hard to manipulate when it should instead expose abstractions for operators such as allowing path selection and easily configurable export and import policies.

### Do you believe the problem is/was important? Explain.

Yes, we still see a large number of outages in the internet due to BGP misconfigurations. I wonder however if an abstraction can be engineered on top of BGP which exposes the abstractions desired and allows configuration at the policy level without having to worry about BGP internals.

### What is the authors' main insight?

The key insight is centralization of AS routing function. The authors propose RCP, a centralized routing control platform, one per AS as they envision. RCP will be able to learn the internal topology of the AS and interface with other AS's, allowing operators to more easily configure policy and let RCP handle the encoding of the policy on the routers within the AS. Routers themselves will do nothing more that forward packets. 

### Do you think the solution is a good one? Explain.

In the sense that it is able to interface with existing infrastructure and be incrementally deployed, I think it is a reasonable idea. However, it's hard to say if RCP can scale, even within a single AS, especially if there is a lot of network churn. To be robust, RCP will necessarily have to have a backing replicated state machine, current implementations of which can only handle a certain volume of writes - this might not be enough for configuring policy in a network under constant change.

I also think cetralization on the AS level is a good thing, at least in the sense that this is already the way the internet operates policy-wise, so why not align the infra with this organization structure as well.

### Any other comments/thoughts?

I couldn't find much about whether RCP is deployed on the internet anywhere, so I'm curious about it's industry impact. Or perhaps the idea of centralization and separation of control and data planes are the main contributions of this paper, with better solutions superceding it?

### Did you enjoy reading this paper?

Yes.