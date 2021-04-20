### What problem does this paper address?

There exist kernel bypass libraries for packet processing, but these don't provide a high level abstraction to applications. On the other end of the spectrum we have libraries which work with the kernel to increase TCP performance, but these are inherently limited by the context switching overhead of the kernel. Is it possible to develop a stack on top of packet processing libraries which provides performance on the order of say DPDK and exposes the high level TCP inteface to applications.

### Do you believe the problem is/was important? Explain.



### What is the authors' main insight?

The authors run an mTCP thread per application which is responsible for sending and recieving packets and batching work for the application. This approach, coupled with kernel bypass and a host of other optimizations, allows mTCP to be very performant.

### Strengths/Weaknesses?

The interface provided to the application is essentially unchanged given that the application was architected to run multithread TCP based networking code in the first place, but there is a massive performance benefit to the application - this is a big win for mTCP. Even if it does nothing else, it is immediately useful.

mTCP is highly customized to providing a TCP interface to applications and is internally constructed to take advantage of the idiosyncracies of the protocol. I wonder if the techniques used in the paper would generalize to other protocols, and if it might have been more interesting to build a more general layer on top of kernel bypass packet processing libraries on which mTCP could then have been built as an example, but which allowed easy extensibility and programmability for implementing other transport level protocols.

### Any other comments/thoughts?

I'm not convinced that this problem was really that important from a research perspective - it's cool as a product, but what does it do that isn't pretty common in systems implementations anyway?

### Did you enjoy reading this paper?

Yes.