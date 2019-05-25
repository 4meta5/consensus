# State Channels

*State channels function under the assumption of unanimous consent amongst parties involved whereas Plasma relies on merkle proofs submitted to the main chain by the Plasma validator(s). As a result, changes made in a state channel achieve finality as soon as messages are signed and do not need to wait for confirmations in order to consider transactions completed and secure (state channels are the only stateful blockchain construction with this property). By contrast Plasma users must still wait for confirmations in order to consider their transactions completed and secure. In Plasma, the validator set is usually assumed to be different than and smaller than the participant set whereas in state channels they are the same set. Additionally, Plasma requires main chain transactions in order to publish the merkle root of the off-chain state periodicaly, whereas state channels do not necessarily assume that any on-chain operations will ever be necessary.* -[counterfactual](https://www.counterfactual.com/statechannels/) 

## References

* [An Empirical Evaluation of State Channels](https://github.com/stonecoldpat/statechannels)
* [Counterfactual: Generalized State Channels on Ethereum](https://medium.com/statechannels/counterfactual-generalized-state-channels-on-ethereum-d38a36d25fc6)

**Applications**
* [The State of State Channels (2018)](https://blog.coinfund.io/the-state-of-state-channels-2018-edition-f5492134ab96)
