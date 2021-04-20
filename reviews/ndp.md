### What problem does this paper address?

Low latency and high throughput is difficult to achieve in datacenter contexts with current transport protocols such as TCP. A new protocol is needed to handle short and long flows in the datacenter as well as address datacenter specific pathologies.

### What is the authors' main insight?

The authors present NDP, a new transport protocol which operates on a number of principles. First, switch buffers are small, which reduces latency due to queuing. The protocol starts with senders transmitting a full window of packets to a reciever, all of which can be used to initiate the connection, since traffic is multi-path routed on a per packet basis. The reciever then maintains a pull queue for each sender, and sends pull requests to senders from this queue such that senders will send to the reciever at line rate. This allows the reciever to clock to rate of transmission. Furthermore, during congestion events, switches trim packet payloads and only send packet headers to recievers. This allows recievers to get a full view of traffic and prioritze which traffic they want to recieve next. All these design properties are useful in the datacenter high fanout, low latency, incast heavy context.

### Strengths/Weaknesses?

NDP reimagines the datacenter transport protocol from the ground up by presenting a design which integrates the needs of datacenter applications and takes advantage of datacenter topologies together. This allows a design which is able to provide the low latency and high throughput guarantees that a datacenter network should be able to provide given the hardware and its toplogy.

A major weakness here is deployability, and it's not clear how NDP would coexist with other protocols in the datacenter.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes.