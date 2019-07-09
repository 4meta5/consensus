# Distributed Consensus Revisited

* actors of the same type don't talk to each other

* the value being decided is often an offset to a log of operations
* consensus around the order of operations to state

* value can be sent with a `prepare`, but this is really up to the implementation
* if a `prepare` is made by the proposer with a higher epoch than what the acceptor has, the acceptor bumps their epoch

* dueling proposers is when proposers cut off the final `propose` with a `prepare` to bump the epoch of the acceptor so that the other proposal isn't accepted

* read Lamport's paper on part-time parliaments and islands

**Databases to read about**
* `ectd`, Cassandra

## Questions

* what is clock skew? clock drift relevance?
> *Exactly one fixed proposer is live and its relative clock is no faster than some delta ahead of global time (this is to prevent proposers duelling indefinitely)* **WHAT?**
* we often require an intersection for the set of epochs among proposers (majority of proposers for each epoch number) in order to ensure that at least one node can catch any inconsistency?

## References

* **[Distributed Consensus Revised, Thesis by Heidi Howard](https://www.repository.cam.ac.uk/bitstream/handle/1810/291682/thesis.pdf?sequence=1&isAllowed=y)**
* [The Morning Paper, part I](https://blog.acolyer.org/2019/05/07/distributed-consensus-revised-part-i/)
* [The Morning Paper, part II](https://blog.acolyer.org/2019/05/08/distributed-consensus-revised-part-ii/)
* [The Morning Paper, part III](https://blog.acolyer.org/2019/05/10/distributed-consensus-revised-part-iii/)

* [The Paper Trail, Paxos](https://www.the-paper-trail.org/post/2009-02-03-consensus-protocols-paxos/)

### Glossary
> would be worth building a glossary of terms (and different definitions in different contexts)

* linearizability: establishes order, persistence to disk is important in this context
* durability: state persists
* safety: finality (if a value has been *decided*, no other value will be decided)
* progress: under a specific set of liveness conditions, if a value has been proposed by a participant then the value is **eventually** decided
* eventual learning: `=>` decided `=>` eventually learned