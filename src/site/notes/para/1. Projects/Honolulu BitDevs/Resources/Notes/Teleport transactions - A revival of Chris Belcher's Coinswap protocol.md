---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Teleport transactions - A revival of Chris Belcher's Coinswap protocol.md","permalink":"/bit-devs/resources/notes/teleport-transactions-a-revival-of-chris-belcher-s-coinswap-protocol/","title":"Teleport transactions - A revival of Chris Belcher's Coinswap protocol","tags":["socratic-32","bitcoin","self-custody","hardware"],"noteIcon":"3","created":"2024-03-17T12:10:51.059-10:00","updated":"2024-03-17T14:30:02.240-10:00"}
---



> [!QUOTE] [@RajarshiMaitra Thread on X](https://x.com/RajarshiMaitra/status/1768623072280809841?s=20)
> For whoever is watching, if Maxwell-Belcher Coinswap rings any bell to you, we got news.
> 
> **Now there exists a one-line command to run the protocol suit with multiple makers, DNS server, and taker client, all working over Tor-only.**
> 
> [GitHub - utxo-teleport/teleport-transactions: Functioning, minimal-viable binaries and libraries to perform a trustless, p2p Maxwell-Belcher Coinswap Protocol](https://github.com/utxo-teleport/teleport-transactions)
> 
> History 🧵👇
> 
> ---
> 
> Greg Maxwell posted in Bitcoin Talk Forum, an ingenious idea of atomic swaps of utxos to "massively improve Bitcoin's fungibility", in 2013,
> 
> **The idea breaks the fundamental heuristics of chainanal and provides passive privacy to whole Bitcoin network.** 
> 
> [CoinSwap: Transaction graph disjoint trustless trading | Bitcointalk](https://bitcointalk.org/index.php?topic=321228.0)
> 
> ---
> 
> This was one of the first applications of HTLCs with Bitcoin scripts. Even before Lightning. 
> 
> But for whatever reason, this protocol was never developed. 
> 
> Until [@chris\_belcher\_](https://twitter.com/chris_belcher_), a prolific privacy researcher and designer of Join-Market took this task up.
> 
> ---
> 
> He detailed the nuances of the protocol, identified all the edge cases, and made a detailed design document with a lot of future improvements. 
> 
> But most importantly outlining the impact of the existence of this protocol.
> 
> [Design for a CoinSwap Implementation for Massively Improving Bitcoin Privacy and Fungibility](https://gist.github.com/chris-belcher/9144bd57a91c194e332fb5ca371d0964)
> 
> ---
> 
> Belcher started working on this protocol on Dec 2020, and released an alpha version of it on Feb 2022.
> 
> [twitter.com/chris\_belcher\_/status/1498306087300259848?s=20](https://x.com/chris_belcher_/status/1498306087300259848?s=20)
> 
> ---
> 
> Back in 2021, I started working on Bitcoin development full-time, and thanks to [@spiralbtc](https://twitter.com/spiralbtc) one of my early assignments was to help Belcher in Coinswap. 
> 
> The complexity of the protocol was overwhelming. I helped him wherever I could, but over time found myself valuable elsewhere.
> 
> ---
> 
> Then something unfortunate happened. 
> 
> By mid-2022 Belcher notified in his public diary that he had been affected by Long-Covid and since then been unable work. **Halting the development of coinswap.**
> 
> [Chris Belcher's Work Diary](https://gist.github.com/chris-belcher/ca5051285c6f8d38693fd127575be44d)
> 
> ---
> 
> After the absence of Belcher, coinswap was **stale for more than 1 year**. 
> 
> Last year I took one major decision to drop off from the [@spiralbtc](https://twitter.com/spiralbtc) dev grant and focus building on [@bitshala_org](https://twitter.com/bitshala_org) and Coinswap. 
> 
> I took up Coinswap as a personal challenge and my tribute to Belcher.
> 
> ---
> 
> The initial days were intimidating. 
> 
> I essentially had to take it apart and **rewrite the whole protocol**, as Belcher wrote it as a demo, which didn't have adequate architecture to use it as a standalone library and binaries.
> 
> ---
> 
> **After 278 commits over the last 8 months, we finally reached the point of maturity.**
> 
> The whole thing works with the full recovery mechanism, DNS servers, a comprehensive taker client api, and simulation in an automated regtest environment.
> 
> Try it out: [https://github.com/utxo-teleport/teleport-transactions](https://t.co/UXEkiALF6C)
> 
> ---
> 
> This was a massive personal milestone for me. But it wasn't me alone. Shadowy supercoders from [@bitshala_org](https://twitter.com/bitshala_org) joined hands and pulled some massive loads. There's an engaging dev community currently behind this project (link in the repo).
> 
> ---
> 
> I am immensely grateful to be able to contribute to Belcher's vision to provide massive fungibility into the #bitcoin ecosystem. Thanks to all the people who contributed and thanks to [@spiralbtc](https://twitter.com/spiralbtc) for leading me to this project. onwards!!

> [!QUOTE] [GitHub - teleport-transactions/docs/dev-book.md: Developer Resources](https://github.com/utxo-teleport/teleport-transactions/blob/master/docs/dev-book.md)
> # What it is
> 
> The Coinswap protocol enhances privacy on the Bitcoin network, specifically addressing transaction ownership traceability through chain analysis.
> 
> Imagine Alice wants to send bitcoin with maximum privacy. She initiates a unique transaction that appears ordinary on the blockchain, with her coins seemingly moving from address A to B. **However, the coins actually end up in an unrelated address Z. This process confounds any attempt to trace ownership.**
> 
> This protocol also benefits users like Carol, who use regular wallets. Her transactions appear the same as Alice's, adding uncertainty to any analysis. **Even users unaware of this software enjoy improved privacy.**
> 
> In a world where privacy is vital due to data collection by advertisers and institutions, this enhancement is significant. Moreover, it bolsters Bitcoin's fungibility, making it a more effective form of currency.
> 
> # How CoinSwap works
> 
> In a two-party coinswap, Alice and Bob can swap a coin in a non-custodial way, where neither party can steal from each other. At worst, they can waste time and miner fees.
> 
> To start a coinswap, Alice will obtain one of Bob's public keys and use that to create a 2-of-2 multisignature address (known as Alice's coinswap address) made from Alice's and Bob's public keys. Alice will create a transaction (known as Alice's funding transaction) sending some of her coins (known as the coinswap amount) into this 2-of-2 multisig, but before she actually broadcasts this transaction she will ask Bob to use his corresponding private key to sign a transaction (known as Alice contract transaction) which sends the coins back to Alice after a timeout. **Even though Alice's coins would be in a 2-of-2 multisig not controlled by her, she knows that if she broadcasts her contract transaction she will be able to get her coins back even if Bob disappears.**
> 
> Soon after all this has happened, Bob will do a similar thing but mirrored. Bob will obtain one of Alice's public keys and from it Bob's coinswap address. Bob creates a funding transaction paying to it the same coinswap amount, but before he broadcasts it he gets Alice to sign a contract transaction which sends Bob's coins back to him after a timeout.
> 
> At this point both Alice and Bob are able to broadcast their funding transactions paying coins into multisig addresses, and if they want they can get those coins back by broadcasting their contract transactions and waiting for the timeout. The trick with coinswap is that the contract transaction script contains a second clause: **it is also possible for the other party to get the coins by providing a hash preimage (e.g. HX = sha256(X)) without waiting for a timeout**. The effect of this is that if the hash preimage is revealed to both parties then the coins in the multisig addresses have transferred possession off-chain to the other party who originally didn't own those coins.
> 
> **When the preimage is not known, Alice can use her contract transaction to get coins from Alice's multisig address after a timeout, and Bob can use his contract transaction to get coins from the Bob multisig address after a timeout. After the preimage is known, Alice can use Bob's contract transaction and the preimage to get coins from Bob's multisig address, and also Bob can use Alice's contract transaction and the preimage to get the coins from Alice's multisig address.**
> 
> Here is a diagram of Alice and Bob's coins and how they swap possession after a coinswap:
> 
> [![BitDevs-32-CoinSwap-Diagram-1.png](/img/user/para/artifacts/BitDevs-32-CoinSwap-Diagram-1.png)](https://github.com/utxo-teleport/teleport-transactions/blob/master/docs/dev-book.md#how-coinswap-works)
> 
> If Alice attempts to take the coins from Bob's coinswap address using her knowledge of the hash preimage and Bob's contract transaction, then Bob will be able to read the value of the hash preimage from the blockchain, and use it to take the coins from Alice's coinswap address. This happens in the worst case, but in virtually all real-life situations it will never get to that point. The contracts usually always stay unbroadcasted.
> 
> So at this point we've reached a situation where if Alice gets paid then Bob cannot fail to get paid, and vice versa. Now to save time and miner fees, the party which started with knowledge of the hash preimage will reveal it, and both parties will send each other their private keys corresponding to their public keys in the 2-of-2 multisigs. After this private key handover Alice will know both private keys in the relevant multisig address, and so those coins are in her sole possession. The same is true for Bob.
> 
> ```
> Alice's coins ----> Bob's address
> Bob's coins ----> Alice's address
> ```
> 
> **In a successful coinswap, Alice's and Bob's coinswap addresses transform off-chain to be possessed by the other party**
> 
> [Bitcoin's script](https://en.bitcoin.it/wiki/Script) is used to code these timelock and hashlock conditions. Diagrams of the transactions:
> 
> [![BitDevs-32-Coinswap-Diagram-2.png](/img/user/para/artifacts/BitDevs-32-Coinswap-Diagram-2.png)](https://github.com/utxo-teleport/teleport-transactions/blob/master/docs/dev-book.md#how-coinswap-works)
> 
> **The contract transactions are only ever used if a dispute occurs. If all goes well the contract transactions never hit the blockchain and so the hashlock is never revealed, and therefore the coinswap improves privacy by delinking the transaction graph.**
> 
> The party which starts with knowledge of the hash preimage must have a longer timeout, this means there is always enough time for the party without knowledge of the preimage to read the preimage from the blockchain and get their own transaction confirmed.
> 
> This explanation describes the simplest form of coinswap. On its own it isn't enough to build a really great private system. For more building blocks read the [design document of this project](https://gist.github.com/chris-belcher/9144bd57a91c194e332fb5ca371d0964).

> [!QUOTE] [GitHub - teleport-transactions/docs/dev-book.md: Developer Resources](https://github.com/utxo-teleport/teleport-transactions/blob/master/docs/dev-book.md)
> # Weaknesses of CoinSwap
> 
> The simplified explanation of CoinSwap provided above has several weaknesses, which would undermine the privacy enhancements CoinSwap offers.
> 
> For example, if Alice and Bob both send each other equivalent amounts of money, chain analysis might be able to match the amounts across the different transactions and deduce that a CoinSwap has occurred. In order to prevent this, the CoinSwap can be split into several transactions, obfuscating the total amounts sent by each party.
> 
> Additionally, a hypothetical CoinSwap market is ripe for denial of service (DoS) attacks and eclipse attacks. In a DoS attack, an attacker can repeatedly initiate a CoinSwap with an honest participant and halt it midway, forcing the victim to pay on-chain fees without reaping the privacy benefits. An attacker can also offer to execute a CoinSwap many times with many individuals in order to discover which UTXOs they control, stripping their existing privacy. Lastly, an attacker can participate in a large number of CoinSwaps and trick users into thinking they have established privacy when they have simply been executing one or more CoinSwaps with the same observer, who can then deanonymize the victim’s coins.
> 
> ## Fidelity Bonds
> 
> Fidelity bonds have been proposed as a solution to these attacks. In brief, fidelity bonds require the [maker](https://river.com/learn/terms/m/maker/) of a CoinSwap offer to post [time-locked](https://river.com/learn/terms/t/timelock/) bitcoin as collateral, assuring the [taker](https://river.com/learn/terms/t/taker/) that the maker has a strong incentive to execute the CoinSwap smoothly. Fidelity bonds lock up a maker’s funds, and thus, a large-scale DoS attack would require an enormous amount of bitcoin to be locked up for a significant time period. This high cost is thought to be sufficient to deter DoS attacks.

# More Resources
- [GitHub - utxo-teleport/teleport-transactions: Functioning, minimal-viable binaries and libraries to perform a trustless, p2p Maxwell-Belcher Coinswap Protocol](https://github.com/utxo-teleport/teleport-transactions)
- [GitHub - teleport-transactions/docs/dev-book.md: Developer Resources](https://github.com/utxo-teleport/teleport-transactions/blob/master/docs/dev-book.md)
- [GitHub - Design for a CoinSwap Implementation for Massively Improving Bitcoin Privacy and Fungibility](https://gist.github.com/chris-belcher/9144bd57a91c194e332fb5ca371d0964)
- [bitcoin-dev - Detailed protocol design for routed multi-transaction CoinSwap appendium](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2020-October/018221.html)
- [CoinSwap: Transaction graph disjoint trustless trading | bitcointalk](https://bitcointalk.org/index.php?topic=321228.0)