---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Ark.md","permalink":"/bit-devs/resources/notes/ark/","title":"Ark","noteIcon":"3","created":"2023-05-25T08:46:04.999-10:00","updated":"2023-06-10T23:03:41.482-10:00"}
---



# Description

Created by [@brqgoo](https://twitter.com/brqgoo). It's a second-layer protocol for making cheap, anonymous off-chain Bitcoin payments - attempting to improve on the UX tradeoffs of Lightning and Liquid without compromising on trustless custody of funds. It has been described as a protocol implementation that follows the the [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Enigma\|Enigma]] framework.

> [!QUOTE] [arkpill.me](https://www.arkpill.me/)
> Ark is a second-layer solution designed to help scale Bitcoin transactions by using a shared utxo model that enables anonymous, off-chain payments through an untrusted intermediary called the Ark Service Provider (ASP). ASPs are always-on servers that provide liquidity to the network, similar to how Lightning service providers work.
> 
> Ark is a scaling category of its own and is not a state channel design or a rollup. The protocol allows recipients to receive payments without an onboarding setup, such as acquiring inbound liquidity while preserving their receiver privacy.
> 
> Ark has a utxo set that lives off the chain. These utxos are referred to as virtual utxos or vtxos in short. Virtual utxos are like short-lived notes that expire after four weeks. Users must spend their vtxos upon receiving them within this four-week timeframe or return them to themselves to reset the four-week timer. 
> 
> Users can acquire vtxos from someone who already owns them or use a process called lifting, which is an atomic two-way peg mechanism that doesn't require trust. Lifting lets users lift their on-chain utxos off the chain for a 1:1 virtual utxo. Users can unilaterally redeem a virtual utxo for an on-chain utxo without asking for ASP cooperation.
> 
> When sending funds, users coin-select and redeem their vtxos and create new ones for the recipient (plus change) in a coinjoin round where ASP is the blinded coordinator. ASP funds the coinjoin with their own on-chain funds in exchange for vtxo redemptions. Therefore, the coinjoin transaction that hits on-chain has only one or a few inputs provided by the ASP. 
> 
> The newly created vtxos of the coinjoin round are bundled and nested under a shared transaction output. This shared output expires four weeks after its creation, and once it expires, the ASP who funded the shared output in the first place can solely sweep the shared output. All nested vtxos under this shared output are expected to be redeemed in this window period.
> 
> In summary, Ark is a liquidity network that operates like Lightning, but without introducing liquidity constraints or a direct link between the sender and receiver. It uses virtual utxos, to enable anonymous, scalable, off-chain payments. ASPs provide liquidity to the network and charge fees for their services.

> [!QUOTE] [Introducing Ark](https://burakkeceli.medium.com/introducing-ark-6f87ae45e272) (narrated on [Bitcoin Audible 734](https://fountain.fm/episode/HwfNHEd6chfAsaAqvtYA))
> - Ark allows recipients to receive payments without acquiring inbound liquidity while preserving their receiver privacy. The protocol is as private as WabiSabi, as convenient as on-chain, and as cheap as Lightning.
> - Ark is a trustless, distinct layer two protocol with unilateral exit.
> - ASPs cannot steal users’ funds or link senders & receivers. Users retain self-custody and can revert their funds to the base layer if something goes wrong on the second layer.
> - Ark has a utxo set that lives off the chain. These utxos are referred to as virtual utxos or vtxos in short.
> - Ark payments settle every 5 seconds and final in every block.
> - Users need to wait for on-chain confirmations to consider a payment ‘final’. However, this doesn’t prevent them from paying invoices with their zero-conf coins.
> - Ark has immediate availability with delayed finality.
> - Ark ensures “absolute atomicity” by using ATLCs instead of HTLCs. Users can receive payments and forward them further without waiting for confirmations. A mempool-level double-spend breaks the atomicity. ASPs cannot redeem senders’ vTXOs if they double-spend recipients’ vTXOs.
> - Ark provides an order of magnitude greater level of privacy compared to Lightning. Every payment on the protocol takes place in a coinjoin round. This obfuscates the trace from the sender to the receiver. The anonymity set is everyone who involves in a payment.
> - Numbers tell us it would take +100 years to onboard the whole population into lightning in a non-custodial way, assuming it takes 4 channels per human and an average channel opening consumes a few hundred vBytes.

Here is how Burak compares Ark's properties to Lightning or on-chain:

![ArkComparisonChart.png](/img/user/para/artifacts/ArkComparisonChart.png)

# Details

At the time of writing (for [[para/1. Projects/Honolulu BitDevs/Events/Socratic Seminar 22\|Socratic Seminar 22]]), there is no technical implementation of Ark - only conceptual. Ark is a complex system, and a detailed overview of how it works can be found at the [arkpill.me deep dive](https://www.arkpill.me/deep-dive) section.

Burak has described Ark as a "trustless, 2-way peg sidechain" and an "off-chain coinjoin protocol" ([source](https://www.youtube.com/watch?v=iQ7TLBhh9r4)).

The general idea is that liquidity management is entirely offloaded to Ark Service Providers (ASPs), which is contrary to Lightning where individual users must manage their own liquidity. Users can also be onboarded to Ark immediately without requiring upfront liquidity because that constraint is deferred to the ASPs. Although ASPs are expected to manage liquidity on the user's behalf, the user maintains self-custody because they can always exit unilaterally on-chain.

Onboarding to Ark is as simple as funding a bitcoin address - Ark "lifts" that UTXO off the chain into a virtual UTXO (vTXO), which can then be transacted on this alternative chain. vTXOs follow a similar transaction flow to on-chain bitcoin - when spending, vTXOs are destroyed and new ones are created.

"Pool transactions are created by Ark service providers perpetually every 5 seconds, which are effectively blinded, footprint-minimal, rapid coinjoin rounds" ([source](https://www.arkpill.me/deep-dive)).  The coinjoin component of Ark will be based off of [WabiSabi](https://eprint.iacr.org/2021/206.pdf).

Transactions on Ark are settled with each 5-second interval by ASPs broadcasting bitcoin transactions containing metadata that represent these vTXO state updates, and transactions are considered final once the corresponding blocks have been confirmed on the bitcoin blockchain.

Every vTXO transaction must have an equivalent amount of bitcoin locked up onchain by an ASP. Although the vTXO can be spent instantly, the corresponding on-chain UTXO is locked up for 4 weeks.

"A vTXO has a lifetime of four weeks. The recipient can solely claim a vTXO in the first two weeks of receiving it. If a vTXO remains unclaimed for the first two weeks, the vTXO reverts to the sender’s control, similar to HTLC timeouts on the Lightning network" ([source](https://www.arkpill.me/deep-dive)). This means that users must periodically refresh any stale vTXOs in order to maintain custody of those funds.

Ark is also interoperable with the Lightning network, assuming ASPs are independently managing Lightning routing nodes with sufficient liquidity. From the user's perspective, Ark vTXOs can simply be used to pay Lightning invoices. 

Although it would benefit from [[para/1. Projects/Honolulu BitDevs/Resources/Notes/OP_CTV\|OP_CTV]]-like covenants, Ark can work on bitcoin today using n-of-n multisig with the tradeoff of requiring interactivity. Without covenants, recipients must be online to sign from the n-of-n multisig to constrain the spending transaction.

[![Ark_TxFootprint_Tweet.png](/img/user/para/artifacts/Ark_TxFootprint_Tweet.png)](https://twitter.com/brqgoo/status/1661467837800787969?s=20)



# More Resources
- [Ark Community Telegram](https://t.me/ark_network_community)
- [SLP482 Burak – Ark: A new L2 protocol for Bitcoin](http://stephanlivera.com/482)
- [Bitcoin Takeover S14 E1: Burak Keceli on Ark & Bitcoin 2nd Layers](https://www.youtube.com/watch?v=iQ7TLBhh9r4)
- [Ark Whiteboard Masterclass with Burak & Robin](https://youtu.be/EocWax43QgQ)
- [Ruben Somsen: Simplest Ark Explanation](https://gist.github.com/RubenSomsen/a394beb1dea9e47e981216768e007454)
- [Bitcoin Optech Newsletter 253](https://bitcoinops.org/en/newsletters/2023/05/31/?ref=nobsbitcoin.com#proposal-for-a-managed-joinpool-protocol)

[![@_arshbot_Tweet_Ark.png](/img/user/para/artifacts/@_arshbot_Tweet_Ark.png)](https://twitter.com/_arshbot/status/1661929814427860997)

