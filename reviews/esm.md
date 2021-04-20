### What problem does this paper address?

According to the authors, IP layer multicast suffers from a number of problems: 
1) Scaling concerns due to maintenence of multicast group state at routers.
2) Lack of support for higher level features such as reliability, congestion control, flow control, and security
3) Requires infra changes and thus slow to deploy

They go on to argue that multicast should be implemented at the end hosts instead to speed up deployment, support the higher level features, and achieve decent performance for most applications requiring multicast support.

### Do you believe the problem is/was important? Explain.

Yes, I think multicast is a very important problem given the classes of applications which would benefit from an efficient implementation. I also think it's a compelling argument that multicast should be implemented at end hosts instead of in the network if possible since there are a number of limitations to the IP implementation and the performance overhead can likely be engineered to be acceptable at with an end system protocol.

### What is the authors' main insight?

The authors present Narada, an end system multicast protocol which tries to address the problems outlined above. Narada creates an overlay mesh connecting all of the nodes in a multicast group. From this mesh, a spanning tree rooted at the source is constructed using distance vector protocols. 

Each node maintains a full list of all other nodes in the mesh and mechanisms are provided for repairing the mesh upon node failure/network partition and improving the mesh through a variety of heuristics involving monitoring and measuring network charactristics such as bandwidth and latency and adding and dropping links once certain criteria are met. The cost function that dictates link addition and removal can be tuned to the needs of the application in question.

### Do you think the solution is a good one? Explain.

One thing this paper does really well is include a thorough evaluation of the implementation of the protocol. While not a highly optimized implementation, its evaluation at least sets the stage for what kinds of metrics might be important in evaluating end system multicast protocols. It doesn't seem like Narada in its current state is good enough for use by real applications simply due to the high convergence time at the beginning for the mesh.

It would have been nice to see what the user experience is like for applications running on different multicast protocols. Probably the convergence time of Narada makes it unusable for many applications, but since the point of multicast is to enable efficient network usage by certain applications, it seems that user experience would be a legitamate dimension to evaluate various solutions on.

### Any other comments/thoughts?

If we could redesign the internet, what would we change about the architecture to make multicast easy? What if multicast were the underlying delivery abstraction that the internet used, with unicast simply being an instance of multicast with only one member in the recieving group?

It would also be interesting to talk about other multicast solutions, such as ones using proxies as points of distribution in the network and using content addressable networks to scale end system multicast.

### Did you enjoy reading this paper?

Yes. I liked that this paper was more honest about the limitations of the solution and I enjoyed the thorough definition of evaluation metrics and various evaluation methods.