# Notes From Rob's Talks

Consensus engines are watching for signals from block headers so that light clients can follow as well. We use digest items for this; certain digests called `consensus` for i.e. changing validator sets or changing consensus engines.

Consensus lives outside of WASM. Consensus involves gossip protocols, message passing, and other complex networking that isn't easily encoded in WASM.

**GRANDPA** is a finality gadget, associated with some block selection system. It is a round-based two-phase-commit finality

PBFT does two rounds of voting to get a 2/3 supermajority sign off on some block hash. 

Instead of voting on a single value (like in Tendermint for example), validators vote on chains in GRANDPA. The goal behind GRANDPA is to determine common ancestry and deterministically finalize that common ancestry to achieve accountable safety and economic finality.

BABE - blind assignment for blockchain selection (heavily inspired by Ouroboros Praos)

Ouroboros Praos: splits time up into slots; earliest version was `Aura`

Idea behind these block selection algorithms is splitting up time into distinct segments and then assigning leaders for each slot and then designating block authorship accordingly.

Ouroboros Praos gives everyone a random key, or a private key that can be used to create deterministic signatures called VRFs; so you don't know who is the slot leader until they prove it to you -- so you don't know who will author the next block until they prove it to you (which increases security).

BABE strives to solve **clock drift**. When you split up time into discrete slots...in a decentralized network, different people have different views of the time. This can lead to different types of attacks involved in time differences ([Applying the CAP Theorem to Permission Blockchain]()).

BABE uses **relative time**; you know how long the slots are supposed to be but you don't know when they start or end at the beginning. You watch at what time you're importing new blocks.
* makes it more resilient to NTP server attacks or geographic distribution of nodes

`ImportQueue`: does parallel verification where it doesn't matter if the blocks are out of order (first stage verification so checking valid signatures from authorities)...doesn't do block execution yet

`BlockImport` worker; most consensus engines don't need to worry about that...the client wraps a database and it handles most of import which is an implementation of this trait.

**Background Worker**: all the pieces that are interacting with the network or authoring blocks or casting votes are there own asynchronous tasks...

> **consensus** directory is the place to look

## Cumulus
> bridges the gap between Substrate and Polkadot

Validation functions are a piece of code registered on the parachain. Collators want to find an input to the validation functions that evaluate to true.

Validation functions are deterministic and self-contained.

**Collator Nodes**: compute block data for a parachainn; depends on the parachain! 

**Cumulus-collator** is a block-authorship pipeline for Substrate.

## References

* [Consensus in Substrate](https://www.youtube.com/watch?v=QE8svRKVYOU) -- May 9, 2019