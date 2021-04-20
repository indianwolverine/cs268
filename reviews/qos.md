### What are the key strengths/contributions of this paper?

The authors propose extensions to the internet to support an integrated services (IS) model (best effort, real time, and controlled link sharing). The key idea here is to have soft state in routers concerning flows of traffic so that QoS and auth* decisions can be made easily in the network. The nice thing about this approach is that it doesn't fundamentally change the existing architecture and is backwards compatible - it's just an extension to the internet to enable the IS model.

Along with the model, a reference implementation is provided. In the forwarding plane, a classifier maps incoming packets into predetermined classes and sends these to the appropriate queue of many managed by the packet scheduler. The packet scheduler then decides which packet to forward next from its set of queues. In the control plane, there is a reservation setup mechanism as well as various daemons (in addition to the routing daemon) which modify the policies the classifier and packet scheduler use.

### What, if any, would you say are the weaknesses of this paper?

Flows exist over multiple routers, so if there is a bottleneck downstream, won't this invalidate any QoS guarantees made upstream. In this distributed system, how can promises made only at one node be fulfilled without complete knowledge of the network i.e. if an application makes some sort of reservation which guarantees it a QoS, how can that result be reliably ensured by the network without resorting to what essentially amounts to circuit switching?

Similar to the ActiveNet idea, this proposal is putting a lot more logic into the routers, which reduces our ability to reason about network behavior even further. It might be better to centralize policy decisions somehow and then distribute these decisions to routers under administrative control so that routers are as dumb as possible, easier to reason about, and easier to debug in case of failure. Already with BGP we see a lot of failures simply due to misconfigurations which take down large swaths of the internet at times - with more added complexity in what should be a dumb layer comes the added likelihood of catastrophic failure.

### Would you say this is an important paper? Why?

Yes - one thing this paper does really well is not only present a fully formed architecture, but also a reference implementation along with it. I think it's very important to follow this model. For example, the ActiveNet idea may have gained more traction had there been an implementation. The reference implementation in this paper makes the goals of this paper seem realizable.

### What, if anything, did you find surprising about this paper?

The most surprising result is actually the guaranteed delay bound work by Parekh which the authors cite in the paper - this seems not at all possible!

### Any other comments/thoughts? (This is a good place to note topics that you'd like to see discussed in class)

What kind of impact did this paper have - is this how we do QoS in the internet today? If not, what are the approaches used? Has there been any work on computing policy decisions centrally then distributing these to routers in the form of say priority schedulings?

### Did you enjoy reading this paper?

Yes, the ascii art was very fun! On a more serious note, I enjoyed the fact that a lot of implementation details were more fleshed out in this paper.