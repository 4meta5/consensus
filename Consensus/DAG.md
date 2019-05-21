# DAGs

**Protocols**
* Casper CBC
* Casanova

### Spectre
*Serialization of Proof of Work Events, Confirming Transactions via Recursive Elections*
* systematic system for deciding pairwise ordering between two transactions

* [Explainer](https://medium.com/@avivzohar/the-spectre-protocol-7dbbebb707b5) by Aviv Zohar

### Iota

* conflating the p2p layer with the consensus safety seems *unsafe* -- adds friction to make it usable as a permissionless system

*Their entire idea of a fee-less system assumes that everyone does the Proof of Work for their own transactions aka everyone provides computational power to the network proportional to their usage of the network. However, if you think about it, that’s also true for normal blockchains...Amortized over time, this would roughly earn you 10% all of all transaction fees in the network, basically getting you to a net zero on transaction fee costs. However, the reason that this is not the case is that there is a discrepancy between the distribution of the usage of the network and the distribution of available computational power. Because this discrepency doesn’t just disappear, it gives me the intuition that there is an economic attack vector possible without the transaction fees*

* Without mining rewards, there is no incentive for someone to be actively providing security to the system at all times -- therefore an attacker doesn't have to overpower the entire honest computational power of the network but, instead, just the honest computational power of the network actively making transactions at any given time
* basically they can just wait for a drop in transaction throughput at off-peak hours and then launch an attack to overpower the honest input flow

* [Thougts on Iota](https://conspirat.us/thoughts-on-iota-df7ef25bfc37) by Sunny

## Watching
* [Concurrency on the Blockchain](https://www.youtube.com/watch?v=fYKxdb0YcXs) -- **Casanova**
* using `pi calculus` for DAGs
* `rho calculus`
* **aggregation throttles concurrency**
* rent collection transactions
* zero weight validators (make reductions, gossip, and don't stake)
* multiple consensus protocols at the same time (multiple sets of validators...)

### Error Correcting Codes
* [error correcting codes and their relationship to distributed agreement](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.129.3561&rep=rep1&type=pdf)