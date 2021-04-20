### What problem does this paper address?

The authors want to unite serverless computing with network functions i.e. right now no cloud provider offers the service of spinning up custom NFs and billing and management for NFs. A custom platform is needed to address the problms in running NFs in the cloud, one which can scale, manage state, provide accurate resource accounting, all while providing a "serverless" abstraction to NF developers.

### Do you believe the problem is/was important? Explain.

If cloud providers start offering NFaaS, this could lead to more widespread adoption of NFV on the internet, so I see creating a platform for easy development and use of NFs as an important step in breaking the reliance on network hardware vendors. This problem is also important from the wider serverless perspective, because it offers insights for how to manage general stateful streaming workloads in the serverless paradigm.

### What is the authors' main insight?

A few key insights enable SNF: the authors decide to account for flows at a flowlet granularity (batches of volume and time sliced traffic) for easier work assignment and manage ephemeral state for flows (to enable stateful computation). 

The SNF architecture consists of a controller which has three main modules which are responsible for dividing the incoming traffic into flowlet granularity, greedily binpacking flowlets into compute units, and determing when to migrate state respectively. An NF runtime on each compute unit manages the actual state migration when required following a similar policy as is employed in live migration of VMs coupled with logical clocks on packets to prevent state staleness.

### Strengths/Weaknesses?

The abstraction provided by SNF is very general which allows developers to write custom NF code pretty easily.

### Any other comments/thoughts?



### Did you enjoy reading this paper?

No.