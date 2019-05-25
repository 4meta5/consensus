# Lightning

Lightning allows for two parties (a local node and a remote node) to conduct transactions off-chain by giving each of the parties a cross-signed commitment transaction, which describes the current state of the channel (basically, the current balance). This commitment transaction is updated every time a new payment is made and is spendable at all times.

## HTLC

*[Bitcoin Wiki: HTLC]*: hash time locked contracts leverage hashlocks and timelocks to require that the receiver of a payment either acknowledge receiving the payment prior to a deadline by generating cryptographic proof of payment or forfeit the ability to claim the payment, returning it to the payer. Direct application of HTLCs enables conditional payments for layer 2 payments or cross-chain atomic swaps. While payment channels already utilize timelocks, extending the interaction with hashlocks allows for routing across multiple payment channels.

**Example**
1. Alice opens a payment channel to Bob, and Bob opens a payment channel to Charlie.
2. Alice wants to buy something from Charlie for 1000 satoshis.
3. Charlie generates a random number and generates its SHA256 hash. Charlie gives that hash to Alice.
4. Alice uses her payment channel to Bob to pay him 1,000 satoshis, but she adds the hash Charlie gave her to the payment along with an extra condition: in order for Bob to claim the payment, he has to provide the data which was used to produce that hash.
5. Bob uses his payment channel to Charlie to pay Charlie 1,000 satoshis, and Bob adds a copy of the same condition that Alice put on the payment she gave Bob.
6. Charlie has the original data that was used to produce the hash (called a pre-image), so Charlie can use it to finalize his payment and fully receive the payment from Bob. By doing so, Charlie necessarily makes the pre-image available to Bob.
7. Bob uses the pre-image to finalize his payment from Alice

## References

* [Lightning Network Specification](https://github.com/lightningnetwork/lightning-rfc)
* [Bitcoin Q&A: How do payment channels work?](https://www.youtube.com/watch?v=DAuNlOfws0o&feature=youtu.be) by aantonop
* [Towards Bitcoin Payment Networks](http://homepages.cs.ncl.ac.uk/patrick.mccorry/paymentnetworks.pdf) by Patrick McCorry
* [An Argument For Single-Asset Lightning Network](https://lists.linuxfoundation.org/pipermail/lightning-dev/2018-December/001752.html) ~= HTLCs as American Call Option, or, How Lightning Currently Cannot Work Across Assets
