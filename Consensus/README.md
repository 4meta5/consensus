# Consensus Algorithm Implementations with Futures
> annotate each one and discuss code patterns that all of them have

* [Accompanying Writing and In-Progress Explainers](./xplanerz/)

**Rust Implementations of Popular Consensus Algorithms**
* [PBFT]()
* [Paxos](https://github.com/nwtnni/paxos)
* [Honeybadger](https://github.com/rphmeier/honeybadger)
* [Tendermint](https://github.com/paritytech/parity-ethereum/pull/9980/files)
    * switching to Rhododendron for better performance
    * identify the difference between *Tendermint and Rhododendron*?
* [Rhododendron](https://github.com/paritytech/rhododendron)
* [Aura]()
* [Babe]()
* [Grandpa]()

## TODO

* finish BEAT Paper and organize notes
* read and understand python code of Phragmen
* port notes from `AmarRSingh/Notes/Blockchain/Consensus` to this repo

## Misc Notes

* Chain-based BFT protocols, such as Aliph-Chain BChain, and Shuttle favor throughput over latency.
* Q/U achieves fault-scalability that tolerates increasing number of faults without significantly sacrificing performance.
* Zyzzayva and Aliph are *hybrid* protocols that have high performance in failure-free cases.

## Async Helpers
* *[`jonhoo/faktory-rs`](https://github.com/jonhoo/faktory-rs)* -- Rust bindings for Faktory clients and workers (may be useful for coding `async helpers`)
    * tomusdr's pull request for off-chain workers
    * Joe's project as a reference for optimal interaction

* **Truebit** design is probably good for off-chain, verifiable computation

## Q

* [Distributed Consensus (the Morning paper)](https://blog.acolyer.org/2019/05/07/distributed-consensus-revised-part-i/)