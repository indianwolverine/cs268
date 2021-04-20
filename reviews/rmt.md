### What problem does this paper address?

SDN promises network programmability and innovation by decoupling the control and data planes. OpenFlow defines a match-action interface for data plane programmability, but prior to this paper, this vision was limited to general purpose hardware which cannot match the performance requirements of switching hardware. This paper seeks to develop a proof of concept data plane chip which can be programmed AND provide the performance required of such hardware at little additional cost.

### Do you believe the problem is/was important? Explain.

In the immediate term, this is probably important, but I wonder as networks evolve if it will always be necessary for packet processing to always occur at such high speeds. Is performance really an inherent requirement in networking hardware or is it something we've come to expect? I think based on current expectations, this is prudent research which allows the debate to shift from "is the data plane programmable at high speeds" to "is match-action the correct abstraction for programming the data plane and what can we do with it".

### What is the authors' main insight?

The authors introduce RMT, a new programmable chip architecture for switches. The idea here is that the RMT chip should provide the reprogrammable match-action hardware necessary for the SDN control plane to reconfigure it and realize new innovative network protocols and functions. 

The chip consists of a front-end parser which extracts packet headers and organizes these into a vector. This vector is then driven through a series of match stages, where specific actions can take place on the vector if matches happen. For example, a match stage might match an IP packet and a corresponding action stage might then decrement the TTL in the header. There are 32 physical stages on the chip, each with their own SRAM (exact matches) and TCAM (ternary matches) as well as action elements (think ALU with control logic). These stages can be organized into logical stages for packet processing restricted only by the resources on the chip.

Every part of the chip can be configured, from the parser, to the match stages, and the action stages, allowing for the programmability desired. 

### Do you think the solution is a good one? Explain.

Yes, for the match-action interface this is a good solution since it shows that this subset of programmability can in fact be realized at high speeds. One of the problems mentioned in the paper was the conflation of memory resources with other chip resources i.e. if a stage wants more resources of any kind it has to reserve more memory regardless, but I believe this is addressed in later work and the Barefoor Tofino switch. Other than that, this is a really cool solution to an important problem.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes, one of the best papers so far - hardware architecture is always awesome to learn about.