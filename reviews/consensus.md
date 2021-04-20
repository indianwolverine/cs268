### What problem does this paper address?

Due to how the BGP protocol works, consistency problems often occur where traffic is either blackholed or gets stuck in forwarding loops for several minutes, which leads to internet outages for many customers.

### What would you say are the paper's main strengths?

The authors present a clean design to address the consistency problems in using BGP for interdomain routing, acounting for general routing schemes which are actually present within the internet. Moreover, they show through evaluations that their scheme actually works, which is impressive considering the complexity inherent in implementing consensus related systems.

### What would you say are the main weaknesses of this paper? 

This solution is pretty complex and its meant to replace a pretty complex solution (BGP) for interdomain routing which comes with its own set of design issues. I'm not sure consensus routing is as easily understandable and debuggable for network operators as the authors make it out to be. It certainly presents a clean result to the problem of maintaining consistent routes, but at the cost of complexity which is decently difficult to understand. However, given a design where the consensus modules are centralized per AS, I think it could work, but there might not be an impetus to switch to CR given the established tribal knowledge surrounding BGP.

### Do you think Consensus Routing (CR) is incrementally deployable? In answering, make sure to distinguish between whether you think it is technically feasible to incremental deploy CR vs. whether you think it is likely that carriers will deploy CR in practice. 

I think it's certainly possible to deploy CR given enough backing by the big players in the internet. Since most traffic goes through a few telcos anyway, if these carriers agreed to deploy the consensus scheme deployed in the paper, it could happen. However, I don't think CR would be favored by smaller carriers, as the design stipulates that a few big AS's agree on AS sets and valid routes for the entire system, which gives them a lot of power in determining policy for the entire internet, especially if a simple majority of these tier 1 AS's were to collude. It might be more interesting if smaller carriers were required in the consensus part of the architecture - this could give them more power in the internet to decide policy, which could level the playing field against big carriers.

### Any other comments/thoughts?

Does interdomain routing have to be this difficult? If we could design from the ground up, is there a clean design that achieves the policy goals of interdomain routing?

### Did you enjoy reading this paper?

Yes.