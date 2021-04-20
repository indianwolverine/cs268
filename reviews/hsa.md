### What problem does this paper address?

This paper addresses a class of problems related to network reachability, forwarding loops, traffic isolation/leakage.

### What is the authors' main insight?

The authors develop a header space algebra. Essentially, all packet headers are treated as a point in an L dimensional space of {0, 1}. Then, common operations such as unions and intersections are defined on this space as well as transfer functions describing network topology and how network boxes function on headers. Finally, this machinery is used to analyze the problems outlined on real networks.

### Strengths/Weaknesses?

Because the solution doesn't deal with header specifics, the framework is very general and can likely be applied to a broad class of networks pretty easily. 

The scope is limited to the data plane, and doesn't really address another large class of errors in the control plane.

### Any other comments/thoughts?

N/A

### Did you enjoy reading this paper?

Yes!