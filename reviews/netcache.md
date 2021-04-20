### Are you convinced that key-value stores should use an architecture like NetCache? Explain.

If high performance is the main concern and it can't in fact be acheived by other means (such as replicating hot keys) and workloads are well-defined to be heavily read skewed, why not? If performance guarantees are the main issue however, using NetCache may in fact introduce a degree of variability in response time which is not acceptable. On top of that, the caching functions of the switch may interfere with the normal switching fucntions of the switch.

### Beyond NetCache, what do you think is the most compelling application/use of RMT switches?

RMT switches can help realize some of the benefits proposed by active networking, at least in the data center context or a similarly controlled environment. We could gain better introspection on what packets are doing (monitoring), be able to figure out where in the network things are going wrong (debugging), enact custom policies for congestion control, and be able to react to network events which happen at timescales too short for the control plane to react to.

### What are the conditions under which you think it is a good idea to use programmable switches and when is it not?

I think as long as the additional overhead imposed by work other than switching doesn't impact the forwarding of packets and this work also imparts some performance benefit to the system, it's a good idea to use programmable switches. Usually we run into trouble when our systems become too complex to understand and reason about, but I think programmable switches can actually make the network easier to reason about if used properly.

### What (if any) do you see as the relationship between programmable switches such as RMT and active networking?

I think that RMT can be used for active networking, but it's not a one to one mapping. RMT certainly makes the active networking dream much more realizable, and I think many of the upsides to RMT are embodied in what people saw as the benefits of active networking.

### Any other comments/thoughts?

I wonder as networks evolve if it will always be necessary for packet processing to always occur at such high speeds. Is performance really an inherent requirement in networking hardware or is it something we've come to expect? I think based on current expectations, this is prudent research which allows the debate to shift from "is the data plane programmable at high speeds" to "is match-action the correct abstraction for programming the data plane and what can we do with it".

### Did you enjoy reading this paper?

RMT: Yes, one of the best papers so far - hardware architecture is always awesome to learn about.
NetCache: Yes. Cool idea - what's the industry impact?