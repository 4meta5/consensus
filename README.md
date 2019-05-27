# Blockchain Consensus Research

*This repo holds my personal notes on modern blockchain consensus mechanisms.* It is organized hierarchically, split between `Consensus` and `Cryptography`. Most reference code is in Rust.

* [`Consensus`](./Consensus/)
* [`Cryptography`](./RealCrypto/)

## Consensus

*Base layer consensus protocols that take inspiration or closely resemble PBFT*
* [BEAT: Asynchronous BFT Made Practical](./Consensus/BEAT.md)
* [HoneyBadgerBFT](./Consensus/HoneyBadgerBFT.md)
* [Ouroboros](./Consensus/Ouroboros.md)

**Related Research**
* [Layer 2 Scaling Mechanisms](./Consensus/L2) encompasses all off-chain message passing that uses the base chain for dispute resolution (including [Lightning](./Consensus/L2/lightning.md), [State Channels](./Consensus/L2/statechannel.md), [Plasma](./Consensus/L2/plasma.md), and [Zero Knowledge Rollups](.Consensus/L2/rollups.md))
* [Ancillary Mechanisms](./Consensus/ancillary) includes [fee](./Consensus/ancillary/fee.md) structures, [finality mechanisms](./Consensus/ancillary/finality.md), and [nPoS](./Consensus/ancillary/npos.md)
* [Directed Acyclic Graphs (DAG) protocols](./Consensus/DAG) includes CasperCBC, SPECTRE, Casanova

## Cryptography

*WIP*
