---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/ZeroSync demos Header Chain Verifier - Instantly verify Bitcoin's block header chain in your browser.md","permalink":"/bit-devs/resources/notes/zero-sync-demos-header-chain-verifier-instantly-verify-bitcoin-s-block-header-chain-in-your-browser/","title":"ZeroSync demos Header Chain Verifier - Instantly verify Bitcoin's block header chain in your browser","tags":["bitdevs","bitcoin","socratic-26","zkp","proof","node","sync","decentralization","zerosync"],"noteIcon":"3","created":"2023-09-12T21:29:50.183-10:00","updated":"2023-09-17T12:50:16.212-10:00"}
---



# ZeroSync Overview

> [!QUOTE] [[para/1. Projects/Honolulu BitDevs/Resources/Notes/How ZeroSync hopes to reduce the costs of validating bitcoin nodes\|How ZeroSync hopes to reduce the costs of validating bitcoin nodes]]
> - ZeroSync is a project that aims to reduce the computational costs of bootstrapping a fully-validating Bitcoin client by using zero-knowledge proofs (ZKPs).
> - **ZKPs in a nutshell**: You prove something without actually revealing the information that would conventionally prove it (in this case, a signature from a single public key).
> - ZKPs can be used to **allow highly-complicated script conditions to be proven with a small or constant amount of data** that, when verified, shows definitively that those conditions were met.
> - **ZeroSync aims to help full nodes accomplish a much faster initial sync by iteratively constructing three proofs** that will, when finished, provide a **full verification of the historical blockchain without requiring a user to actually download and process it**.
> - **No consensus change to the Bitcoin protocol is required to accomplish this**, as everything happens simply at the application level, i.e., in the software you run.
> - **The three proofs being constructed are:**
> 	- **Block header proofs** that cover the validity of block headers, proving that each block in the chain met the difficulty requirement at the time and tracks each difficulty change to ensure that every block meets the appropriate target
> 	- **Transaction inclusion proofs** that verify that transactions are included in a block and are valid
> 	- **UTXO set proofs** that ensure the current UTXO set is correct and has not been modified since the last block
> - Given that the blockchain is [currently almost 500 GB in size](https://ycharts.com/indicators/bitcoin_blockchain_size), there is a very restrictive cost that prevents a large number of users from running a validating client.
> - ZeroSync could **bring that cost down to a few gigabytes for the UTXO set and a ZKP proof so small that it could fit on a 1.44 MB floppy disk**. _And it requires no consensus changes or forks whatsoever to do it_.

# What Happened?

The ZeroSync team published a demo of their [Header Chain Verifier](https://zerosync.org/demo/), which lets you verify a recursive proof of Bitcoin's header chain in your browser. This is the first of the 3 proof types described above - the **block header proofs**.

The block header proof alone isn't particularly interesting, but it is an important milestone in the ZeroSync roadmap and is a strong proof-of-concept.

[![BitDevs-26-zerosync-1.png](/img/user/para/artifacts/BitDevs-26-zerosync-1.png)](https://x.com/robin_linus/status/1700601091329606124?s=20)

# More Context

> [!QUOTE] [ZeroSync & Blockstream Satellite - Blockstream Talk 22](https://blockstreamtalk.com/episodes/blockstream-talk-22-zerosync-blockstream-satellite-kVi9Kqxs) podcast transcription snippets
> - Zerosync is a non profit working on technology that allows for a compact cryptographic proof to substitute the hundreds of gigabytes of information that make up the Bitcoin blockchain, meaning the entire history of Bitcoin could be validated in an instant rather than in hours or days.
> - And when combined with something like the Blockstream satellite network, the implications are pretty far reaching.
> - All of a sudden, every smartphone on every part of the planet is capable of validating the Bitcoin network, and the number of nodes goes from something like just under 20,000 to maybe 20 billion or more.
> - We are using the zero knowledge proofs to basically compress the Bitcoin blockchain - that is, in one sentence, what we are doing. And we're using Stark proofs, and these are a particular kind of zero-knowledge proofs. What's important about them is they are transparent, which means there is no trusted setup involved.
> - So it's a cryptographic measure to have a very large computation or very large proof and be able to verify it succinctly without having to trust the prover. That is an important part that surprises people often - that there is absolutely no trust involved. Even if your biggest enemy creates the proof, there is no way for them to cheat.
> - The main application we are currently building is the chain proof, which is a proof of the entire blockchain. And it allows you to sync the chain state instantly. So instead of downloading the entire blockchain 500GB or so and verifying that entire 500GB, you just verify a proof. And that proof is as good as if you had downloaded the entire blockchain.
> - I think there might be more phones on the planet than there are people at this point. And every one of those phones could be a node for bitcoin. That makes me think about the Blockstream Satellite.
> - The Blockstream Satellite and ZeroSync are a perfect match because the bandwidth constraints are so strong with the initial block download. And currently, when you sync with Blockstream Satellite, it takes more than a week or even weeks. A ZeroSync proof would allow you to sync that basically instantly.
> - Also you could build subnetworks. Like one person receives it via satellite and they can easily reshare the proof with all other people in the community, which is much easier with a proof than with the blockchain. Of course, you could also reshare the 500GB of blockchain, meaning that if... someone has access to Blockstream Satellite that they could kind of act as a hub and a spoke for everybody around them that they could interact with on a mobile device.
> - But the grand vision would be that people could reshare those proofs in rural areas and create a subnetwork for bitcoin.
> - You have a proof that is very hard or impossible to forge and you can look into the bitcoin blockchain and just see if the payment happened or the transaction happened. That's another way users would benefit or the whole ecosystem would benefit from it.
> - This is still a very early stage, and we have just completed our first major milestone of recursive chain proof. That means we have implemented most of bitcoin's consensus rules, and we have also implemented a recursive verifier that is necessary to incrementally extend proofs.
> - We want to roll it out in multiple stages. The first stage would be just a headers chain proof that is not that interesting by itself, but it makes sense to have it as a first milestone. Hopefully, we can roll it out by the end of this year.
> - The toolkit is basically a byproduct of what we are building because we are implementing all the bitcoin consensus rules. It's basically a byproduct that we are creating a library for bitcoin proofs. You can reuse our proofs to prove anything about a bitcoin transaction. And when we figured that out, we decided that we're going to ship that toolkit for people to customize proofs and to customize them for their individual use cases.
> - But computing the proof is very computationally intensive. In the current version that we have now, it's maybe even intractable. But there are lots of ways to improve the performance of the prover, and the main obstacle is to make proving fast enough for us to be able to prove a full block within ten minutes - because we should be able to complete the proof before the next block arrives.
> - The other thing is we can roll it out as kind of with a backup mechanism. So you could use the proof to instantly sync your node and then, over time, use the conventional peer-to-peer network to sync your node. If you find any errors after that, or if you don't find any, you can be sure that the proof was correct. So you cannot be fooled for longer than three or four days.
> - You can just have your phone sync it instantly. And then even if you don't want to sync it anymore... You could stop being in sync, and then after a few blocks, or a few hundred blocks, you turn on the proof again, get a new proof, and be up to date instantly. So I think this really lowers the entry barrier for users of the Bitcoin.
> - It could expand the number of nodes by a huge amount. We could have billions of nodes with better geographical dispersion as well. The security of any decentralized currency stems from everybody verifying everything and, of course, that scales poorly because your phone will not verify the transactions of billions of people. But with such a proof system, it is suddenly possible. That solves one of the fundamental scalability problems of Bitcoin.
> 



# More Resources
- [Bitcoin Nodes Now One Step Closer To Instant Sync](https://bitcoinmagazine.com/technical/bitcoin-nodes-now-one-step-closer-to-instant-sync)
- [ZeroSync - Introducing STARKs to Bitcoin (Tabconf Slides)](https://docs.google.com/presentation/d/1KgNTxulMnIa3SCQIh4P061cIW6Jz_IZYMwqzaohA8ds/edit?pli=1#slide=id.g27e0704f09f_0_4)
- [How Bitcoin Usage Could Skyrocket Thanks To Zero-Knowledge Proofs](https://www.forbes.com/sites/digital-assets/2023/08/21/how-bitcoin-usage-could-skyrocket-thanks-to-zero-knowledge-proofs/?sh=62c73b04bde6)
- [How ZeroSync hopes to reduce the costs of validating bitcoin nodes](https://bitcoinmagazine.com/technical/zerosync-reduces-bitcoin-node-validation)
- [Stephan Livera Podcast 484 Robin Linus ZeroSync: Speeding up Bitcoin IBD](https://stephanlivera.com/episode/484/)


