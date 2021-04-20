### Introduction

TCP/IP developed at DARPA in the 1970's
- packet switched protocols
- widely adopted for commercial use

How have the original objectives of internet architecture led to the current design?

### Fundamental Goal

- develop an architecture to interconnect already existing networks with their own administrative boundaries and allow for future, not yet seen networks to use this interconnect as well
- packet switching (instead of circuit switching) design came from applications which used network and existing networks both being packet oriented already
- borrowing from ARPANET, networks interconnected using switches

### Second Level Goals

1. Internet communication must continue despite loss of networks or gateways.
2. The Internet must support multiple types of communications service.
3. The Internet architecture must accommodate a variety of networks.
4. The Internet architecture must permit distributed management of its resources.
5. The Internet architecture must be cost effective.
6. The Internet architecture must permit host attachment with a low level of effort.
7. The resources used in the internet architecture must be accountable.

Noticibly, accountability not a high priority goal since this was developed in a military context. This is of course problematic now and the cause for much research.

### Survivability in the Face of Failure

- architecture of internet had to abstract away any transient network failures for applications
- service should only fail if network is partitioned
- state must be maintained for each connection
- internet chooses to maintain state at end hosts instead of intermediate nodes (fate sharing)

### Types of Service

- different types of service (characterized by speed, latency, reliability, throughput etc.) need to run on architecture
- TCP designed to be general purpose to support services such as remote login and file transfer
- some applications don't work well on TCP, such as audio calls since these don't require reliable transport
- reliable transport is the largest contributor to network delay, bad for calls
- these differing requirements led to transport layer abstraction on top of IP early on

### Varieties of Networks

- internet has successfully supported joining together a plethora of different networks with various underlying characteristics
- best effort delivery of datagrams

### Other Goals

- internet consists of several autonomous systems which have admin control over their own subset of switches and hosts and exchange routing tables with other AS's through BGP protocol
- lack of sufficient tools to manage the distributed resources of the internet; currently routing decisions are constrained by resource usage policies
- possibly not as const efficient as it could be (large packet header for small data exchanges)
- poor accountability for traffic flows as well as misbehaving hosts

### Architecture and Implementation

- no formal specfication of performance characteristics since goal of internet was to permit variability of networks

### Datagrams

- eliminate connection state
- can be composed at higher layers to provide specific service
- very easy to implement in networks, very few assumptions

### TCP

- byte oriented instead of packet oriented; allows coalescing different small data into same packet and also splitting up data across packets


### What are the key strengths/contributions of this paper?

This paper tries to answer the question - How have the original objectives of internet architecture led to the current design? 

According to Clark, the main goals of the internet were to interconnect existing networks by providing a convinient communication abstraction and to be architected in such a way as to allow federation and variability rather than rigidity and performance.

It explains that the origins of a packet switching based network design are rooted in the need for survivability of the network under failure scenarios (given that ARPANET was originally a military project) as well as most networks being interconnected already using packet switching protocols. Moreover, the use of switches to forward packets comes directly from ARPANET as well.

Originally, the TCP and IP layers were much more tightly coupled in the architecture, but Clark explains the need to create separate layers arising from several applications not working well with the guarantees of reliability and in order packet delivery which TCP provides by default (remote debugging, voice calls etc.). Ideas from the end to end principle are also at play here regarding where to place responsibility for e.g. reliability (end hosts vs. network).

Other goals of the internet were not as well addressed by the architecture, such as concerns of security, cost effectiveness, distributed administration, performance, and accountability. However, given the previously outlined important goals of the internet architecture, Clark considers these design flaws minor.

### What, if any, would you say are the weaknesses of this paper?

While the internet architecture is indeed admirable, it would have been nice if Clark went into more depth into it's flaws with regards to security, accountability, and performance, and perhaps outlined alternative architectural decisions which might mitigate these. Along the same lines, while it is interesting to see why the architecture is the way it is, it would also be interesting to see why it isn't another way. 

### Would you say this is an important paper? Why?

It's important to study the motivations behind design decisions rather than taking designs as standalone doctrines without any justification. Given these motivations, it becomes easier to reason about alternative designs when assumptions in the environment change. This paper is important as it shows that the internet was not architected in a vacuum, and will need to evolve to meet the demands of the current environment. 

### What, if anything, did you find surprising about this paper?

It's surprising that the internet exists at all! It seems that most of the questions we're asking nowadays are concerned with squeezing every last bit of performance out of machines and networks, which the early internet designers certainly could have done if they came up with a more rigid design which required certain strict semantics from networks it connected. But instead, the internet is, very surprisingly, architected with the goal of supporting as much variation as possible. Instead of building on top of existing networks, it seems just a probable that the designers could have built an entirely new network, without the debt of supporting existing networks.

### Any other comments/thoughts? (This is a good place to note topics that you'd like to see discussed in class)

Has circuit switching been implemented at any scale, for example? If not switches, then what other kinds of hardware are possible? Why not a whole system built on the assumption of using only commodity hardware? After all, we give up a lot of control and privacy as users to big telcos by using their backbone networks and even anonymity technologies such as Tor fail when adversaries control a majority of hosts.

### Did you enjoy reading this paper?

Yes!