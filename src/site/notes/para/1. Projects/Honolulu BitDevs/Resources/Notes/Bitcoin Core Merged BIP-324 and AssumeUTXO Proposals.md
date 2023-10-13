---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bitcoin Core Merged BIP-324 and AssumeUTXO Proposals.md","permalink":"/bit-devs/resources/notes/bitcoin-core-merged-bip-324-and-assume-utxo-proposals/","title":"Bitcoin Core Merged BIP-324 and AssumeUTXO Proposals","tags":["bitdevs","bitcoin","socratic-27","privacy","node"],"noteIcon":"3","created":"2023-10-11T16:31:09.561-10:00","updated":"2023-10-12T15:58:45.698-10:00"}
---



# What happened?

Initial pull requests for [BIP-324](https://github.com/bitcoin/bitcoin/pull/28331) and [AssumeUTXO](https://github.com/bitcoin/bitcoin/pull/27596) have been merged into Bitcoin Core. These upgrades improve node privacy and bootstrapping UX.

# BIP-324

BIP-324 is an upgrade to the P2P gossip layer that will allow Bitcoin nodes to communicate with each other over encrypted connections. It is opt-in and backwards compatible (v2 clients will allow inbound v1 connections).

> [!QUOTE] [What Is BIP324? - The Bitcoin Manual](https://thebitcoinmanual.com/articles/what-is-bip324/)
> One potential attack vector for nodes on the network is the way nodes communicate with each other via unencrypted traffic. Powerful interests like governments and Internet Service Providers (ISPs) could use this weakness to wage “man in the middle” attacks on Bitcoin nodes, and you wouldn’t know it until it’s too late. Those gatekeepers of internet connections and traffic relays can secretly gather information about sent transactions.
> 
> ...
> 
> BIP324 is an improvement proposal that aims to enhance the [privacy of Bitcoin nodes](https://thebitcoinmanual.com/articles/protect-bitcoin-full-node/), making the network more robust and secure. **The update is a proposal to encrypt traffic between nodes connected to the Bitcoin network to make network metadata, like the location a transaction is coming from, more private, making it harder for third parties monitoring internet traffic to spy on this type of data transfer.**
> 
> ---
> 
> ## How BIP324 helps improve node privacy:
> 
> 1. **Encrypted communication**: By encrypting the messages exchanged between nodes, BIP324 makes it much harder for eavesdroppers to intercept and analyse the data transmitted between nodes, protecting user privacy.
> 2. **Authentication**: The Noise protocol also ensures that the nodes communicating with each other are authentic, preventing potential man-in-the-middle attacks.
> 3. **IP address protection**: Since the communication between nodes is encrypted, it becomes more difficult for malicious actors to associate a user’s IP address with their transactions or other activities.
> 4. **Confidentiality against passive attacks**: A passive attacker having recorded a v2 P2P bytestream (without timing and fragmentation information) must not be able to determine the plaintext being exchanged by the nodes.
> 5. **Observability of active attacks**: A session ID identifying the encrypted channel uniquely is derived deterministically from a Diffie-Hellman negotiation. An active man-in-the-middle attacker is forced to incur a risk of being detected as peer operators can compare session IDs manually, or using optional authentication methods possibly introduced in future protocol versions.
> 6. **Pseudorandom bytestream**: A passive attacker having recorded a v2 P2P bytestream (without timing information and fragmentation information) must not be able to distinguish it from a uniformly random bytestream.
> 7. **Shapable bytestream**: It should be possible to shape the bytestream to increase resistance to traffic analysis (for example, to conceal block propagation), or [censorship avoidance](https://gitlab.torproject.org/legacy/trac/-/issues/20348#note_2229522).
> 8. **Forward secrecy**: An eavesdropping attacker who compromises a peer’s sessions secrets should not be able to decrypt past session traffic, except for the latest few packets.
> 9. **Upgradability**: The proposal provides an upgrade path using transport versioning which can be used to add features like authentication, PQC handshake upgrade, etc. in the future.
> 10. **Compatibility**: v2 clients will allow inbound v1 connections to minimise risk of network partitions.
> 11. **Low overhead**: introducing a new P2P transport protocol should not substantially increase computational cost or bandwidth for nodes that implement it, compared to the current protocol.

# AssumeUTXO

AssumeUXTO enables instant UTXO set bootstrapping for Bitcoin nodes by temporarily trusting a snapshot from another node (while still downloading and verifying the entire chain in the background).

> [!QUOTE] [AssumeUTXO | River Learning Center](https://river.com/learn/terms/a/assume-utxo/)
> AssumeUTXO is a proposed, optional setting that would **allow users to make use of their Bitcoin node before [initial block download (IBD)](https://river.com/learn/terms/i/initial-block-download-ibd/) is complete**. IBD is one of the most prohibitive costs to running a node, so reducing or hiding this burden is an important improvement for Bitcoin’s usability and decentralization.
> 
> **AssumeUTXO allows users who are launching full nodes to first download a full copy of the [UTXO set](https://river.com/learn/terms/u/utxo-set/) from a node, allowing their node to immediately start crafting, querying, and broadcasting transactions. In the background, the full node still downloads and verifies each block, maintaining the trustless nature of Bitcoin.**
> 
> Without AssumeUTXO, users must wait to craft and query transactions until their node has downloaded and validated the entire blockchain, a process that can take up to two weeks depending on the computer.

[![BitDevs-27-AssumeUTXO-JamesOBeirne-Tweet.png](/img/user/para/artifacts/BitDevs-27-AssumeUTXO-JamesOBeirne-Tweet.png)](https://nitter.net/jamesob/status/1708993120036110695)

# More Resources

- BIP-324
	- [BIP-324: Version 2 P2P Encrypted Transport Protocol](https://github.com/bitcoin/bips/blob/master/bip-0324.mediawiki)
	- [Version 2 P2P transport | Bitcoin Optech](https://bitcoinops.org/en/topics/v2-p2p-transport/)
	- [BIP324: Improving Bitcoin’s P2P Transport Protocol - YouTube](https://youtu.be/7J7EfqknVpM)
	- [What Is BIP324? - The Bitcoin Manual](https://thebitcoinmanual.com/articles/what-is-bip324/)
	- [BIP 0324 - Bitcoin Wiki](https://en.bitcoin.it/wiki/BIP_0324)
	- [Marty's Bent 1231: BIP 324 would bring encryption to bitcoin's P2P layer and it needs some review](https://tftc.io/martys-bent/issue-1231-bip-324-would-bring-end-to-end-encryption-to-bitcoins-p2p-layer-and-it-needs-some-review/)
	- [BIP-324: A Message Transport Protocol That Could Protect Bitcoin Peers](https://bitcoinmagazine.com/technical/bip-324-a-message-transport-protocol-that-could-protect-bitcoin-peers)
- AssumeUTXO
	- [AssumeUTXO docs](https://github.com/jamesob/assumeutxo-docs/tree/2019-04-proposal/proposal)
	- [AssumeUTXO | Bitcoin Optech](https://bitcoinops.org/en/topics/assumeutxo/)
	- [Assume UTXO w/ James O'Beirne - YouTube](https://www.youtube.com/live/JottwT-kEdg?feature=shared)
	- [An Easier Way To Bootstrap Your Node's UTXO Set](https://bitcoinmagazine.com/technical/coming-soon-an-easier-way-to-bootstrap-your-bitcoin-nodes-utxo-set)