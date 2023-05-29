---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bitcoin Transaction Package Relay.md","permalink":"/bit-devs/resources/notes/bitcoin-transaction-package-relay/","title":"Bitcoin Transaction Package Relay","noteIcon":"3","created":"2023-05-29T12:51:01.067-10:00","updated":"2023-05-29T12:56:51.544-10:00"}
---


# Description

> [!QUOTE] [Package relay | Bitcoin Optech](https://bitcoinops.org/en/topics/package-relay/)
> **Package relay** is a proposed feature for Bitcoin relay nodes that would allow them to send and receive packages of related transactions which would be accepted or rejected based on the feerate of the overall package rather than having each individual transaction in the package accepted or rejected based only on its own feerate. 
> 
> Without package relay, it’s not possible to effectively [CPFP](https://bitcoinops.org/en/topics/cpfp/) fee bump a transaction that’s below the minimum feerate nodes accept. Nodes will reject the parent transaction for its too low feerate and then ignore the fee-bumping child transaction because the parent transaction is needed in order to validate the child. This is especially problematic because the minimum feerate that a node accepts depends on the contents of its mempool, so a parent transaction that could previously be fee bumped might not be bumpable now. This has significant security implications for LN and other time-sensitive contract protocols that want to depend on CPFP fee bumping.
> 
> The main obstacle to adding package relay support to the Bitcoin P2P protocol is ensuring that an implementation of it doesn’t create any new vectors for denial-of-service attacks.

# Package Relay over Nostr

[![Nostr_txPackageRelay_Demo.png](/img/user/para/artifacts/Nostr_txPackageRelay_Demo.png)](https://twitter.com/joostjgr/status/1658487013237211155)

# More Resources
- [Bitcoin Transaction Relay over Nostr](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2023-May/021700.html)