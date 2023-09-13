---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Scaling & Anonymizing Bitcoin At Layer 1 Through Client-Side Validation.md","permalink":"/bit-devs/resources/notes/scaling-and-anonymizing-bitcoin-at-layer-1-through-client-side-validation/","title":"Scaling & Anonymizing Bitcoin Through Client-Side Validation","tags":["rgb","scaling","client-side validation"],"noteIcon":"3","created":"2023-06-11T21:56:42.351-10:00","updated":"2023-06-19T14:35:52.779-10:00"}
---



# Description

[Maxim Orlovsky](https://twitter.com/dr_orlovsky) from the [LNP/BP Standards Association](https://www.lnp-bp.org/) released a proposal outlining how client-side validation could be leveraged to improve scalability, privacy, and contract expressiveness on Bitcoin.

Client-side validation is a methodology in which owners of some state (BTC transaction data, a smart contract, etc.) validate only the part of the transactional history that they own and nothing else - in in contrast to blockchain validation where all nodes maintain and validate a copy of the entire chain history. In this paradigm, the majority of activity happens off-chain, and the blockchain itself is mainly used to manage state updates for those off-chain contracts (i.e., a cryptographically enforced commitment layer), greatly increasing transactional throughput and confidentiality.

Maxim is also spearheading the development of [RGB](https://www.rgbfaq.com/what-is-rgb) (**R**eally **G**ood for **B**itcoin), which is a protocol that started development in ~2018. It is built over Bitcoin's consensus layer and uses client-side validation to enable the execution of private smart contracts between two parties. However, the concept of client-side validation itself can be adopted by other systems. This proposal outlines the general framework of client-side validation (with RGB as an example). 

> [!QUOTE] [Scaling and anonymizing Bitcoin at layer 1 with client-side validation](https://github.com/LNP-BP/layer1) (full proposal) 
> - In the paper, we propose a way to upgrade Bitcoin layer 1 (blockchain/timechain) without a required softfork. The upgrade leverages properties of client-side validation, can be gradual, has a permissionless deployment option (i.e. not requiring majority support or miner cooperation) and will have the scalability of the order (no zk-proofs) or (with zk proofs), where is a global number of transactions.
> - The original implementation of Bitcoin by Satoshi Nakamoto brought the strange idea that everybody needs to verify transactions for the whole world.
> - **Introduction of the ledger has created two problems: absence of scalability and poor privacy**; the first prevents adoption and networking effect from happening; the other contradicts the original cypherpunk spirit of Bitcoin and represents a strategic civilizational risk.
> - The first ideas in this space came with Peter Todd's back in 2016 and 2017 when he pointed out that **the owners of some state (for instance BTC or any other stateful contract) need to verify just a part of the transactional history - the part which is directly related to their ownership - and omit the rest. He named his approach client-side validation**. Giacomo Zucco designed a protocol able to create assets with this approach, named **RGB**.
> - In my previous work at LNP/BP Standards Association I was able to develop RGB further and convert it into **the first generic client-side-validated smart-contract system with rich state and bounded Turing-complete computing, providing sufficient functionality to run anything which can be done with blockchain-based smart contracts - but without the public ledger/blockchain storing any user data**, directly utilizing anti-double-spending properties of Bitcoin PoW consensus protocol. This system was publicly developed during the course of four years and got released in April 2023.
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

In April 2023, RGB v0.10 was released, which included the functional components for RGB to start being adopted in production-like systems. Now that the core consensus layer of the protocol is relatively finalized, the next step is for application-layer technologies to be developed that fully integrate and showcase RGB's key features to spur further adoption.

> [!QUOTE] [[bitcoin-dev] RGB protocol announcement](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2023-April/021554.html)
> 
> **RGB v0.10**
> 
> Today we’d like to announce the next main milestone: **release of RGB v0.10**, which includes consensus layer, standard library (used by wallets/exchanges for integration) and a command-line tool.
>
> v0.10 release is a major milestone which brings RGB further to being a production-ready system. It introduces the last consensus-breaking changes, aiming at keeping future RGB versions fully backward-compatible. It also unlocks the last features that were required for implementing fully-functional smart contracts which may be arbitrary customized by contract developers.
> 
> ---
> 
> **Roadmap after v0.10**
> With this release the future development of the core RGB technology (at in its consensus layer) becomes gradually ossified, as the cases of client-side-validated systems upgrades are more complex to coordinate than those of blockchain layer 1. Also, the normal understanding of soft-forks and hard-forks do not apply to upgrades in layer 2 and 3. So we found a way for backwards-compatible upgrades, which we call “fast-forwards”, where users keep their assets issued under the older versions that can always operate and be accepted by the users of any other future version. However, the users of a newer version will be restricted in transferring their assets only to the users of the same or more recent version (but they can always ask recipients to upgrade their software). We have a number of features planned for the future fast-forwards:
> - full support of bitcoin layer 1 and channel state introspection;
> - inter-contract interaction;
> - bulletproofs++ support;
> - zero-knowledge-based optimizations of the client-side-validated history.
> 
> We're also working on the design of a layer 1 which will be perfect for the client-side-validated applications (“how to design a blockchain today if we knew about client-side-validation/single-use-seals”). This should be very compact (order of one signature per block) ultra-scalable (theoretically unlimited no of tx in a block) chain which can run systems like RGB - with Bitcoin UTXO set migrated into RGB operating on both bitcoin blockchain and this new chain (we code-name it “sigchain”). However, these are quite early developments with a number of unsolved tradeoffs and challenges; if there is an interest on this topic here we can start a different discussion thread on the matter.


# More Resources
- [The Kevin Rooke Show - E108: Maxim Orlovsky on Building RGB, Standards for BTC & LN, and Smart Contracts on Bitcoin](https://fountain.fm/episode/Zpq9GFPXY71z6hS6U0IQ)
- [What is RGB? - RGB FAQ](https://www.rgbfaq.com/what-is-rgb)
- [Bitcoin Optech Newsletter 247](https://bitcoinops.org/en/newsletters/2023/04/19/#rgb-update)
- [RGB Update: Smart Contracts For Bitcoin & The Lightning Network! - YouTube](https://youtu.be/y2Ak970WpkA)
- [LNP-BP slideshow "RGB & Spectrum explanation for business"](https://github.com/LNP-BP/presentations/blob/master/Presentation%20slides/RGB%20%26%20Spectrum%20explanation%20for%20business.pdf)
- [RGB Protocol on Bitcoin, What is it? | Trust Machines](https://trustmachines.co/learn/what-is-the-rgb-protocol-on-bitcoin/#:~:text=Client%2Dside%20Validation,-One%20of%20RGB's&text=This%20validation%20method%20leverages%20the,and%20privacy%20are%20drastically%20improved.)
- [What Is The RGB Network - The Bitcoin Manual](https://thebitcoinmanual.com/blockchain/rgb-chain/)
- ["Emergence of Token Layers on Bitcoin: Overview of Client-Side Validation, RGB, and Taro" slideshow from the Diamond Hands community](https://docsend.com/view/he8x9erkjmphphvn)
- [Transcript of Peter Todd's "Progress on scaling via client-side validation" presentation from Scaling Bitcoin 2016 in Milan](https://scalingbitcoin.org/transcript/milan2016/client-side-validation)