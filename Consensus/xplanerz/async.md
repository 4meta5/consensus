# Synchrony Assumptions Overview

* partial synchrony (e.g. PBFT) -- guarantees liveness only when the network satisfies timing assumptions
    * PBFT would achieve zero throughput against an adversarial asynchronous scheduler 
    * look at `consensus in the presence of partial synchrony` for other definition and find more

Timing assumptions. Distributed systems can be roughly divided into three categories according to their timing assumption: asyn- chronous, synchronous, or partially synchronous. An asynchronous system makes no timing assumptions on message processing or transmission delays. If there is a known bound on message process- ing delays and transmission delays, then the corresponding system is synchronous. The partial synchrony model [37] lies in-between: messages are guaranteed to be delivered within a time bound, but the bound may be unknown to participants of the system.
In protocols for asynchronous systems, neither safety nor live- ness can rely on timing assumptions. In contrast, a protocol built for a synchronous or partially synchronous system risks having its safety or liveness properties violated if the synchrony assumption on which it depends is violated. For this reason, protocols built for asynchronous systems are inherently more robust to timing and denial-of-service (DoS) attacks [70, 94].


## Why Asynchronous Consensus Algorithms

* ensures liveness without timing assumptions
* inherently more robust against timing and denial-of-service (DoS) attacks that can be mounted over an unprotected network such as the Internet


