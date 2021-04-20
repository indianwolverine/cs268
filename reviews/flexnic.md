### What problem does this paper address?

While network I/O speeds continue to grow, servers are struggling to keep up with the traffic even with kernel bypass technologies. The authors argue that NICs should be used to offload work from the host since only NICs are both close to the host, and thus can be made aware of application semantics, but are also able to handle traffic at line rate.

### Do you believe the problem is/was important? Explain.



### What is the authors' main insight?



### Strengths/Weaknesses?

The main strength of this paper is in identifying a problem in network traffic handling by observing hardware trends and applying a previously explored idea (RMT) to combat it. It's a quite elegant extension of the programmable switch idea. In addition to this, the authors provide many case studies of common applications which could gain better performance from FlexNIC which is useful in demonstrating the power of the abstraction.

The RMT model for the NIC is nice, since it has been shown to be able to process packets at line rate, but is this the correct abstraction for NICs to expose to applications? Can we offer more complex capabilities to applications without sacrificing performance?

### Any other comments/thoughts?



### Did you enjoy reading this paper?

