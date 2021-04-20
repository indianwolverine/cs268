### What problem does this paper address?

In order to meet the latency requirements of datacenter applications (microsecond-scale tail latencies), servers are structured with CPUs spin polling NICs instead of interrupt based processing. This spin polling wastes CPU cycles and leads to overall lower CPU efficiency.   

### Do you believe the problem is/was important? Explain.

Yes, I think there is a lot of room for hardware and OS level systems evolution in response to emerging datacenter workloads. For example, we may see a lot more specialized hardware for packet processing within commodity servers and setups like these will require a reimagining of how we structure the lowest level of systems software. In this context, I think not only the problem, but the approach taken to solve the problem are both important.

### What is the authors' main insight?

The authors introduce Shenango, a kernel bypass stack which uses a dedicated core to process network queues and schedule work for the remaining cores. The monitoring core, IOKernel, runs a scheduling algorithm every 5us, checking to see if the runqueues and packet queues contain items seen on the previous run. If so, IOKernel attempts to allocate more cores to the congested kernel threads in a locality and latency aware manner. 

### Strengths/Weaknesses?

A general purpose CPU must be dedicated to the IOKernel, but the constrained set of functions the IOKernel performs suggest that a less powerful or less general hardware may suffice.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes!