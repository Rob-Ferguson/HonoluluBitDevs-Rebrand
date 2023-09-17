---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/How ZeroSync hopes to reduce the costs of validating bitcoin nodes.md","permalink":"/bit-devs/resources/notes/how-zero-sync-hopes-to-reduce-the-costs-of-validating-bitcoin-nodes/","title":"How ZeroSync hopes to reduce the costs of validating bitcoin nodes","tags":["resource","bitcoin","zkp","proof","node","sync","decentralization","zerosync"],"noteIcon":"3","created":"2023-04-05T22:10:37.122-10:00","updated":"2023-09-17T12:32:55.186-10:00"}
---


# [How ZeroSync hopes to reduce the costs of validating bitcoin nodes](https://bitcoinmagazine.com/technical/zerosync-reduces-bitcoin-node-validation)

#### Article Summary
- ZeroSync is a project that aims to reduce the computational costs of bootstrapping a fully-validating Bitcoin client by using zero-knowledge proofs (ZKPs).
- **ZKPs in a nutshell**: You prove something without actually revealing the information that would conventionally prove it (in this case, a signature from a single public key).
- ZKPs have been discussed in the Bitcoin community for over a decade but had never had a solid implementation.
- Complicated and large bitcoin scripts ultimately necessitate putting proportionally-large pieces of witness data on the blockchain in order to spend those coins.
- ZKPs can be used to **allow highly-complicated script conditions to be proven with a small or constant amount of data** that, when verified, shows definitively that those conditions were met.
- **ZeroSync aims to help full nodes accomplish a much faster initial sync by iteratively constructing three proofs** that will, when finished, provide a **full verification of the historical blockchain without requiring a user to actually download and process it**.
- **No consensus change to the Bitcoin protocol is required to accomplish this**, as everything happens simply at the application level, i.e., in the software you run.
- When complete, **anyone can choose to use a ZeroSync node and be sure the UTXO set they download is valid**, or they can keep running Bitcoin Core and fully validate everything in the conventional way.
- **The three proofs being constructed are:**
    - **Block header proofs** that cover the validity of block headers, proving that each block in the chain met the difficulty requirement at the time and tracks each difficulty change to ensure that every block meets the appropriate target
    - **Transaction inclusion proofs** that verify that transactions are included in a block and are valid
    - **UTXO set proofs** that ensure the current UTXO set is correct and has not been modified since the last block
- **Block header proofs**
	- The first proof that ZeroSync is working on covers the validity of block headers, proving that each block in the chain correctly met the difficulty requirement at the time and tracks each difficulty change to ensure that every block meets the appropriate target.
	- This also introduces a huge benefit for [Simplified Payment Verification (SPV)](https://river.com/learn/terms/s/simplified-payment-verification-spv/#:~:text=Simplified%20Payment%20Verification%20(SPV)%20is,Satoshi%20Nakamoto%20in%20the%20whitepaper) wallet architecture by applying a Merkle tree to each individual block header in the chain, allowing much more compact SPV proofs.
	- Users wouldn't need to have a copy of the block headers to verify that a transaction is committed to inside of the blockchain with block header proofs. They simply add on a Merkle path from the block header that the transaction is in to the root hash of the Merkle tree.
- **Verifying block contents**
	- The second proof is focused on the actual validity of the contents of the block, however, like the [Assume Valid](https://river.com/learn/terms/a/assume-valid/) function of Bitcoin Core, it does not prove the validity of the witness data. 
	- It will check and verify transaction size limit, coin inflation rules, etc., but doesn't provide a proof that the signatures, hash locks and other witness data are correct.
	- This proof, however, will incorporate [Utreexo](https://github.com/mit-dci/utreexo) in order to integrate the UTXO set at each block height into the overall ZKP protocol for the chain.
	- The first proof would simply show you that the block headers are valid, but that says nothing about the coin supply or the UTXO set. This second proof would allow a UTXO set to be delivered to a user with a ZKP that proves all of the block headers leading to that UTXO set are valid, as well as including a commitment to each UTXO set and all changes to it proving that each transition from one to the next is also valid.
	- This would allow for a full sync up to the Bitcoin Core default Assume Valid height with just the UTXO set at that block height and a tiny proof, all with the exact same trust model as downloading all of that and verifying the full blocks directly.
- **Verifying every piece of witness data**
	- Lastly, the final proof will incorporate both the ZKP for the block headers and build on top of the ZKP for Assume Valid to include proving the validity of every piece of witness data in the historical chain.
	- After this stage, technically speaking, a node using the final ZeroSync proof system will actually be able to bootstrap with a single proof and a UTXO set with a stronger verification model than Bitcoin Core by default.
	- The only issue with this last proof is that the computational complexity to actually construct it is much higher than that of the previous two. Verifying a proof is simple and quick, requiring only the ZKP and verifier, but constructing it actually requires taking the full, raw data that would constitute a conventional proof (in this case, the entire historic blockchain) and actually processing it to construct a ZKP for it.
	- Adding the witness data into the proof currently is very expensive. In order to achieve this roadmap goal a lot of optimization is going to be required.
	- This project would still provide a massive amount of value in allowing users to "zero sync" up to the default Assume Valid block height and then conventionally verify the rest of the chain from there to the tip.
- **How would this reduce Bitcoin's computational costs?**
	- If its roadmap is successful, this project could have a massive effect on reducing the computational costs for Bitcoin users to bootstrap a fully-validating Bitcoin client.
	- Given that the blockchain is [currently almost 500 GB in size](https://ycharts.com/indicators/bitcoin_blockchain_size), there is a very restrictive cost that prevents a large number of users from running a validating client. You need to have the bandwidth available to download it, and in many parts of the world, bandwidth is still prohibitively expensive. You also need a device powerful enough to process that data, and in many parts of the world, people have nothing but a smartphone in terms of digital devices that can connect to the internet.
	- ZeroSync could **bring that cost down to a few gigabytes for the UTXO set and a ZKP proof so small that it could fit on a 1.44 MB floppy disk**. _And it requires no consensus changes or forks whatsoever to do it_.
- Built by altcoiners
	- ZeroSync is built utilizing the Cairo language developed by Starkware, a Turing-complete language that can be used to build zero-knowledge systems for arbitrary computations. Starkware is a company developing ZKPs for the Ethereum ecosystem, specifically developing zero-knowledge rollups as a second layer solution.
	- ZeroSync building out a ZKP-verified syncing client for Bitcoin might wind up being the first time a real material development from an altcoin actually produces a valuable improvement that folds back into the Bitcoin ecosystem.

# More Resources
- [Bitcoin Nodes Now One Step Closer To Instant Sync](https://bitcoinmagazine.com/technical/bitcoin-nodes-now-one-step-closer-to-instant-sync)
- [ZeroSync - Introducing STARKs to Bitcoin (Tabconf Slides)](https://docs.google.com/presentation/d/1KgNTxulMnIa3SCQIh4P061cIW6Jz_IZYMwqzaohA8ds/edit?pli=1#slide=id.g27e0704f09f_0_4)
- [How Bitcoin Usage Could Skyrocket Thanks To Zero-Knowledge Proofs](https://www.forbes.com/sites/digital-assets/2023/08/21/how-bitcoin-usage-could-skyrocket-thanks-to-zero-knowledge-proofs/?sh=62c73b04bde6)
- [Stephan Livera Podcast 484 Robin Linus ZeroSync: Speeding up Bitcoin IBD](https://stephanlivera.com/episode/484/)
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/ZeroSync demos Header Chain Verifier - Instantly verify Bitcoin's block header chain in your browser\|ZeroSync demos Header Chain Verifier - Instantly verify Bitcoin's block header chain in your browser]]

