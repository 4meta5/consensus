# Cumulus Notes

1. **consensus**: run a Polkadot node internally, and dictate to the client and synchronization algorithms which chain to follow, finalize, and treat as best
2. **runtime**: wrapper around substrate runtimes to turn them into parachain validation code and to provide proof-generation routines
3. **collator**: Polkadot collator for the parachain

## Consensus

* Polkadot parachain types in `polkadot/primitives/src/parachain.rs`

`LocalClient` trait represents a helper for the local client. It maintains a type `Block` from `sr_primitives::traits::Block` and has two methods both of which take the hash of the associated type and returns the `ClientResult<bool>` from `substrate_client`:
1. `mark_best` marks the given block as the best block or returns `false` if the block isn't known
2. `finalize` finalizes the given block and returns false if it is unknown

There is an `Error` enum with variants `Client(ClientError)` (where `ClientError` is from `substrate_client`), `Polkadot(P)`, and `InvalidHeadData`.

There is a struct for the parachain head update referred to as `HeadUpdate` with two fields:
1. `relay_hash`: the relay chain's block hash where the parachain head was updated
2. `head_data`: the parachain head-data

The `PolkadotClient` is a trait that conforms to `Clone` and seeks to emulate `Arc` as a lightweight handle. It has three associated types:
1. the `Error` which conforms to trait bounds `std::fmt::Debug + Send`
2. `HeadUpdates` which yields updates to the parachain head -- it is a `Stream<Item=HeadUpdate, Error=Self::Error> + Send`
3. `Finalized` which yields finalized head data for a certain parachain -- it is a `Stream<Item=Vec<u8>, Error=Self::Error> + Send`

The associated methods for `PolkadotClient` are `head_updates` which takes `&self` and the `ParaId` and returns `Self::HeadUpdates`; `finalized_heads` follows the same pattern with `Self::Finalized` as the return type.

