# Synchrony Assumptions Overview

* partial synchrony (e.g. PBFT) -- guarantees liveness only when the network satisfies timing assumptions
    * PBFT would achieve zero throughput against an adversarial asynchronous scheduler 
    * look at `consensus in the presence of partial synchrony` for other definition and find more


## Why Asynchronous Consensus Algorithms

* ensures liveness without timing assumptions
* inherently more robust against timing and denial-of-service (DoS) attacks that can be mounted over an unprotected network such as the Internet


