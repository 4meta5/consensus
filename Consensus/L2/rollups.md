# Rollups

**MOTIVATION**: Most layer 2 solutions maintain a security model that depends on liveness assumptions `=>` vulnerable to mass exit issues `&&` a bad operator can cause liveness to fail

## Rollups Solve

Roll_up aggregates transactions so that they only require a single onchain transactions required to validate multiple other transactions. The snark checks the signature and applies the transaction to the the leaf that the signer owns.

Multiple users create signatures. Provers aggregates these signatures into a snark and use it to update a smart contract on the ethereum blockchain. A malicious prover who does not also have that leafs private key cannot change a leaf. Only the person who controls the private key can.

### Philosophy

`Trustless ~= non-custodial`; an optimally trustless but permissioned L2 is better than a permissionless L2 where coins can be stolen or destroyed

## References
* [recent twitter feed on rollup benefits by Vitalik and John Adler vs Rick Dudley](https://twitter.com/vitalikbuterin/status/1129782589596852229?refsrc=email&s=11)
* [barryWhiteHat/roll_up](https://github.com/barryWhiteHat/roll_up)
