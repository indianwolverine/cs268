### What problem does this paper address?

The authors seek to build a framework which allows general offloading of distributed applications to SmartNICs.

### Do you believe the problem is/was important? Explain.



### What is the authors' main insight?

The authors develop the iPipe framework which manages actor based computation on NIC cores and host cores and migrates them as needed to ensure both efficient packet processing and SmartNIC resource usage.

### Strengths/Weaknesses?

As general purpose CPU speeds are no longer increasing rapidly, it seems appropriate to attempt to find other ways to speed up computation. Taking advantage of resources which are present on SmartNICs seems like a good approach to begin with. Also, using the actor model to dynamically migrate computation from the NIC to the host is a nice abstraction resembling MPI. 

Along the same lines, the actor model seems restrictive as well. A lot of computation in datacenters is task based and mapping this onto the actor based interface iPipe exposes may be difficult and not worth the effort.

### Any other comments/thoughts?

As we get faster and faster network hardware and CPU speeds no longer increase as dramatically as they used to, we'll have to find other ways of speeding up computation - using smartNICs may be one way to tackle that problem, but adoption will depend on the development of general compute stacks on top of accelerator hardware. 

### Did you enjoy reading this paper?

Kind of. It doesn't seem like this framework will see much adoption, but I think it is still important to explore this area as it evolves and presents new hardware to build abstractions for.