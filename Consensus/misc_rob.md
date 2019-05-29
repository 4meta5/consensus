# (Sovereign Substrate => Parachain) via Cumulus
*[Consensus in Substrate](https://www.youtube.com/watch?v=QE8svRKVYOU)* by Rob at Sub0

* [Introduction to Polkadot Consensus](#intro)
* [Cumulus](#cumulus)
* [Swappable Consensus](#swappable)

## Introduction to Polkadot Consensus <a name = "intro"></a>

Consensus engines are watching for signals from block headers so that light clients can follow as well. We use digest items for this; certain digests called `consensus` for i.e. changing validator sets or changing consensus engines.

Consensus lives outside of WASM. Consensus involves gossip protocols, message passing, and other complex networking that isn't easily encoded in WASM; still need to give the runtime the ability to negotiate between different consensus engines.

**GRANDPA** is a finality gadget, associated with some block production system (necessary invariant for block production algorithm: fork choice rule must follow the most recently finalized block). It is a round-based two-phase-commit -- 2 rounds of voting to get a 2/3 supermajority.

PBFT does two rounds of voting to get a 2/3 supermajority sign off on some block hash. 

Instead of voting on a single value (like in Tendermint for example), validators vote on chains in GRANDPA. The goal behind GRANDPA is to determine **common ancestry** and deterministically finalize that common ancestry to achieve accountable safety and economic finality. Consensus engine is safe as long as <1/3 of participants do not misbehave, and, if it is unsafe, then we slash the >1/3 of participants and this provides accountability and economic finality.

BABE - blind assignment for blockchain selection (heavily inspired by Ouroboros Praos)

Ouroboros Praos: splits time up into slots; earliest version was `Aura`

Idea behind these block selection algorithms is splitting up time into discrete segments and then assigning leaders for each slot and designating block authorship accordingly.

**Ouroboros Praos** gives everyone a random key, or a private key that can be used to create deterministic signatures called VRFs; so you don't know who is the slot leader until they prove it to you -- so you don't know who will author the next block until they prove it to you (which increases security).

BABE strives to solve **clock drift**. When you split up time into discrete slots...in a decentralized network, different people have different views of the time. This can lead to different types of attacks involved in time differences ([PBFT vs Proof of Authority: Applying the CAP Theorem to Permissioned Blockchain](https://eprints.soton.ac.uk/415083/2/itasec18_main.pdf)).

BABE uses **relative time**; you know how long the slots are supposed to be but you don't know when they start or end at the beginning. You watch at what time you're importing new blocks; once you get all the incoming pieces of information, you can make an (over)estimate of where the rest of the network thinks the slots are...
* makes it more resilient to **NTP server attacks** or geographic distribution of nodes

*Aura is the only stable consensus engine in 1.0*

**Every consensus engine specifies**:
1. `ImportQueue`: does parallel verification where it doesn't matter if the blocks are out of order (first stage verification so checking valid signatures from authorities)...doesn't do block execution yet (because block execution must be in-order)
2. `BlockImport` worker; most consensus engines don't need to worry about that...the client wraps a database and it handles most import which is an implementation of this trait.
* most of the time you can just use `client`
* for Grandpa you need to track the properties of blocks coming in and you need to do this in order; so you need to wrap the client internally and, on either side of that call, you need to do your own book-keeping
3. We need to isolate the `Background Workers`: all the pieces that are interacting with the network or authoring blocks or casting votes are there own asynchronous tasks...those don't get told what to do by anything else

Background Worker and Import Queue talking to networking. The `ImportQueue` is getting blocks from networking; the `Background Worker` might be receiving messages or sending messages but it doesn't have to -- `aura` doesn't require any special networking here 
* more complicated engines like Grandpa or Tendermint require more interaction with networking for gossip-related consensus

## Cumulus <a name = "cumulus"></a>
*set of libraries designed to bridge the gap between Substrate and Polkadot -- change a Substrate runtime into a Polkadot validation function*

* authorship by running a collator node
* finality by following the relay chain and checking when that is finalized

*a node using `Cumulus` embeds a Polkadot Light Client*

**Relay Chain**: coordinates consensus and transaction delivery between chains
**Parachains**: constituent blockchains which gather and process transactions
**Bridges**: link to blockchains with their own consensus

Validation functions are a piece of code registered on the relay chain. Collators want to find an input to the validation functions that evaluate to true. Validators vote for things that make the validation function true.
* validation functions are deterministic and self-contained

```rust
// signature of validation function
fn validate(
    last_header: &[u8],
    polkadot_info: PolkadotStatus,
    block_data: &[u8],
) -> Result<Vec<u8>>
```

**Collator Nodes**: compute block data for a parachain (make validation function for the parachain return successfully); depends on the parachain logic -- collators have to have chain-specific logic...

**Cumulus-collator** is a special block-authorship pipeline for Substrate that creats blocks along with their State Trie Block Data.
* rips out a subset of the state trie necessary to process all the transactions as well as any incoming messages and the state required to execute those incoming messages.

**CUMULUS COLLATION PIPELINE**
* **INPUT**: (1) compute incoming messages and other relay chain -- forms a `PolkadotInherent` from them (2) Select a set of other transactions and inherents to include in the block
* **PROCESSING**: construct a block from the `PolkadotInherent` and other transactions -- combine this with all read trie nodes
* **OUTPUT**: combine the transactions, state trie proof, and messages inot the PoVBlock (Proof of Validation Block)

> trust wormholes (in the `PolkadotInherent`)?

**How are parachains different from sovereign-chain Substrate?** They have to follow the relay chain -- they are finalized via Grandpa consensus because that's how the relay chain is finalized...this means that we can always find the latest finalized header for a given parachain
* for full nodes, we have to download all the blocks of the parachain to the head of the chain (we figure out the head from the relay chain state) => one approach is to download all the blocks backwards from the head all the way to the beginning; better approach is download forwards -- we use `Log2` ancestors

**Log2 Ancestors**: parachain state keeps a bunch of header hashes -- header hashes are the hash of the latest ancestor whose number is a power of 2. When you import a block, you can easily update the relevant rows in the table by squashing the rows according to this rule...from a finalized block, you can therefore take larger hops backwards -- used in parallel with synchronization forward allows you to find which block hash is canonical at what number...

## Swappable Consensus <a name = "swappable"></a>

We write a wrapper for each of the (3) components around some consensus engine -- it will poll the correct asynchronous background worker to completion
* ie Grandpa would poll the Grandpa finality voter

**Kinds of Consensus Engines**
* finality providers
* blockchain extenders

*only one at a time; some consensus engines fulfill both*

The `Consensus Overseer` is a consensus engine that allows switching between a number of registered consensus engines. Each of them has its own ID.
* you can add your own and register them in the `overseer`

Changing engines is done by issuing a digest in the header -- this allows ligjht clients to follow along as well.

*standard set of rules for migrating fork choice rules -- this is difficult to reason about...(seems impossible to "solve")*