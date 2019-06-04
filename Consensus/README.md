# Consensus

*Base layer consensus protocols that take inspiration or closely resemble PBFT*
* [BEAT: Asynchronous BFT Made Practical](./BEAT.md)
* [HoneyBadgerBFT](./HoneyBadgerBFT.md)
* Ouroboros

**Related Research**
* [Layer 2 Scaling Mechanisms](./L2) encompasses all off-chain message passing that uses the base chain for dispute resolution (including [Lightning](./L2/lightning.md), [State Channels](./L2/statechannel.md), [Plasma](./L2/plasma.md), and [Zero Knowledge Rollups](./L2/rollups.md))
* [Ancillary Mechanisms](./ancillary) includes [fee](./ancillary/fee.md) structures, [finality mechanisms](./ancillary/finality.md), and [uncle blocks](./ancillary/uncle.md)
* [Directed Acyclic Graphs (DAG) protocols](./DAG) includes CasperCBC, SPECTRE, Casanova

## Pure Rust Consensus Algorithms
* [PBFT](https://github.com/losfair/pbft-rs)
* [Paxos](https://github.com/nwtnni/paxos)
* [Honeybadger](https://github.com/rphmeier/honeybadger)
* [Tendermint](https://github.com/paritytech/parity-ethereum/pull/9980/files)
* [Rhododendron](https://github.com/paritytech/rhododendron)
* [Aura](https://github.com/paritytech/substrate/tree/master/core/consensus/aura)
* [Babe](https://github.com/paritytech/substrate/tree/master/core/consensus/babe)
* [Grandpa](https://github.com/paritytech/finality-grandpa)

## Misc Notes

* Chain-based BFT protocols, such as Aliph-Chain BChain, and Shuttle favor throughput over latency.
* Q/U achieves fault-scalability that tolerates increasing number of faults without significantly sacrificing performance.
* Zyzzayva and Aliph are *hybrid* protocols that have high performance in failure-free cases.

<!--## Async Helpers
* *[`jonhoo/faktory-rs`](https://github.com/jonhoo/faktory-rs)* -- Rust bindings for Faktory clients and workers (may be useful for coding `async helpers`)
* tomusdr's pull request for off-chain workers
* Joe's project as a reference for optimal interaction -->

* [UniqueChain: A Fast, Provably Secure Proof-of-Stake Based Blockchain Protocol in the Open Setting](https://eprint.iacr.org/2019/456)
* [Distributed Consensus (the Morning paper)](https://blog.acolyer.org/2019/05/07/distributed-consensus-revised-part-i/)
* *[My ETH 2.0 Notes](https://github.com/4meta5/notes/blob/master/Blockchain/Ethereum/Serenity.md)*
