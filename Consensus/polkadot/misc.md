# misc

## babe

Proof of work can be *modeled* as a `gen_random < threshold(node_id)` s.t. threshold corresponds to computational power of the node in question (node with high computational power has a higher threshold).

Verifiable Random Function (VRF): cryptographic proof of PRNG generation.

In practice, `gen_random(private_key, seed, slot_number)` such that `seed` adds entropy. This PRNG is deterministic -- Moreover, in any one slot, more than one validator can produce a block. 

The seed is generated from the hash of a previous state. Divide slot periods into epochs (sessions). For example, each epoch (session) is 1000 slots. For epoch 0, the algorithm is actually collecting randomness for epoch 2.

It is easier to assume a synchronized clock, but clock drift is a legitimate problem.

Babe adds secondary slots to mitigate the high variability of block times.

## primary vs secondary blocks

Primary blocks are calculated from the VRF described above (`get_random`). 

Secondary blocks are deterministic round-robin for mitigating the problem of high variance in block times due to some unassigned blocks via the VRF.
