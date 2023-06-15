---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Scaling & Anonymizing Bitcoin At Layer 1 Through Client-Side Validation.md","permalink":"/bit-devs/resources/notes/scaling-and-anonymizing-bitcoin-at-layer-1-through-client-side-validation/","title":"Scaling & Anonymizing Bitcoin Through Client-Side Validation","tags":["rgb, scaling"],"noteIcon":"3","created":"2023-06-11T21:56:42.351-10:00","updated":"2023-06-14T22:19:13.515-10:00"}
---



# Description

Maxim Orlovsky from the LNP/BP Standards Association released a proposal outlining how client-side validation could be leveraged to improve scalability, privacy, and contract expressiveness on Bitcoin.

****
> [!QUOTE] [Scaling and anonymizing Bitcoin at layer 1 with client-side validation](https://github.com/LNP-BP/layer1) (full proposal) 
> - In the paper, we propose a way to upgrade Bitcoin layer 1 (blockchain/timechain) without a required softfork. The upgrade leverages properties of client-side validation, can be gradual, has a permissionless deployment option (i.e. not requiring majority support or miner cooperation) and will have the scalability of the order (no zk-proofs) or (with zk proofs), where is a global number of transactions.
> - The original implementation of Bitcoin by Satoshi Nakamoto brought the strange idea that everybody needs to verify transactions for the whole world.
> - **Introduction of the ledger has created two problems: absence of scalability and poor privacy**; the first prevents adoption and networking effect from happening; the other contradicts the original cypherpunk spirit of Bitcoin and represents a strategic civilizational risk.
> - The first ideas in this space came with Peter Todd's back in 2016 and 2017 when he pointed out that **the owners of some state (for instance BTC or any other stateful contract) need to verify just a part of the transactional history - the part which is directly related to their ownership - and omit the rest. He named his approach client-side validation**. Giacomo Zucco designed a protocol able to create assets with this approach, named **RGB**.
> - In my previous work at LNP/BP Standards Association I was able to develop RGB further and convert it into the first generic client-side-validated smart-contract system with rich state and bounded Turing-complete computing, providing sufficient functionality to run anything which can be done with blockchain-based smart contracts - but without the public ledger/blockchain storing any user data, directly utilizing anti-double-spending properties of Bitcoin PoW consensus protocol. This system was publicly developed during the course of four years and got released in April 2023.
> - In the current proposal we demonstrate that Bitcoin, if provided with a stateful client-side-validated layer (like RGB), can be upgraded to a system without the limiting properties of public ledger (blockchain), and, while preserving PoW consensus protocol, it can be re-based onto a new scalable non-blockchain layer 1 (**codenamed Prime**).
> - This layer will be able to **host a theoretically indefinite number of transactions (at least billions per minute)** since the storage of state, computing and validation will be moved to the client-side-validated layer above.
> - The protocol has **three deployment options (permissionless, miner-activated, and softfork)**, with the first two not requiring any soft- (or hard-) fork. Options are independent, but can also be deployed in a consequent way.
> - The proposal provides several benefits to Bitcoin as digital cash
> 	- **Higher scalability**, achieved at the base layer, without the need for Lightning Network or other dedicated scalability solutions
> 	- **Much improved privacy** with no publically exposed transaction graph, ledger, addresses or public keys;
> 	- **Rich programmability**, provided by RGB or other client-side-validation systems;
> 	- **Better upgradability**: new protocol features may be adopted gradually and without reaching a wide consensus
> - Some relative drawbacks of the proposed system are:
> 	- **Instead of downloading blockchain participants must keep track of the updates from miners** since a part of the information required for the validation is ephemeral and not persisted by the network. However, dedicated trustless services may appear, which will cache this information and provide it later for a fee (which prevents the unhealthy state of the Bitcoin blockchain where "everybody keeps everything for everybody for free").
> 	- **BTC as currency, once transferred to the Prime in a trustless way, can't be brought back trustlessly without a Bitcoin blockchain softfork** providing support for either zk op-codes, drivechains or other decentralized/trustless peg-out mechanisms. Alternatively, if the new layer gets higher adoption than the blockchain layer, such peg-out would not be needed at all.
> - The proposed system (codenamed Prime) consists of four main components:
> 	- **Timestamping service**, generating a sequence of compact (~100 bytes) headers, which periodicity can be 10 minutes or less (up to 10 seconds), improving finality properties;
> 	- **Proofs**: ephemeral public data produced and published by miners alongside headers. The proofs are not required to be stored by the network and are parsed into individual proofs kept by the users of the protocol in their client-side-validated data storages (named stashes).
> 	- **Single-use-seal protocol**, providing protection from double-spending attacks.
> 	- **Smart contract protocol**, operating with client-side-validated data and providing programmability and rich state. Each piece of business logic in the system, including mining fees, is defined as a separate smart contract. Individual contracts are sharded and their history is not linked directly (in the future it may be linked with zero-knowledge proofs). A ready-to-go solution is to use RGB, however, other systems may be developed as well.
> - These components are jointly equivalent in their functionality to a blockchain-type ledger; however, in our design they become abstracted, providing much more scalability and privacy than any other blockchain system.

# More Resources
- [The Kevin Rooke Show - E108: Maxim Orlovsky on Building RGB, Standards for BTC & LN, and Smart Contracts on Bitcoin](https://fountain.fm/episode/Zpq9GFPXY71z6hS6U0IQ)
- [RGB protocol announcement on the bitcoin-dev mailing list](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2023-April/021554.html)