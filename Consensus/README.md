# Consensus Algorithm Implementations with Futures
> annotate each one and discuss code patterns that all of them have

* [Paxos](https://github.com/nwtnni/paxos)

* [Honeybadger BFT](https://github.com/rphmeier/honeybadger)

* [Rhododendron](https://github.com/paritytech/rhododendron)

* [Tendermint](https://github.com/paritytech/parity-ethereum/pull/9980/files)
    * switching to Rhododendron for better performance
    * ask **June** -- what is the difference between *Tendermint and Rhododendron*?

## Async Helpers
* *[`jonhoo/faktory-rs`](https://github.com/jonhoo/faktory-rs)* -- Rust bindings for Faktory clients and workers (may be useful for coding `async helpers`)
    * tomusdr's pull request for off-chain clients

## Accompanying Writing

* Byzantine Generals Problem explained in Modern Terms

* Sybil mechanism vs permissionless consensus
    * barriers to entry and static validator sets in PoS
    * power law as an economic law
        * leads to centralization for Proof of Work and Proof of Stake
        * which might be better? Capital is pretty centralized...so is Bitcoin

* Finality as a Price Threshold
    * use Alexis's post

* CAP Theorem and Quick Block Production
    * aura as an example

* Sychrony Assumptions for Consensus Algorithms
    * asynchrony