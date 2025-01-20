---
{"dg-publish":true,"dg-path":"BitDevs/Resources/Notes/Bull Bitcoin Wallet Adds Serverless Payjoin V2 Support.md","permalink":"/bit-devs/resources/notes/bull-bitcoin-wallet-adds-serverless-payjoin-v2-support/","title":"Bull Bitcoin Wallet Adds Serverless Payjoin V2 Support","tags":["bitcoin","bitdevs","socratic-41","self-custody","software","payjoin","privacy","coinjoin"],"noteIcon":"3","created":"2025-01-19T16:13:34.431-10:00","updated":"2025-01-19T22:50:36.193-10:00"}
---



[Bull Bitcoin wallet beta is available today on Android](https://play.google.com/store/apps/details?id=com.bullbitcoin.mobile&hl=en_US&pli=1) with iOS support expected in 2025.

> [!QUOTE] [Bull Bitcoin releases serverless asynchronous Payjoin (BIP77) send and receive capabilities for its mobile wallet](https://www.bullbitcoin.com/blog/bull-bitcoin-wallet-payjoin)
> I am very excited about this new and bleeding-edge feature, because it has been a long-standing ambition of Bull Bitcoin to become the first Bitcoin exchange to process Bitcoin withdrawals via Payjoin (Pay-to-Endpoint) transactions.
> 
> ![BitDevs-41-BullBitcoin-Payjoin-X.png](/img/user/para/artifacts/BitDevs-41-BullBitcoin-Payjoin-X.png)
> 
> However, it was hard to justify Bull Bitcoin investing time into building this feature since there were no commercially available end-user Bitcoin wallets that were able to receive Payjoin payments. 
> 
> Indeed, in order to receive Payjoin payments (BIP78), a Bitcoin wallet needed to be connected to a full node server and be online at the moment the payment is made. This means in practice that only merchants, professional service providers and advanced full node users had the capacity to receive Payjoin payments. This is, we believe, one of the major reasons why Payjoin had failed to gain significant traction among Bitcoin users.
> 
> For this reason, the Payjoin V2 protocol (BIP77) was conceived and developed by Dan Gould, as part of the Payjoin Dev Kit project, to outsource the receiver's requirement to run his own server to an untrusted third-party server called the Payjoin Directory. In order to prevent the server from spying on users, the information is encrypted and relayed to the Payjoin Directory via an Oblivious HTTP server.
> 
> Bull Bitcoin’s Payjoin ambitions had been put on hold since 2020, until there was more adoption of Payjoin receiving capabilities among end-user Bitcoin wallets… 
> 
> But it turns out that in the meanwhile, Bull Bitcoin developed its own mobile Bitcoin wallet. And it also turns out that the open-source Bitcoin development firm Let There Be Lightning, which we had collaborated with in the past, had itself collaborated with Dan to build a software library for Payjoin that was compatible with and relatively straightforward to integrate into our own wallet software. All that was missing was to put the pieces together into a finished product. 
> 
> Thanks to the collaborative open source effort of the Payjoin Dev Kit team, Let There Be Lightning team and the Bull Bitcoin team, the Bull Bitcoin wallet has now become the first commercially available end-user mobile wallet on the Google Play store to implement the BIP 77 Payjoin V2 protocol.
> 
> Moreover, the Bull Bitcoin wallet has also implemented asynchronous Payjoin payments, which means that a Payjoin transaction can be “paused” until the receiver or the sender come back online. This way, the receiver's mobile phone can be “turned off” when the sender makes the payment. As soon as the recipient’s phone is turned back on, the Payjoin session will resume and the recipient will receive the payment. This is a major breakthrough in the mobile Payjoin user experience.
> 
> ##### [Download the wallet here](https://play.google.com/store/apps/details?id=com.bullbitcoin.mobile&amp;hl=en_US)
> 
> We would like to thank the Human Rights Foundation for allocating a generous bounty for the development of a Serverless Payjoin protocol and its implementation in a mobile Bitcoin wallet, as well as OpenSats and Spiral for supporting the work of Payjoin Dev Kit, which made this all possible. 
> 
> ## **Why does this matter?**
> 
> Payjoin, also known as Pay-to-endpoint, is a protocol which allows the Bitcoin wallet of a payments receiver and the Bitcoin wallet a payments sender to communicate with each other for the purpose of collaborating on creating a Bitcoin transaction. 
> 
> I first heard about Payjoin (then called Pay-to-endpoint) in 2018 and it completely blew my mind. What I liked most about it was that it was not a protocol change to Bitcoin, but rather it was an application-layer protocol that allows wallets to communicate in order to create smarter and more efficient Bitcoin transactions.
> 
> Whereas in a normal Bitcoin payment the transaction is created by the sender, and all the inputs of that transaction belong to the sender, in a Payjoin payment both the sender and the receiver contribute coins as inputs.
> 
> ![BitDevs-41-Payjoin-Tx-Example.png](/img/user/para/artifacts/BitDevs-41-Payjoin-Tx-Example.png)
> 
> In the Bitcoin whitepaper, Satoshi wrote:
> > some linking is still unavoidable with multi-input transactions, which necessarily reveal that their inputs were owned by the same owner.
> 
> With Payjoin, this assumption is no longer true. With Payjoin, we have fixed one of Bitcoin’s most fundamental privacy problems... without changing the Bitcoin protocol!
> 
> In a Payjoin transaction, the output amounts visible on the blockchain does not necessarily reflect the value of the payment that was actually exchanged. In other words, you can’t easily tell how much money one wallet sent to the other. This is great for users that are concerned a malicious third party may be attempting to obtain sensitive information about their finances without their consent. This does not however pose an accounting problem for the Bitcoin wallets involved in that transaction: since both wallets are aware of which coins they used as inputs and outputs, they are independently able to calculate the "actual" value of the payment that was sent even if the payment on the blockchain appears to be a of a different amount.
> 
> Payjoin breaks the common input ownership heuristic, an assumption used by hackers and fraudsters to track ownership of addresses on the blockchain. The neat thing about this property of Payjoin is that it benefits everyone on the network, not just the Payjoin users themselves.
> 
> It allows the receiver of a payment to opportunistically consolidate his utxos when he is receiving funds, in a way which does not necessarily appear to be a consolidation transaction on the blockchain. Depending on the configuration of a payment transaction, it can also make a regular payment look like a consolidation.  
> 
> In addition to these benefits, the introduction of collaborative peer-to-peer transaction protocols opens up exciting opportunities for the creation of Lightning Network channels, as well as efficiencies for transaction batching.

# More Resources
- [Bull Bitcoin Wallet Adds Serverless Payjoin V2 Support](https://www.nobsbitcoin.com/bull-bitcoin-wallet-v0-4-0/)
- [[para/1. Projects/Honolulu BitDevs/Events/BitDevs Socratic Seminar 27#Presentation\|Payjoin presentation by Dan Gould at Socratic Seminar 27]] 
- [Serverless Payjoin Gets its Wings by Dan Gould](https://payjoin.substack.com/p/serverless-payjoin-gets-its-wings)
- [Proposal for a serverless version of the BIP78 payjoin protocol | Bitcoin Optech 236](https://bitcoinops.org/en/newsletters/2023/02/01/#serverless-payjoin-proposal)

