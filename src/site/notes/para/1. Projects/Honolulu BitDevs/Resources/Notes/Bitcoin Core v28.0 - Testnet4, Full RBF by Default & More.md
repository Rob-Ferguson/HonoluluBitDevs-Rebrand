---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bitcoin Core v28.0 - Testnet4, Full RBF by Default & More.md","permalink":"/bit-devs/resources/notes/bitcoin-core-v28-0-testnet4-full-rbf-by-default-and-more/","title":"Bitcoin Core v28.0 - Testnet4, Full RBF by Default & More","tags":["bitcoin","bitdevs","socratic-38"],"noteIcon":"3","created":"2024-10-22T19:14:30.329-10:00","updated":"2024-10-22T19:53:31.117-10:00"}
---




> [!QUOTE] [Bitcoin Core v28.0: Testnet4, Full RBF by Default & More](https://www.nobsbitcoin.com/bitcoin-core-v28/) 
> ## What's new
> 
> Some of more notable changes introduced in Bitcoin Core v28 include:
> - **Testnet4/BIP94 Support.** Support for Testnet4 as specified in [BIP94](https://github.com/bitcoin/bips/blob/master/bip-0094.mediawiki) has been added. Testnet3 will be phased out in an upcoming version.
> 	- The BIP94 timewarp attack mitigation is now active on the `regtest` network.
> - **Opportunistic one-parent-one-child (1p1c) package relay.** Transactions with low fee rates can be paired with their child transactions and submitted as a package, allowing nodes to download 1-parent-1-child packages via the transaction relay protocol.
> - **Default relay of opt-in topologically restricted until confirmation (TRUC) transactions.** The new policy includes limits on spending unconfirmed outputs, eviction of a previous descendant if a more incentive-compatible one is submitted, and a maximum transaction size of 10,000vB.
> 	- "These restrictions simplify the assessment of incentive compatibility of accepting or replacing TRUC transactions, thus ensuring any replacements are more profitable for the node and making fee-bumping more reliable."
> - **Default relay of pay-to-anchor (P2A) transactions.** Pay To Anchor is a new standard witness output type for spending, a newly recognized output template.
> - **Limited package RBF relay.** Limited package RBF is now enabled, where the proposed conflicting package would result in a connected component, aka cluster, of size 2 in the mempool. All clusters being conflicted against must be of size 2 or lower.
> - **Full RBF by default.** The default value of the `-mempoolfullrbf` configuration option has been changed from 0 to 1, i.e. `mempoolfullrbf=1`.
> - **AssumeUTXO available on mainnet.** AssumeUTXO mainnet parameters have been added for height 840,000. The `loadtxoutset` RPC can now be used on mainnet with the matching UTXO set from that height.
> - **New Windows Data Directory.** The default Windows data directory has been moved to `C:\Users\Username\AppData\Local\Bitcoin`. If old directory is present, the client will continue to use it for backwards compatibility.
> - **JSON-RPC 2.0 Support.** The JSON-RPC server now recognizes JSON-RPC 2.0 requests and responds with strict adherence to the [specification](https://www.jsonrpc.org/specification).
> 	- "JSON-RPC clients may need to be updated to be compatible with the JSON-RPC server. [Please open an issue on GitHub](https://github.com/bitcoin/bitcoin/issues/31039) if any compatibility issues are found."
> - **libbitcoinconsensus Removal.** The libbitcoin-consensus library was deprecated in 27.0 and is now completely removed.
> - **Easier to migrate legacy wallets to descriptor wallet format.**
> 	- The "Migrate Wallet" menu allows users to migrate any legacy wallet in their wallet directory, regardless of the wallets loaded.
> 	- A new `createwalletdescriptor` RPC allows users to add new automatically generated descriptors to their wallet. This can be used to upgrade wallets created prior to the introduction of a new standard descriptor, such as taproot.
> - **Blockstorage improvements.** Block files are now XOR'd by default with a key stored in the blocksdir.
> - **Maximum mempool size along with the mempool usage** are now displayed in the "Information" window.
> - **UNIX domain sockets** can now be used for proxy connections.
> - **GCC 11.1 or later, or Clang 16.0 or later**, are now required to compile Bitcoin Core.
> - **The minimum required glibc to run Bitcoin Core is now 2.31**. This means that RHEL 8 and Ubuntu 18.04 (Bionic) are no-longer supported.

[![BitDevs-38-Bitcoin-v28-X-1.png](/img/user/para/artifacts/BitDevs-38-Bitcoin-v28-X-1.png)](https://xcancel.com/roasbeef/status/1842956355516223824)

[![BitDevs-38-Bitcoin-v28-X-2.png](/img/user/para/artifacts/BitDevs-38-Bitcoin-v28-X-2.png)](https://x.com/realtbast/status/1834213774674247987)

# More Resources
- [Bitcoin Core v28.0 Release Notes](https://github.com/bitcoin/bitcoin/blob/master/doc/release-notes/release-notes-28.0.md)
- [Bitcoin Explained Episode 95: Bitcoin Core v28.0](https://bitcoinexplainedpodcast.com/@nado/episodes/episode-95-bitcoin-core-v280/activity)

