# BEAT
> notes on `BEAT: Asynchronous BFT Made Practical` by Duan, Reiter, Zhang

* [Protocol Overview](#overview)
* [Related Work](#related)
* [System and Threat Model](#threat)

Recommended to differentiate between **append-only ledgers** and **on-chain smart contracts**
1. **BFT Storage**: append-only, linearizable storage systems; leverages erasure encoding to reduce overall storage
2. **General State Machine Replication (SMR)**: requires each replica to maintain a copy of all service state to support contracts that operate on that state

Examples:
* (1) => food safety, exchange of healthcare data
* (2) => AI blockchain, financial payments

> **Motivating question behind BEAT**: can we have asynchronous BFT storage that significantly outperforms asynchronous general SMR?

## BEAT Protocols Overview <a name = "overview"></a>

* **Beat0**: secure, efficient threshold encryption, direct instantiation of threshold coin flipping (in lieu of using threshold signatures), and flexible, efficient erasure-coding support
* **Beat1**: replaced erasure-coded broadcast (AVID broadcast) with replication-based broadcast (Bracha's broadcast). This reduces latency when there is low contention and small batch size.
* **Beat2**: reduces latency by moving the encryption part of the old threshold encryption to the client; achieves this by trading liveness, but it can still be combined with  asynchronous communication networks to achieve full liveness. This variant also achieves causal order.
* **BEAT3**: replaces Byzantine reliable broadcast with bandwidth-efficient asynchronous verifiable information dispersal (AVID-FP) by using fingerprinted cross-checksum (bandwidth consumption is information theoretically optimal)
* **BEAT4**: extends fingerprinted cross-checksums to handle partial read; in the context of pyramid codes, adds an erasure-coded asynchronous verifiable information dispersal protocol with reduced read bandwidth (AVID-FP-Pyramid)

## Related Work <a name = "related"></a>

> **atomic registers** by Lamport; notions of linearizability and wait-freedom by Herlihy and Wing

State machine replication cannot be achieved in asynchronous environments, unless it uses randomization to circumvent this impossibility result (like HoneyBadgerBFT and BEAT).

**Comparison with erasure-coded Byzantine atomic registers**
* Pasis, CT, M-PoWerStore, Loft, and AWE

**Why Pyramid Codes?**
* reducing bandwidth costs 
* Xorbas codes are a close competitor that also reduces bandwidth costs for data and redundant fragments

## System and Threat Model <a name = "threat"></a>