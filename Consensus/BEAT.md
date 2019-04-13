# BEAT
> notes on `BEAT: Asynchronous BFT Made Practical` by Duan, Reiter, Zhang

Recommended to differentiate between **append-only ledgers** and **on-chain smart contracts**
1. **BFT Storage**: append-only, linearizable storage systems; leverages erasure encoding to reduce overall storage
2. **General SMR**: requires each replica to maintain a copy of all service state to support contracts that operate on that state

Examples:
* (1) => food safety, exchange of healthcare data
* (2) => AI blockchain, financial payments

> **Motivating question behind BEAT**: can we have asynchronous BFT storage that significantly outperforms asynchronous general SMR?

## BEAT Protocols

* **Beat0**: secure, efficient threshold encryption, direct instantiation of threshold coin flipping (in lieu of using threshold signatures), and flexible, efficient erasure-coding support
* **Beat1**: replaced erasure-coded broadcast (AVID broadcast) with replication-based broadcast (Bracha's broadcast). This reduces latency when there is low contention and small batch size.
* **Beat2**: reduces latency by moving the encryption part of the old threshold encryption to the client; achieves this by trading liveness, but it can still be combined with  asynchronous communication networks to achieve full liveness. This variant also achieves causal order.
* **BEAT3**: a BFT storage system...