---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Quantum Computing and Bitcoin.md","permalink":"/bit-devs/resources/notes/quantum-computing-and-bitcoin/","title":"Quantum Computing and Bitcoin","tags":["bitcoin","bitdevs","consensus","quantum","risk","socratic-40"],"noteIcon":"3","created":"2024-12-17T19:56:13.148-10:00","updated":"2024-12-18T20:28:37.971-10:00"}
---



Google [announced a new chip for quantum computing called Willow](https://blog.google/technology/research/google-willow-quantum-chip/). Here is the AI-generated summary from the blog post:

> [!QUOTE] [Meet Willow, our state-of-the-art quantum chip](https://blog.google/technology/research/google-willow-quantum-chip/)
> - Google's new quantum chip, Willow, is a major step towards building a useful, large-scale quantum computer.
> - Willow reduces errors exponentially as it scales up, achieving a breakthrough in quantum error correction.
> - Willow performed a benchmark computation in under five minutes that would take a supercomputer 10 septillion years.
> - Willow's performance is a sign that useful, very large quantum computers can be built.
> - Google is working on developing quantum algorithms that can solve real-world problems.

This announcement has re-ignited a lot of the FUD around bitcoin's susceptibility to quantum computing. This is not a new discussion - Satoshi himself mused on quantum risks back in 2010:

![BitDevs-40-Quantum-Satoshi-BitcoinTalk.jpg](/img/user/para/artifacts/BitDevs-40-Quantum-Satoshi-BitcoinTalk.jpg)

But it's worth revisiting in the context of recent events. NYDIG released a great summary of the situation in a recent newsletter:

> [!QUOTE] [Meet Willow, our state-of-the-art quantum chip](https://blog.google/technology/research/google-willow-quantum-chip/)
> # Google’s Quantum Computing Advancements Stoke Existential Fears
> 
> On Monday, Google [unveiled](https://blog.google/technology/research/google-willow-quantum-chip/?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG) its state-of-the-art quantum chip, Willow, sparking some concerns within the Bitcoin and broader digital asset community. Although quantum computing (QC) has long been a peripheral fear for investors, its future distance has kept it from being a pressing issue for analysis. Advancements like Google’s are inevitable, and while their significant impact may still be decades away, we’re providing this as a reference for investors the next time QC-related concerns arise. Expert opinions on the timeline vary widely, but we believe informed investors are best equipped to make sound decisions.
> 
> ## How Bitcoin Uses Cryptographic Technology
> 
> To start, let's cover the basics of how Bitcoin utilizes cryptographic technologies. It relies on two key types: digital signatures and cryptographic hash functions.
> 
> Digital signatures, such as ECDSA (Elliptic Curve Digital Signature Algorithm with the secp256k1 parameter) and Schnorr, are fundamental to generating private/public key pairs and managing how users send and receive bitcoins. Users create a key pair and lock an output (bitcoins) to a public key. These bitcoins are secure because only the corresponding private key can produce a valid signature to unlock or spend them. The public key is derived from the private key using ECDSA or Schnorr algorithms.
> 
> Hashing, particularly through the Secure Hash Algorithm 256-bit (SHA-256) and RIPEMD-160, processes an input string to produce a fixed-length output, known as a digest. Bitcoin relies on hashing for several critical functions, including address security, transaction verification, time stamping, and mining.  
> - Public keys, derived from private keys using digital signature algorithms, are hashed twice—first with SHA-256 and then with RIPEMD-160—to generate a public address.
> - The hash of all transactions in a block called the Merkle root, is included in the block header to enable transaction verification.
> - Each block has a unique hash, created by double-hashing (SHA-256) its header, which contains the previous block’s hash and other details, forming a chain of blocks.
> - In mining, hashing involves combining various pieces of information, processing them through SHA-256, and iteratively adjusting data, such as the nonce, until the resulting digest meets specific criteria.
> 
> Both digital signatures and hash functions could, in theory, be compromised by QCs. QCs could compromise existing digital signatures using Shor’s algorithm, which efficiently solves the Discrete Logarithm Problem, allowing QCs to reverse a private key from a public key. Similarly, QCs could threaten current hash algorithms using Grover’s algorithm, known for its quadratic speedup over classical search methods. This could affect mining. 
> 
> ## Good In Theory, Hard in Practice
> 
> The issue, however, is the practicality of these theoretical vulnerabilities. Digital signatures are widely seen as the more vulnerable of the two technologies, with an [estimated](https://nap.nationalacademies.org/read/25196/chapter/6?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG#98:~:text=ECC%20Discrete%2Dlog%20probleme%2Dg) 8.56M physical qubits required to break ECDSA in 10.5 hours. Google’s Willow chip operates at 105 physical qubits, implying that an 81,523x improvement would be required for a similar attack. SHA-256 is much thornier for QCs, [requiring](https://nap.nationalacademies.org/read/25196/chapter/6?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG#98:~:text=algorithm%20when%20available-,SHA256h,-Bitcoin%20mining) 2.2M physical qubits (21,238x improvement over Willow) to break - in 18,000 years. Mining is not likely to be impacted significantly by QCs given what we know today.
> 
> ## What’s at Stake
> 
> While experts differ on the timing of when (or even if) QCs of sufficient strength will be available to break digital signatures, let’s pretend that QCs of sufficient power have arrived. There are two potential vulnerabilities: bitcoins at rest and bitcoins in transit. Bitcoins for whom their public key has been revealed, either through P2PK transactions, the earliest type of transaction types that is no longer in use, or through address reuse (of any signature type). These include Satoshi’s potentially 1M+ bitcoins, which are sitting in P2PK addresses. In total, this amounts to about [4M bitcoins](https://www.deloitte.com/nl/en/services/risk-advisory/perspectives/quantum-computers-and-the-bitcoin-blockchain.html?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG#:~:text=How%20many%20Bitcoins%20could%20be%20stolen%20now%20if%20sufficiently%20large%20quantum%20computers%20were%20available%3F) (~$400B). A sufficiently strong QC could reverse the private keys for these bitcoins and move them to new addresses the attacker controls. For bitcoins in transit, whose public key has been revealed in a spending transaction, a QC would need to reverse a private key in 10 minutes to intercept these bitcoins and double spend them, again moving them to addresses the attacker controls.
> 
> ## Technologists Haven’t Been Sitting Down
> 
> What is to be done about these risks, however remote they may be? First, QCs pose a risk for all sorts of real-world applications that are far more important than Bitcoin – commerce, banking, government, and military, just to name a few. Second, the experts haven’t been sitting down. The NIST (National Institute of Standards and Technology) started a competition in 2016 for post quantum computing (PQC) digital signatures, and today we have [3 viable candidates](https://www.nist.gov/news-events/news/2024/08/nist-releases-first-3-finalized-post-quantum-encryption-standards?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG). The agency is continuing the search for more candidates too, with [14 more algorithms](https://www.nist.gov/news-events/news/2024/10/nist-announces-14-candidates-advance-second-round-additional-digital?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG) moving on to the next phase of evaluation. For federal systems, the NIST has [set a deadline](https://nvlpubs.nist.gov/nistpubs/ir/2024/NIST.IR.8547.ipd.pdf?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG) of deprecating ECDSA by 2030 and disallowing it entirely after 2035, to give readers a sense of how it views the timing of transitioning to a PQC world. 
> 
> ## Potential Solutions
> 
> Several things could be done for Bitcoin specifically to address QCs. PQC digital signature algorithms could be implemented on Bitcoin. Vulnerable bitcoins at rest could be moved to PQC addresses. Those that cannot be moved because of private key loss or because the individuals are no longer around (Satoshi) could have non-spending conditions put on them via a soft fork. These are some simple solutions, but given the inventiveness of the Bitcoin community, we are certain plenty of other options will come forth. Furthermore, this isn’t just a problem that the Bitcoin community faces, but all digital assets. General solutions may arise from other parts of the broader digital asset ecosystem as well.
> 
> ## Final Thoughts
> 
> QCs may conjure up bewildering visions of the future, but they also spark fears, particularly for technologies like Bitcoin. Fortunately, the risks posed by QCs are often overstated (in the case of hashing) or remain many years away (for digital signatures). Moreover, cryptographers have been preparing for a PQC world for years, and Bitcoin developers are [actively addressing](https://github.com/cryptoquick/bips/blob/p2qrh/bip-p2qrh.mediawiki?utm_campaign=Research%20Emails&utm_source=hs_email&utm_medium=email&_hsenc=p2ANqtz--pir15QGlaLHZCJc_-25vcSqK04ejEM2be4hF57IRaVnwNPUK8r4BSXoFKop-wswpGFieG) this challenge. Technology risks are one of the largest categories to consider when evaluating Bitcoin, and while QCs carry significant theoretical implications due to their novelty, investors can take comfort in the fact that these risks are manageable if the threat ever becomes more immediate.

# Recent Proposals

## Matt Corallo's Scheme For [Quantum Readiness via Taproot](https://groups.google.com/g/bitcoindev/c/8O857bRSVV8/m/4cM-7pf4AgAJ?pli=1)

> [!QUOTE] [Summary of cryptoquick's talk at Bitcoin Amsterdam](https://x.com/cryptoquick/status/1844012810558423057)
> There's been a few rough ideas for QC robustness in the signature scheme over Bitcoin transactions  over the past many years, but many of them have a number of fairly major drawbacks.
> 
> First, some base assumptions:
> (a) QCs that can break EC will take a while (probably closer to a decade or two than a few years). This lines up with NSA and other recommendations. We have time to upgrade, but we might consider having an option today for wallets to get QC security later.  
> (b) Its entirely possible that fundamental scaling constraints will emerge and QCs that break EC simply won't ever be reality. We might not want to bet on this, but its possible.  
> (c) We'll get some reasonable warning before QCs are there - QC development requires immense  resources, so much so that only a few organizations in the world can afford to hire the talent required and fund the lab. This type of development has and will likely continue to lead to announcements as progress continues, and we'll have a few years warning as QCs get closer and closer.  
> (d) post-QC security assumptions (like Lattices and obviously Supersingular Elliptic Curve Isogeny) are insufficient to secure coins today, and are bad candidates for inclusion in Bitcoin's consensus due to the likelihood of future cryptography research. This implies the only candidates for post-QC signature security in Bitcoin's consensus today are hash-based signatures (basically SPHINCS/SPHINCS+). 
> (e) its not worth waiting on OP\_CAT and the other more general script opcode additions for this, as those seem stuck in bikeshed hell, not to mention questions around MEVil and Bitcoin's future abound. Further, doing this via dedicated opcode simplifies wallet adoption, which is likely to struggle already given the additional workload for wallet developers for no immediate user-facing features.
> 
> Given these assumptions, it seems ill-advised for wallets today to start locking funds up in a way where they need to pay the on-chain footprint cost to get post-QC security for their transactions \*today\*, but given upgrade cycles in Bitcoin it also seems ill-advised to not have some option for wallets to have "emergency" paths.
> 
> Luckily, taproot provides a great way to build such a scheme! Because taproot script-path spends are strongly-bound (the taproot script-path hash t includes the internal key in its hash), a future QC could determine the associated private key and script-path merkle root, but it cannot forge an alternative script-path merkle-root.
> 
> This provides a compelling hook for post-QC security - with the simple addition of an OP\_SPHINCS (or equivalent post-QC non-one-time-use (i.e. not Lamport/Winternitz) signature verification opcode, functioning in much the same was OP\_CHECKSIG works today), wallets simply need to construct their taproot outputs to always contain a script-path alternative spending condition. When QCs are becoming a reality, key-path taproot spends could be disabled via soft-fork, forcing spends to be done using the QC-secure path.
> 
> This scheme obviously has the major drawback of non-upgraded funds confiscation at the time of QC existence, but:
> (a) we could instead require explicit opt-in for this scheme. This has the drawback of yet another on-chain fingerprint and would require a new scriptPubKey format (but keeping the existing bech32m address format, hopefully most wallets support that without any code changes today). Of course if we do, substantial quantities of Bitcoin which are unlikely to ever be spent could lead to supply shock, severely damaging Bitcoin's utility in other ways, 
> (b) alternatively, we could allow key-path spends for wallets which prove the script-path is a NUMS point (via some new keypath+proof spend variant). I doubt many wallets today bother committing to a NUMS point for their taproot output pubkeys, so this would break existing wallets, but it would allow for an opt-out scheme.
> 
> This scheme has the incredibly nice property of not bloating existing use-cases nearly at all (just one extra taproot script-path branch, but that's not a huge deal generally).
> 
> There's a few things to bike-shed on here, though - first of all whether to require opt-in or provide an opt-out and secondly whether to also fail any script-paths that hit an ECDSA signature validation (probably yes?).
> 
> I assume this has been written up elsewhere but I couldn't find it. Most of this is due to not\_nothingmuch, I'm just writing it up here and taking credit for it.
> 
> This doesn't address the questions around PoW in a post-QC world, of course, but that likely isn't something that can be answered until we see more practical limitations of QCs (eg what is the minimal latency of a QC gate? If its particularly low, can we simply complexify Bitcoin's PoW hash function in order to delay QC results far past when traditional hardware is able to mine a block?)

## QuBit Softfork From cryptoquick

> [!QUOTE] [Summary of cryptoquick's talk at Bitcoin Amsterdam](https://x.com/cryptoquick/status/1844012810558423057)
> Quantum computers pose two threats to Bitcoin: to signatures and to mining. There's an algorithm called Shor's that can, with a certain level of certainty, find the factors to very large numbers. The Elliptic Curve Discrete Log Problem is what keeps Bitcoin secure, and Shor's could one day, with sufficient computation, find the private key to a public key. 
> 
> The algorithm used to optimize mining is called Grover's, and it can reverse the inputs to a black box function, such as SHA-256d. That requires far more computation than Shor's algorithm requires to factor a public key, and so the major focus to make Bitcoin quantum resistant is to add new post quantum cryptography signature algorithms. 
> 
> Post quantum cryptography has been an emerging field over the last decade, but the primary concerns as they relate to Bitcoin are public key size and signature size. Typically for algorithms such as SPHINCS, XMSS, and FALCON, they are measured in the kilobytes, whereas a secp256k1 X-only public key is only 32 bytes and a Schnorr signature is only 64 bytes. 
> 
> The American government evaluates these algorithms as potential candidates, slowly establishing confidence in their security. Their timeline stretches into 2029 through 2033. So what will our timeline be like? As low time preference bitcoiners, will we aim to be at least as secure as the government intends to be? 
> 
> Coins are vulnerable if the public key of an address is ever exposed. There are five cases where Bitcoin public keys can be exposed. 
> 1. Early P2PK or Pay to Public Key addresses, like the kind Peter Todd used for his block rewards. 
> 2. Reused addresses, meaning, addresses you've spent from, then received funds to again. 
> 3. Taproot addresses are public keys themselves. 
> 4. And any transactions signed and sent to the mempool also briefly reveal your keys. 
> 5. Additionally, keys derived from unhardened BIP-32 derivation paths can also expose child public keys. 
> 
> In the Pay to Quantum Resistant Hash, or P2QRH BIP I've proposed, I describe how we can introduce a new transaction field called the attestation similar to the witness introduced in SegWit v0. In the attestation, only valid signatures are allowed. Junk data cannot be introduced with this rule because there needs to be a private key to sign for every public key included in the attestation. We know they are valid signatures because every public key is committed to via HASH256, and this is what we call SegWit v3, which produces bech32m addresses starting with bc1r. We think this is a good way to quickly visually tell these are quantum resistant addresses. 
> 
> P2QRH will build on top of P2TR, or Pay to Taproot. We're not looking to replace classical cryptography, even if it's broken one day, but to augment it. This approach is called hybrid cryptography. There is one key difference; P2QRH spend scripts are a hash of the public key, and not a public key themselves. They can commit to multiple post quantum public keys, but only to one secp256k1 public key as part of its design. 
> 
> P2QRH addresses are proposed to be introduced as a soft fork called QuBit, with a capital B. This soft fork will necessitate a transitionary period where individuals will need to migrate their coins to the new address type. To facilitate this migration, we propose a 16x attestation discount. Assuming rational economic incentives, Satoshi's original coins, could serve a purpose as a sort of shield. This is because every P2PK coinbase reward has a balance of 50 bitcoin, making it so there is a cryptoeconomic incentive for quantum attackers to target those coins instead of more recent coins below that value. That's what we call Satoshi's Shield.
> 
> One of the things the Surmount Systems team is working on is an early warning system to track how many exposed public keys there are and when they're being spent. This includes assessing the integrity of Satoshi's shield.
> 
> [https://github.com/SurmountSystems/gabriel/](https://t.co/GeBLrma9z5)

Here is a link to the draft BIP for QuBit: [SegWit version 3 spending rules (P2QRH)](https://github.com/cryptoquick/bips/blob/p2qrh/bip-p2qrh.mediawiki) 

[![BitDevs-40-Quantum-HunterBeast-Thumbnail.png](/img/user/para/artifacts/BitDevs-40-Quantum-HunterBeast-Thumbnail.png)](https://youtu.be/T44xpDulUlI?feature=shared)

# More Resources
- [Meet Willow, our state-of-the-art quantum chip](https://blog.google/technology/research/google-willow-quantum-chip/)
- [Quantum Leap](https://viewemail.nydig.com/quantum-leap)
- [Quantum computing as a field is obvious bullshit | Locklin on science](https://scottlocklin.wordpress.com/2019/01/15/quantum-computing-as-a-field-is-obvious-bullshit/)
- [@BTCillustrated on X](https://x.com/BTCillustrated/status/1856658745557999772)
- [@Adrian_R_Morris on X (video on how quantum computers work)](https://x.com/Adrian_R_Morris/status/1868795527007223904)
- [@skdh on X](https://x.com/skdh/status/1866352680899104960)
-  [@anon_hodler on X (video)](https://x.com/anon_hodler/status/1866787980666408978)

