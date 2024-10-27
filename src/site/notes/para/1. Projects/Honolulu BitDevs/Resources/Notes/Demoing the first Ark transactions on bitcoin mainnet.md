---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Demoing the first Ark transactions on bitcoin mainnet.md","permalink":"/bit-devs/resources/notes/demoing-the-first-ark-transactions-on-bitcoin-mainnet/","title":"Demoing the first Ark transactions on bitcoin mainnet","tags":["bitcoin","bitdevs","socratic-38","scaling"],"noteIcon":"3","created":"2024-10-26T19:54:19.015-10:00","updated":"2024-10-26T20:39:18.343-10:00"}
---



# Ark Is Almost Ready
> [!QUOTE] [Ark on bitcoin is here](https://blog.second.tech/ark-on-bitcoin-is-here/)
> Slightly over a year ago, an idea for a new off-chain payment protocol for bitcoin was proposed: Ark. **Originally conceived as a solution for onboarding Lightning users, Ark’s design has evolved significantly since then, and it’s become a full-fledged bitcoin scaling protocol in its own right.**
> 
> Now, we believe Ark is ready for primetime. That’s why we’ve formed [Second](https://second.tech/)—a company dedicated to scaling bitcoin through Ark and other second-layer technologies. 
> 
> To demonstrate the progress we made, **we ran the first-ever Ark transactions with some friends on bitcoin mainnet yesterday**—yes, _real sats_. [Read our dedicated report](https://blog.second.tech/demoing-the-first-ark-transactions-on-bitcoin-mainnet/).
> 
> ## Beyond Lightning
> 
> Since its reveal in 2016, the Lightning Network has made incredible progress, becoming the undisputed standard for making retail payments with bitcoin. 
> 
> **However, with this success, we’ve also started to see the challenges of Lightning’s limitations. While it works incredibly well for tech-savvy users with high payment volumes, retail users often face friction with onboarding and channel management.**
> 
> Lightning Service Providers (LSPs) can alleviate some of this, but if users are relying on centralized entities for their payments, it raises the question: do they need the complexities of Lightning, which was originally designed for a fully peer-to-peer network?
> 
> ## Simpler bitcoin scaling
> 
> This is where Ark comes in. **Ark embraces a centralized approach, adopting a client-server model for fast, low-cost payments while leveraging smart cryptography to ensure that users remain in full control of their bitcoin.** 
> 
> **It achieves this while offering an easier experience for developers and users alike: simpler integrations and simpler wallet management.**
> 
> ## An extension of Lightning, not a replacement
> 
> **Ark was initially designed to improve Lightning onboarding, so it’s naturally compatible with Lightning and should be seen more as an extension than a replacement.** For instance, Ark users can directly pay Lightning invoices (and soon, receive payments too!), allowing them to participate seamlessly in bitcoin’s wider payment ecosystem while enjoying the benefits of Ark when transacting with other Ark users.
> 
> We’re still in the early stages of working out how things will shake out, recognizing that some users may benefit more from Ark, others from Lightning, and many from a combination of both.

# Ark Mainnet Demo
> [!QUOTE] [Demoing the first Ark transactions on bitcoin mainnet](https://blog.second.tech/demoing-the-first-ark-transactions-on-bitcoin-mainnet/)
> Over the past few months, we’ve implemented an ASP (Ark Service Provider) and a command-line wallet called _bark_. It’s a terminal-only experience for now, but that didn’t stop anyone. **Our guests created their first wallets and received some sats to start testing.**
> 
> ## In-round payments
> 
> With everyone set up, it was time to run the first round. In the Ark protocol, the ASP automatically triggers rounds at regular intervals (e.g., every hour), but for this test we had to manually trigger the round.
> 
> **Each round results in a single on-chain transaction.** We had seven guests on the call, each adding their transaction to the round. But, importantly, we only had to pay the on-chain fee for a single small transaction. Efficiency is beautiful.
> 
> To make an in-round payment, our participants used the command:
> ```
> $ bark send-round `vtxo-pubkey` `amount_sat`
> ```
> When they saw `Waiting for round…` appear in their logs, they knew they were ready. Steven then manually triggered the round.
> 
> ![Image](https://blog.second.tech/content/images/2024/09/image-1.png)
> 
> The Ark demo's first round transaction
> 
> Success! Our transaction ([txid 32cea70…baad051](https://mempool.space/tx/32cea70b1e71cace5b4797d1c509ceaa92c6ddb91e0f40b2270aeee03baad051#flow=&vout=0)) was broadcast to the mempool and confirmed in block 862149. The payments were smooth, and everyone verified their balances had been updated.
> 
> > **This is the most amazing feeling I’ve had since the Lightning Network came out.**  
> > **—Super Testnet**
> 
> ## Out-of-round payments (arkoor)
> 
> Our ASP also supports **out-of-round payments**, otherwise known as **arkoor**. Unlike traditional Ark payments, these don’t require waiting for a round. Everyone made an arkoor transaction with:
> 
> ```
> $ bark send `vtxo-pubkey` `amount`
> ```
> 
> Arkoor payments are much simpler and faster than a typical Lightning payment and they completed almost instantly. **With Ark, you only need a single round-trip between client and server. In contrast, Lightning payments get routed through multiple hops, with handshakes at each step to update channel states.**
> 
> > **Insanely fast!**  
> > **—Marty Bent**
> 
> That said, there are trade-offs. **The security model for arkoor payments is different. The recipient needs to trust that the payer and the ASP aren’t colluding to double-spend. If that feels risky, the recipient can cycle their arkoor transaction into an in-round transaction during the next round.**
> 
> ## Lightning payments
> 
> We still had one trick up our sleeve. Even though we were demoing Ark, we knew we had to show off how it works with Lightning. After all, Lightning has become the go-to mechanism for bitcoin payments. **With Ark, you’re not stranded on an isolated island. You can easily send payments to any Lightning wallet, with the ASP acting as the Lightning "gateway".**
> 
> Participants made transfers to their own Lightning wallets. Payments were delivered seamlessly in seconds. The swap from Ark to Lightning is handled atomically, so at no point did any user have to take on any counterparty risk.
> 
> ## Getting a bitcoin balance off Ark
> 
> Ark offers two ways to get your sats back on-chain: **offboarding** and **unilateral exits**.
> 
> ### Offboarding
> 
> The cheapest option is to offboard, which requires collaboration with the ASP and the user needs to waiting for a round. You can initiate an offboard with the simple command:
> 
> ```
> $ bark offboard-all
> ```
> 
> You can see [this round transaction](https://mempool.space/tx/ce9423aef4fcecb22f4f58d83029f3291b50b33b13052f5766c02d3f795f1448#flow=&vin=1) from the demo has an extra output that represents an offboard. I won’t mention who did the offboard to protect their on-chain privacy!
> 
> ### Unilateral exit
> 
> **If the ASP refuses to cooperate or is unavailable for whatever reason, a user can choose to unilateral exit.** Unilateral exits are bit more involved than offboarding and are more expensive due to multiple on-chain fees, but it gets the job done.
> 
> We had two adventurous (and patient!) participants initiate unilateral exits during the demo. Here's an example of [one of the exit transactions](https://mempool.space/tx/f07ebf51e4aed1fef7fc1bb16b72bce56294a512bf0da9fd61db18612b4201c9#flow&vout=0).
> 
> ![Image](https://blog.second.tech/content/images/2024/09/image.png)
> 
> A unilateral exit transaction, "peeling off" branches of the transaction tree
> 
> ## Can I try it myself?
> 
> Right now, the software is experimental, and we've disabled our mainnet ASP. **But if you want to give Ark a spin, you can do it on [_regtest_](https://river.com/learn/terms/r/regtest/).** You can [find the code on Codeberg](https://codeberg.org/ark-bitcoin) and [follow the guide](https://docs.second.tech/getting-started/introduction/) to get started.

# More Context
[![BitDevs-38-Ark-Boltz-X-1.png](/img/user/para/artifacts/BitDevs-38-Ark-Boltz-X-1.png)](https://x.com/ArkLabsHQ/status/1844767778261315763)

[![BitDevs-38-Ark-Boltz-X-2.png](/img/user/para/artifacts/BitDevs-38-Ark-Boltz-X-2.png)](https://x.com/ArkLabsHQ/status/1844767846292967455)


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/bit-devs/resources/notes/ark/#description" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



# Description

Created by [@brqgoo](https://twitter.com/brqgoo). It's a second-layer protocol for making cheap, anonymous off-chain Bitcoin payments - attempting to improve on the UX tradeoffs of Lightning and Liquid without compromising on trustless custody of funds. It has been described as a protocol implementation that follows the the [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Enigma\|Enigma]] framework.

> [!QUOTE] [arkpill.me](https://www.arkpill.me/)
> **Ark is a second-layer solution designed to help scale Bitcoin transactions by using a shared utxo model that enables anonymous, off-chain payments through an untrusted intermediary called the Ark Service Provider (ASP). ASPs are always-on servers that provide liquidity to the network, similar to how Lightning service providers work.**
> 
> Ark is a scaling category of its own and is not a state channel design or a rollup. **The protocol allows recipients to receive payments without an onboarding setup**, such as acquiring inbound liquidity while preserving their receiver privacy.
> 
> Ark has a utxo set that lives off the chain. These utxos are referred to as virtual utxos or vtxos in short. **Virtual utxos are like short-lived notes that expire after four weeks. Users must spend their vtxos upon receiving them within this four-week timeframe or return them to themselves to reset the four-week timer.** 
> 
> Users can acquire vtxos from someone who already owns them or use a process called lifting, which is an atomic two-way peg mechanism that doesn't require trust. Lifting lets users lift their on-chain utxos off the chain for a 1:1 virtual utxo. **Users can unilaterally redeem a virtual utxo for an on-chain utxo without asking for ASP cooperation.**
> 
> **When sending funds, users coin-select and redeem their vtxos and create new ones for the recipient (plus change) in a coinjoin round where ASP is the blinded coordinator.** ASP funds the coinjoin with their own on-chain funds in exchange for vtxo redemptions. Therefore, the coinjoin transaction that hits on-chain has only one or a few inputs provided by the ASP. 
> 
> The newly created vtxos of the coinjoin round are bundled and nested under a shared transaction output. This shared output expires four weeks after its creation, and once it expires, the ASP who funded the shared output in the first place can solely sweep the shared output. All nested vtxos under this shared output are expected to be redeemed in this window period.
> 
> **In summary, Ark is a liquidity network that operates like Lightning, but without introducing liquidity constraints or a direct link between the sender and receiver. It uses virtual utxos, to enable anonymous, scalable, off-chain payments. ASPs provide liquidity to the network and charge fees for their services.**

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


</div></div>

# More Resources
- [Ark Protocol](https://ark-protocol.org/)
- [@2ndbtc on X](https://x.com/2ndbtc/status/1837875577761812577)
- [[para/1. Projects/Honolulu BitDevs/Resources/Notes/Ark\|Previous Note on Ark]]

