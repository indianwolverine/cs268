### What problem does this paper address?

Implementing a new control plane function in the network involves dealing with a many low level primitives such as state distribution, element discovery, and failure recovery in order to build the functionality actually needed in the first place. This has led to a glacial pace of innovation and difficulty of management for network control planes - the authors seek to fix this.

### Do you believe the problem is/was important? Explain.

Yes in the sense that forcing all of this distributed complexity on control plane protocols is inherently a bad design and requires reevaluation.

### What is the authors' main insight?

Borrowing from systems ideas of creating a narrow, well-defined interface (think Unix syscalls, RVM, etc.) for control plane protocols to build on top of, the authors present Onix, a platform which interfaces with all the raw network hardware and exposes an abstract view of the network to applications running on top of it. Applications can then use the abstract view of the network provided by Onix to enact certain policies, such as traffic engineering, or network management in the guise of Ethane, or perhaps creating virtual networks for separate tenants.

The important thing is that Onix handles concerns of fault-tolerance, consistency, distribution, and scalability for the applications, so that the higher layers can focus solely on the control logic without having to build out all the lower level infrastructure to enforce it.

### Do you think the solution is a good one? Explain.

Yes, this idea just makes sense - I can't think of a more natural way to do it. It would also be cool to think about if switches could be programmed by the control plane applications running on top of Onix - what kinds of policies would this enable?

### Any other comments/thoughts?

One thing the authors don't talk about is if Onix could autoscale, or methods for reacting to stress on the network. It would also be nice to have a sane fallback in case Onix goes down - perhaps the network could fallback on default policies. 

### Did you enjoy reading this paper?

Yes!