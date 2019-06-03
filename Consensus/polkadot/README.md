# Polkadot Consensus
*[substrate/core/consensus](https://github.com/paritytech/substrate/blob/master/core/consensus/), [polkadot](https://github.com/paritytech/polkadot)*

Consensus in Polkadot/Substrate is organized in two specific algorithms:
1. Block Extension Algoprithms::{aura, babe}
2. Finality Gadgets::{GRANDPA}

## Block Extension Algorithms

### Aura

A list of authorities `A` are expected to roughly agree on the current time. Time is divided up into discrete slots of `t` seconds each. For each slot `s`, the author of that slot is `A[s % |A|]`.

The author is allowed to issue one block but not more during that slot, and it will be built upon the longest valid chain that has been seen.

Blocks from future steps will be either deferred or rejected depending on how far in the future they are.

**What is clock drift and why is this bad?** NTP server attacks relevant?

### BABE
*inspired by [Ouroboros Praos](https://eprint.iacr.org/2017/573.pdf)*

BABE (Blind Assignment for Blockchain Extension) consensus in Substrate

**how does BABE patch the clock drift attack vector?**

## Finality Gadgets

* [GRANDPA](https://wiki.polkadot.network/en/latest/polkadot/learn/consensus/#grandpa-finality-gadget)

*also see [ancillary/finality](../ancillary/finality.md)