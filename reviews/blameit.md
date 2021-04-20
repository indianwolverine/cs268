### What problem does this paper address?

The authors want to understand the root causes of high latency events in the cloud to client path traversing the public internet. In the process, they also want to develop a tool to automatically detect and diagnose such outages in order to aid network operators in finding the root cause of such events.

### Do you believe the problem is/was important? Explain.

This problem is definitely important for Microsoft from an operational perspective, but the work done to understand causes of latency in the public internet is also important in the same vein as the packet dynamics work by Paxson - we need to know these things to build an accurate model of the internet now.

### What is the authors' main insight?

There a few key observations which drive the authors' solution: high latencies are experienced pretty much everywhere and at many different times, but the distribution of latency events is long tailed with only a few being long enough to merit investigation, and the number of users affected along with the duration of the event is the key indicator for impact of an event.

The design of blameit is twofold - a passive service maintains an accounting of expected RTT values for all network quartets (client IP /24 prefix, cloud location, mobile (or) non-mobile device, 5 minute time bucket), and triggers a blame assignment when the RTT values exceed a badness threshold. This allows blame for latency to be assigned when a cloud location sees more than 80% of bad latency quartets in a timespan. A similar accounting is kept per BGP path, in case the fault lies in some middle AS. If this is the case, blameit goes into an active investigation mode where it issues traceroutes against these BGP paths in question in order to identify where latency spikes are occuring compared to background levels. It uses a budget based on prioritizing events affecting more clients for a longer time in order to minimize the impact of the traceroutes and be able to direct resources usefully.

### Do you think the solution is a good one? Explain.

Yes, this is a really cool paper. Since blameit is operating at internet scale, there are a number of tradeoffs the solution has to make in order to remain an effective tool, such as the idea of investigating issues at a coarse granularity before diving in, and prioritizing only the most urgent issues. It's also very nice that blameit works in real time rather than processing old data, since we've seen before that internet characteristics are constantly evolving and results from yesterday likely won't be as useful today. I wonder however how much of a load blameit generates for network operators - Often monitoring and alerting tools are only useful so long as the false positive and false negative rates are kept very low. Along the same lines, it's likely that the tool will require additional tuning as the internet continues to evolve.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

Yes!