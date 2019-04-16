# Synchrony Assumptions Overview

* partial synchrony (e.g. PBFT) -- guarantees liveness only when the network satisfies timing assumptions
    * PBFT would achieve zero throughput against an adversarial asynchronous scheduler 
    * look at `consensus in the presence of partial synchrony` for other definition and find more

Distributed systems can be roughly divided into three categories according to their timing assumption: 
1. **asynchronous**: no timing assumptions on message processing or transmission delays; inherently more robust to timing and deanial-of-service (DoS) attacks
2. **synchronous**: known bound on message process- ing delays and transmission delays
3. **partially synchronous**: messages are guaranteed to be delivered within a time bound, but the bound may be unknown to participants of the system

## Why Asynchronous Consensus Algorithms

* ensures liveness without timing assumptions
* inherently more robust against timing and denial-of-service (DoS) attacks that can be mounted over an unprotected network such as the Internet


