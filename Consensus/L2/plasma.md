# Plasma

Plasma is a layer 2 consensus mechanism that employs fraud proofs to enforce state transitions on the main blockchain. This class of L2 protocols relies heavily on an `assert/challenge` framework. The basic idea is to use time commitments to construct a fidelity bond which acts as the `assert/challenge` agreement such that the asserted data is subject to a dipute period during which an abserver may submit a proof to enforce(/prevent) valid(/invalid) state transitions.

Plasma is *recursive* and may maintain arbitrary depth at the gradual loss of availability. In the [whitepaper](https://plasma.io/plasma.pdf), Plasma's ability to nest channels is compared to the court system:

*One can view the root blockchain as the Supreme Court from whichthe power of all subordinate courts derive their power.  It is the law of the root blockchainwhich allows for all lower courts to derive their judicial power.  This allows for scalability invenues, it’s only when the state of the lower courts is disputed or halted that one needs tomove on to higher courts for a more represented venue.  Broadcasting attestations of statein higher courts are always possible, but can be more expensive.*

## Minimal Viable Plasma

*[ethresear.ch: minimal viable plasma](https://ethresear.ch/t/minimal-viable-plasma/426)*

## Plasma Cash is Plasma

*[ethresear.ch: plasma with much less per user data checking](https://ethresear.ch/t/plasma-cash-plasma-with-much-less-per-user-data-checking/1298)*
* [Simon DLR Plasma Cash Primer](https://blog.ujomusic.com/a-plasma-cash-primer-27dcfd1d5ddc)

## Plasma XT

*[ethresear.ch: plasma cash with much less per user data checking](https://ethresear.ch/t/plasma-xt-plasma-cash-with-much-less-per-user-data-checking/1926)*

Successful checkpoints allow users to discard the history prior to the checkpoint and significantly reduce the storage requirements from a user standpoint as the checkpoint is viewed as final and transactions prior to it cannot be reversed or challenged. Cryptoeconomic aggregate signatures allow operators to efficiently get sign-off from the users on a proposed checkpoint using bitfields.

## Plasma Debit

*[ethresear.ch: arbitrary denomination payments in plasma cash](https://ethresear.ch/t/plasma-debit-arbitrary-denomination-payments-in-plasma-cash/2198)*

## More Viable Plasma

*[ethresear.ch: more viable plasma](https://ethresear.ch/t/more-viable-plasma/2160)*

An alternative attempt to improve on confirmation signatures in the context of the Plasma exit game; the proposed exit game provides significantly improved UX at the cost of a two-period challenge-response scheme in the worst case.

## Reading Resources

* [Scaling Ethereum with Plasma: Georgios Konstantopolous of Loom](https://podcast.ethhub.io/scaling-ethereum-with-plasma-georgios-konstantopoulos-of-loom) -- Into The Ether podcast on December 27, 2018
* [SNARK-driven Plasma: Introducing Ignis: Fire Plasma](https://medium.com/plasma-ignis/presenting-ignis-plasma-of-fire-502fab5a6f17)
