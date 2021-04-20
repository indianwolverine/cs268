## Notes

As a thought exercise, how would we implement network architectures we've seen in Click?
Where does this approach fail? Multicore? Why run on Linux, why not a custom stack for the router use case?
Control and data logic in same flows?
What about actions which need to operate on global state?
Is thundering herd a problem (multiple pull elements wake up at the same time in response to queue signal)
io_uring?

### Introduction
- Routers increasingly taking on many more functions than just routing
  - traffic prioritization
  - NAT
  - tunnelling
  - filtering
  - firewalls
- However, router designs are closed, static, and inflexibile
- Need a way to program routers
- Click is a modular software architecture for building routers
  - elements composed into graph
  - packets move from element to element in processing

### Architecture
- Router composed of elements, which are units of processing, in a directed graph
- each element has a class which determines its behavior, ports for packet input and output, and a configuration string for dynamic behavior tuning
- Push and pull connections between elements
  - push - upstream elements hands off packet downstream - usually for input
  - pull - downstream element asks for packets recursively up the graph - usually for output
- push and pull elements connected by queues (think pub/sub system)
- Essentially push elements process a packet, and then call the push function of downstream elements. These downstream elements then get ownership of the packet (packet data is not copied since Click follows CoW semantics), and if it's a queue, it essentially keeps packets around for downstream pull elements. The pull elements, when ready, pull from an upstream element, such as a queue, for processing and usually sending out of some interface.
- There is also flow based router context which allows elements to learn about the entire flow either upstream or downstream, e.g. a queue can notify downstream pull elements once it is nonempty.
- Elements implemented as C++ objects implementing interface
- comes with declarative langauge to specify connections

### An IP Router
- see figure in paper

### Extensions
- packet schedulers implemented as pull elements which enact some policy on multiple input queues
- since abstraction operates on flow of packets, certain things are hard to do
  - control must be implemented in large opaque elements (think routing tables)
- scheduling CPU between elements problematic when multiple devices send/recv simultaneuosly

### Implementation
- implemented as a kernel module (can be run as a user level process using BPF)
- runs as bottom half of a device driver
  - on recv, Linux copies packet to input queue and passes control to Click
  - Click forwards packet to correct FromDevice which pushes until queue
  - when output hardware interrupts, Linux passes control to Click
  - Click invokes the correct ToDevice and pulls, sending directly to output device
- config and stats communication through /proc

### Evaluation
- most overhead of Click is simply architectural (element function calls leading to instruction cache misses)
- probably better to use polling instead of interrupts due to livelock at high recv rates

---

### What problem does this paper address?

- Routers increasingly taking on many more functions than just routing
  - traffic prioritization
  - NAT
  - tunnelling
  - filtering
  - firewalls
- However, router designs are closed, static, and inflexibile
- Need a way to easily program routers

### Do you believe the problem is/was important? Explain.

Yes, I think it's very important to be able to prototype and iterate quickly on ideas for innovation, and Click brings that to the router world. Click also presages NFV and presents a compelling argument for moving more of the complex functions in the network from hardware to software while making hardware as simple as possible.

### What is the authors' main insight?

The authors present Click, a modular software architecture for building routers.
  
- Router composed of elements, which are units of processing, in a directed graph
- each element has a class which determines its behavior, ports for packet input and output, and a configuration string for dynamic behavior tuning
- Push and pull connections between elements
  - push - upstream elements hands off packet downstream - usually for input
  - pull - downstream element asks for packets recursively up the graph - usually for output
- push and pull elements connected by queues (think pub/sub system)
- Essentially push elements process a packet, and then call the push function of downstream elements. These downstream elements then get ownership of the packet (packet data is not copied since Click follows CoW semantics), and if it's a queue, it essentially keeps packets around for downstream pull elements. The pull elements, when ready, pull from an upstream element, such as a queue, for processing and usually sending out of some interface.
- There is also flow based router context which allows elements to learn about the entire flow either upstream or downstream, e.g. a queue can notify downstream pull elements once it is nonempty.

### Do you think the solution is a good one? Explain.

Yes! I think thinking about implementing routers in software using a packet flow abstraction is very intuitive and maps well to how routers are structured anyway.

### Any other comments/thoughts?

The authors argue that doing complex things such as control using the packet flow abstration is difficult, but I would argue that perhaps an extension to the design is needed to handle control, or maybe control should be handled by a different software altogether, leaving Click to handle the data plane.

As a thought exercise, how would we implement network architectures we've seen in previous papers using Click?
Where does this approach fail? What about multicore systems? Why run on Linux, why not a custom stack for the router use case? Is thundering herd a problem (multiple pull elements wake up at the same time in response to queue signal)?
io_uring for better performance on network I/O and eBPF as a sort of Linux built-in Click?

### Did you enjoy reading this paper?

Yes!